---
description: Guided tour of the Datalab
---

# First time use

Welcome to the Datalab Onyxia, a shared self-service data processing platform for statisticians and data scientists of the State. This tutorial offers a guided tour of the Datalab to be quickly operational in the use of its services.

{% hint style="warning" %}
&#x20;We remind you that the Datalab is intended exclusively for the processing of public and non-sensitive data. Experimental projects using non-open data can be carried out in consultation with the Datalab team, provided that they comply with the project's specific safety rules
{% endhint %}

## The service catalog

The [service catalog](https://onyxia.euw1.prod.sgcip.io/catalog/cip) is at the center of the use of the Datalab. It offers a set of services for statistical data processing as well as the complete management of data science projects.

![](../.gitbook/assets/catalogue.png)

### Start a service

To launch a service, simply click on the Launch button of the desired service.

![](../.gitbook/assets/lancer-un-service.png)

A page focused on the requested service opens, which offers several possibilities:

* Click the Launch button again to launch the service with its default configuration;
* Customize the name of the instance after the service is launched;
* Expand a configuration menu to customize the configuration of the service before launching it;
* Save a custom configuration by clicking the bookmark at the top right of the service.

{% hint style="info" %}
The precise configuration of Datalab services is an advanced use and is therefore not covered in this tutorial, but in other pages of this documentary site.
{% endhint %}

### Use a service

The action of launching a service automatically leads to the [My Services](https://onyxia.euw1.prod.sgcip.io/my-services) page, where all active instances on the user's account are listed.

![](../.gitbook/assets/utiliser-un-service.png)

Once the service is launched, an Open button appears that allows access to the service. A password — and, depending on the service, a username — is generally required in order to use the service. This information is available in the README associated with the service, which can be accessed by clicking on the button of the same name.

### Delete an instance

Removing an instance from a service is done simply by clicking the trash can icon below the instance.

{% hint style="danger" %}
For some services, deleting an instance deletes all associated data, and this action is irretrievable. It is therefore necessary to always read the README associated with the instance, which specifies the consequences of deleting the instance. In general, it is very important to ensure that the data and code used are backed up before deleting the instance. The ideal is to[ version your code with Git](controle-de-version/) and perform regular data backups using the[ S3 storage system.](controle-de-version/stockage-de-donnees.md)
{% endhint %}

{% hint style="danger" %}
The resources made available for the execution of the services are shared between the different users of the Datalab. Please do not leave services that you no longer use. We sometimes systematically delete instances that have been inactive for some time in order to free up resources.
{% endhint %}

## Go further

We wanted to present through this tutorial the standard use of the services offered on the Datalab. More advanced uses are presented in other pages of this documentary site:

* [version your code with Git](controle-de-version/)&#x20;
* [store your data with MinIO ](controle-de-version/stockage-de-donnees.md)
* [manage your secrets with Vault ](gestion-des-secrets.md)
* Work on collaborative projects
* self-training with the Datalab&#x20;

## Support

Support and help in the use of the Datalab are carried out at a dedicated exhibition of the interdepartmental instant messaging service Tchap. Any questions about the use of the Datalab or suggestions for improvement are welcome.

