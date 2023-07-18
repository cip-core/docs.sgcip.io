---
description: A short demonstration to launch an R project with the SSP Cloud datalab
---

# Start an R project with the datalab

A short demonstration to use R with the [SSP Cloud datalab](https://onyxia.euw1.prod.sgcip.io/home): working with Git code and data hosted on My Datalab Files.

## Setting up the environment&#x20;

* Open the [service catalog](https://onyxia.euw1.prod.sgcip.io/catalog)&#x20;
* Launch and open an RStudio service
* Se connecter avec les iLog in with the following credentials:
  * user: `onyxia`
  *   password: Your password for your services

      You can find it on your account or copy it directly from My Services by clicking on the key.
*   In your RStudio, clone and open this project:

    ```
    git2r::clone("https://github.com/RLesur/sspcloud-demo.git", "sspcloud-demo")
    rstudioapi::openProject("sspcloud-demo")
    ```
* Install dependencies declared in the file `DESCRIPTION`

## Using the storage system&#x20;

### Cheatsheet&#x20;

Find the name of your personal bucket

Each Cloud SSP user has personal storage space on the Cloud SSP storage system. These storage spaces are called buckets.

To find the name of your personal storage space, you can go to the my files page. We then find the name of his personal bucket.

Upload a file&#x20;

```
aws.s3::save_object(object, bucket, region = "")
```

**Import a  file**

```
aws.s3::put_object(file, object, bucket, region = "")
```

### Exemple #1 : Import an R Markdown report

The `s3.Rmd` presents the basic commands to manage its cloud files

*   generate the report

    ```
    # Modifier le bucket ci-dessous (renseignez votre bucket)
    bucket <- "f7sggu"

    rmarkdown::render("s3.Rmd", params = list(bucket = bucket), output_dir = "out")
    ```
*   Import a report

    ```
    source("_upload.R")
    ```

### Exemple #2 : Working with data stored on MinIO&#x20;

Un exemple minimal est présent dans le fichier [datasaurus.R](https://github.com/RLesur/sspcloud-demo/blob/main/datasaurus.R) :

* Datasaurus data are publicly available at this address[https://minio.lab.sspcloud.fr/f7sggu/sspcloud-demo/data/datasaurus.csv](https://minio.lab.sspcloud.fr/f7sggu/sspcloud-demo/data/datasaurus.csv)
* we build a ggplot graph that we save in png and upload to MinIO

To run this pipeline:

```
source("datasaurus.R")
```
