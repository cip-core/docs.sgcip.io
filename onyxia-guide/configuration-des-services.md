---
description: Documentation of the different parameters of a service.
---

# Configuring Services

After clicking "New Service" > "RStudio/Jupyter-python/VScode-python" > "Launch"

## Custom name&#x20;

To recognize the service and/or configuration if you register it by clicking on the bookmark symbol at the top right. If the name already exists among the saved configurations, saving will overwrite the old configuration. Convenient to distinguish different services of the same type (RStudio, Jupyter ...).

## Share the service

It is possible to share a service to a group of people by checking the "Share service" box when opening the service. Other members of the group will see the service and will be able to use it. The creation of groups is done by writing to the administrators on Tchap (privately) or by email to the address innovation@insee.fr, communicating the group name, the usernames of the members, the need or not for an associated storage space on MinIO.

{% hint style="info" %}
For a one-time need, it is also possible to share a service that has been created with another person. All you have to do is give him the URL (type https://user-aaaaaaaaaaaaaa-xxxxxxx-x.user.lab.sspcloud.fr/), as well as the password of the service. The username remains Onyxia. Attention, it is recommended to change the password of the service when it is launched (Security tab) so as not to leak it. You will also need to uncheck Enable IP protection and Enable network policy in the Security tab. Only one person at a time can connect to an RStudio service.
{% endhint %}

## S3

This concerns the S3 storage space. To learn how to use this tab, see the [dedicated page.](http://localhost:5000/o/PJE4wAHZSTsTbfQZzqlZ/s/zGooQhLS0mJUxkbJDe0X/)

## Kubernetes

## Init

### PersonalInit

A link to a shell script (linux command chain) that is executed right after the service is launched. Convenient to automate the implementation of certain configurations.

This link to the script must be accessible on the internet, for example on https://git.lab.sspcloud.fr/ with a public project or on [S3 storage](https://app.gitbook.com/o/PJE4wAHZSTsTbfQZzqlZ/s/zGooQhLS0mJUxkbJDe0X/\~/changes/8/onyxia-guide/controle-de-version/stockage-de-donnees) with a public file.&#x20;

Sample initialization script that clones a project from a private Gitlab instance, configures RStudio global options, automatically opens the cloned RStudio project, installs and selects French spell checking, customizes code snippets.

{% hint style="warning" %}
The script is run as root, and the files it creates are owned by the root. This generates errors when these files are called, for example RStudio configuration files. To give back to the normal user (which is called onyxia) the rights on his personal file:

```bash
chown -R ${USERNAME}:${GROUPNAME} ${HOME}
```
{% endhint %}

### PersonalInitArgs

Options to pass to the initialization script, separated by spaces and then called with `$1`, `$2`...

For example if you enter in the PersonalInitArgs field `fichier1.txt fichier2.txt`, and that we use this initialization script:

```bash
#!/bin/bash
touch $1
touch $2
```

The script will create via the touch command two files`fichier1.txt` et `fichier2.txt`.

## Onyxia

## Resources

## Networking

## Security

### Password

This is the password to enter when opening a service, the one given by "Copy the password" on the services page. It is provided by the general setting "Password for your services" found in "My Account" > "Account Information", unless an individual has been defined at the service level.

### Enable IP protection

If checked, the service is only accessible by one IP, to be unchecked if you want to work from two different places.

### Enable network policy

## Git

To learn how to use this tab, see the dedicated [page](controle-de-version/).&#x20;

{% hint style="warning" %}
It is not possible to automatically clone a private project from a private instance (that is, other than gitlab.com and github.com). To do this, it will be necessary to use a shell script as shown [here](configuration-des-services.md).&#x20;
{% endhint %}

### Enabled

If checked, configure Git and attempt a clone when the service starts.

### Name

The name that will appear in commits (not the username of the Gitlab or Github account).

### Email

The email address that will appear in the commits (not necessarily the email associated with the Gitlab or Github account).

### Cache

### Token

Access token defined on the platform used (Gitlab, Github...).

### Repository

The URL obtained on the platform used (Gitlab, Github...) by clicking on "Clone" > HTTPS.

Type :

```
https://github.com/InseeFrLab/docs.sspcloud.fr.git
```

### Service

### Discovery

### Persistence

### Vault

To learn how to use this tab, see the dedicated [page](broken-reference).&#x20;
