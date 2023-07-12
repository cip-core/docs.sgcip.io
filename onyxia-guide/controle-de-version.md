---
description: Datalab integration with Git software and GitHub development platform
---

# Version control

## Why use version control?

The Datalab is a shared platform: the resources used by the services are shared between the different users. As such, Datalab services operate on the model of ephemeral containers: in standard use, the user launches a service, performs data processing, saves the code that made it possible to perform these processes, and deletes the instance of the service. This saving of code is greatly facilitated by the use of version control.

However, this performance consideration should not be seen as a constraint: version control is an essential development best practice. The benefits are numerous, both individually:

* The local project is synchronized with a remote server, making code loss almost impossible;
* The complete history of choices and changes made on the project is preserved;
* The user can go through this history to look for changes that may have created errors, and decide at any time to revert to a previous version of the project, or to certain files.

In the context of collaborative projects :

* Simultaneous work on the same project is possible, without risk of loss;
* The user can share his changes while benefiting from those of others;
* It becomes possible to contribute to open-source projects, for which the use of Git is largely standard.

{% hint style="warning" %}
This tutorial aims to present how version control can be easily implemented using the tools present on the Datalab. It does not present how Git works and therefore presupposes some familiarity with the tool. There are many online resources that can serve as introductions; for example, the R user will be able to [consult this guide](https://linogaliana.gitlab.io/collaboratif/git.html) and the Python user this course chapter. A complete Git training will soon be offered in the Datalab training area.
{% endhint %}

## GitHub integration with Datalab&#x20;

### Why GitHub ?

Although offline use of Git is possible, the whole point of version control lies in synchronizing the local copy of a project (clone) with a remote repository. Different software forging services allow this synchronization of Git projects, the best known of which are [GitHub ](https://github.com/)and [GitLab](https://about.gitlab.com/). Since the former now has much more visibility — for example, the INSEE repositories, InseeFr and [InseeFrLab](https://github.com/InseeFrLab), are on GitHub — the Datalab offers easy integration with GitHub, which we present through this tutorial.

{% hint style="warning" %}
The rest of the tutorial requires a[ GitHub account](https://github.com/).
{% endhint %}

{% hint style="info" %}
If the use of the Datalab with the GitHub platform is facilitated, it is by no means mandatory: it is still quite possible to use the software forge of your choice for the synchronization of projects. A forge based on GitLab is made available to Datalab users.
{% endhint %}

### Create an access token&#x20;

Syncing with a remote repository requires authentication to GitHub. This is done using a personal access token, which must be generated from the user's GitHub account. The build service is available at [this address](https://github.com/settings/tokens). The GitHub [documentation](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens) provides illustrations to guide the process.

To generate a token, it is necessary to choose a token name, expiration timeout and access rights (scope). It is recommended to choose a short time frame (30 days) and restricted access (repo only) to limit the security risks in case of malicious spread of the token.

![Recommended requirements for generating a GitHub access token](<../.gitbook/assets/token (1).PNG>)

Once the token is generated, it appears on the screen. A token can only be viewed once; In case of loss, it will be necessary to generate a new one.

### &#x20;Add the Datalab access token

It is recommended that you add your access tokens to a password manager. The token can also be added to the "External Services" configuration of the user account on the Datalab, which allows the token to be directly accessible within the services offered on the platform.

![Add a GitHub access token to a user account on the Datalab](<../.gitbook/assets/git (1).PNG>)

{% hint style="warning" %}
Be careful to use in the "Account Information" the email address associated with your GitHub account, it is it that allows you to effectively link the commits you will make to your GitHub account.
{% endhint %}

## Using Git with Datalab services&#x20;

Git is preconfigured to work natively with the various relevant services of the Datalab. When opening a service, it is possible to configure certain elements. If you have added a GitHub access token to your account on the Datalab, it is pre-configured. It is also possible to specify the full URL of a Git repository (e.g. [https://github.com/InseeFrLab/onyxia](https://github.com/InseeFrLab/onyxia)), which will then be cloned at initialization in the workspace of the instance.

![Configuring Git when opening a service](../.gitbook/assets/rstudio.PNG)

### Via the terminal

The GitHub access token is available in the terminal of the various services via the environment variable`$GIT_PERSONAL_ACCESS_TOKEN`. In order to avoid having to authenticate each operation involving the remote repository (clone, push & pull), it is recommended to clone it by including the access token in the HTTPS link, using the following command:

`git clone https://${GIT_PERSONAL_ACCESS_TOKEN}@github.com/<owner>/<repo>.git`

where \<owner> and \<repo>are to be replaced by the username and the name of the GitHub repository respectively.

### Via integrated graphical interfaces

The main code production services available on the Datalab have a graphical interface to facilitate the use of Git:

* RStudio: RStudio offers a graphical interface for native and fairly complete Git. The user [documentation](https://www.book.utilitr.org/03\_fiches\_thematiques/fiche\_git\_utilisation) presents its operation in detail; &#x20;
* Jupyter: the [jupyterlab-git](https://github.com/jupyterlab/jupyterlab-git) plugin allows a (rather basic) interfacing of Jupyter with Git;&#x20;
* VSCode: VSCode natively offers a very well integrated graphical interface with Git and GitHub. Detailed [documentation](https://code.visualstudio.com/docs/sourcecontrol/overview) presents the possibilities of the tool.

{% hint style="warning" %}
The graphical interfaces facilitate the handling of Git, but never completely replace the use of the tool via a terminal because of a necessarily imperfect integration. It is therefore useful to familiarize yourself with the use of Git via the terminal as soon as possible.
{% endhint %}
