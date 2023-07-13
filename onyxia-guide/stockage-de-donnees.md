---
description: Store data and use it in services on the Datalab
---

# Data storage

## Principles

The file storage solution associated with Datalab is [MinIO](https://min.io/), a cloud-based object storage system compatible with Amazon's S3 API. Concretely, this has several advantages:

* Stored files are easily accessible from anywhere: a file is accessible directly via a simple URL, which can be shared;
* It is possible to access files stored directly in the data science services (R, Python...) offered on the Datalab, without the need to copy the files locally beforehand, which greatly improves the reproducibility of the analyses.

## Manage your data&#x20;

### Import data&#x20;

The My Files page of the Datalab takes the form of a file explorer showing the different buckets (repositories) to which the user has access.

By default, each user has a personal bucket to store their files. Within this bucket, two options are possible:

* "create a directory": creates a directory in the current bucket/directory, hierarchically, as in a traditional file system;
* "upload\*\* a file\*\*": upload one or more files to the current directory.

{% hint style="info" %}
The graphical interface for data storage on the Datalab is still under construction. As such, it may present problems of reactivity. For frequent operations on file storage, it may be preferable to interact with MinIO through the terminal.
{% endhint %}

### Share data&#x20;

Clicking on a file in your personal bucket takes you to its features page. On it, it is possible to change the distribution status of the file. Changing the status of the file from "private" to "public" provides a broadcast link, which can then be transmitted for download of the file. The "public" status only gives other users read rights, modification or deletion of personal files by other users is impossible.

To simplify the playback of several files – as part of a training for example – it is possible to create a "distribution" folder in your personal bucket. By default, all files in this folder have a public broadcast status.&#x20;

{% hint style="info" %}
In the context of collaborative projects, it may be interesting for the different participants to have access to a common storage space. It is possible for this purpose to create shared buckets on MinIO. Do not hesitate to contact us via the channels specified on the ["First use" ](premiere-utilisation.md)page if you wish to port open-data projects to the Datalab.
{% endhint %}

{% hint style="warning" %}
In accordance with the terms of use, only open data or non-sensitive data may be stored on the Datalab. The fact that a file has a "private" distribution status is not enough to guarantee perfect confidentiality.
{% endhint %}

## Work with data in a service&#x20;

The access credentials needed to access data on MinIO are pre-configured in the various services of the Datalab, accessible in the form of [environment variables.](gestion-des-secrets.md) Thus, importing and exporting files from services is greatly facilitated.

{% hint style="warning" %}
Access to MinIO storage is possible via a personal token, valid for 7 days, and automatically regenerated at regular intervals on the Cloud SSP. When a token has expired, services created before the expiration date (with the previous token) can no longer access storage; The service in question will then appear marked in red on the [My Services](https://onyxia.euw1.prod.sgcip.io/my-services) page. It is therefore essential to regularly renew the services that are running, taking care to back up your code and data beforehand.
{% endhint %}

### With R Studio

The section of the [user documentation ](https://www.book.utilitr.org/)dedicated to the use of RStudio on the Cloud SSP environment presents in detail how to list the files of a bucket, import and export data using the library `aws.s3` from R.

### In Python (with Jupyter or VSCode)

In Python, interaction with an S3-compatible file system is made possible by two libraries:

* [Boto3](https://boto3.amazonaws.com/v1/documentation/api/latest/index.html), a bookstore created and maintained by Amazon;&#x20;
* [S3Fs](https://s3fs.readthedocs.io/en/latest/), a library that allows you to interact with stored files like a classic filesystem.&#x20;

For this reason and because S3Fs is used by default by the[ pandas](https://pandas.pydata.org/) library to manage S3 connections, we will present storage management on MinIO via Python through this library.&#x20;

```python
import os

import s3fs
import pandas
```

```python
# Create filesystem object
S3_ENDPOINT_URL = "https://" + os.environ["AWS_S3_ENDPOINT"]
fs = s3fs.S3FileSystem(client_kwargs={'endpoint_url': S3_ENDPOINT_URL})
```

**List the files in a \_bucket**\_**.**

```python
BUCKET = "donnees-insee"
fs.ls(BUCKET)
```

**Import data into Python.**

The S3Fs package allows you to interact with files stored on MinIO as if they were local files. The syntax is therefore very familiar to Python users. For example, to import/export tabular data via pandas:

```python
BUCKET = "donnees-insee"
FILE_KEY_S3 = "BPE/2019/BPE_ENS.csv"
FILE_PATH_S3 = BUCKET + "/" + FILE_KEY_S3

with fs.open(FILE_PATH_S3, mode="rb") as file_in:
    df_bpe = pd.read_csv(file_in, sep=";")
```

**Export data into MinIO.**

```python
BUCKET_OUT = "<mon_bucket>"
FILE_KEY_OUT_S3 = "mon_dossier/BPE_ENS.csv"
FILE_PATH_OUT_S3 = BUCKET_OUT + "/" + FILE_KEY_OUT_S3

with fs.open(FILE_PATH_OUT_S3, 'w') as file_out:
    df_bpe.to_csv(file_out)
```

{% hint style="warning" %}
S3Fs also offers functions to download/export files from the local filesystem of the Python session. However, copying files locally into the service is usually not a good practice: it limits the reproducibility of analyses, and quickly becomes impossible with large volumes of data. So it's best to get into the habit of importing data as files directly into Python.
{% endhint %}

### The MinIO client

MinIO provides a command-line client that allows you to interact with the storage system in the same way as a typical UNIX filesystem. This client is installed by default and accessible via a terminal in the various services of the Datalab.

The Datalab storage can be accessed through the alias s3. For example, to list the files in his personal bucket:

```bash
mc ls s3/mon-bucket-perso
```

{% hint style="info" %}
The MinIO client offers basic UNIX commands, such as ls, cat, cp, etc. The complete list is available in the [customer documentation.](https://min.io/docs/minio/linux/reference/minio-mc.html?ref=docs-redirect)
{% endhint %}

{% hint style="warning" %}
Handling large files on MinIO is an expensive operation because the stored files are immutable. Thus, renaming or moving a file involves deleting the original file and recreating the file with new metadata. It is therefore important to think upstream about the data structure of projects.
{% endhint %}
