---
description: >-
  In addition to writing documentary content with Gitbook, go even further and
  offer an interactive version of your tutorials with Jupyter notebooks or
  learnr tutorials.
---

# ​🕹️​ Offers interactive training thanks to Onyxia

## Interactive tutorial in the form of a Jupyter Notebook&#x20;

The easiest method is certainly to host your Jupyter notebook on a git platform such as [GitHub](https://github.com/) or [GitLab](https://about.gitlab.com/).&#x20;

You can take as an example the following Jean-Michel Bernabotto's deposit: [https://github.com/jmbernabotto/MachineLearning](https://github.com/jmbernabotto/MachineLearning). In your repository, declare your dependencies in the `requirements.txt`

Then add a script that will be executed when the Jupyter server is launched on the Onyxia platform: you can modify the`onyxia.sh`  script that you will find in this repository.

Next, go to the Onyxia [service catalog](https://onyxia.euw1.prod.sgcip.io/catalog), select the Jupyter service and in the advanced configurations, in the Init tab, paste the URL to the launch script you just wrote. Be careful to use a raw URL to your script. For example, with the above repository, the URL is [https://raw.githubusercontent.com/jmbernabotto/MachineLearning/master/onyxia.sh. ](https://raw.githubusercontent.com/jmbernabotto/MachineLearning/master/onyxia.sh)

![Configure a Jupyter Service - Initialization Script](../../../.gitbook/assets/frame-59.png)

You can then copy the link by clicking on the icon at the top right and keep it to allow direct access to your training. Now make your tutorial visible and accessible within the Cloud SGCIP community:

{% content-ref url="referencer-son-contenu-sur-le-site-sspcloud.fr.md" %}
[referencer-son-contenu-sur-le-site-sspcloud.fr.md](referencer-son-contenu-sur-le-site-sspcloud.fr.md)
{% endcontent-ref %}

## Interactive tutorial with  **`learnr`**

`learnr` is an R package that makes it easy to design interactive tutorials in R Markdown. If you do not know it, do not hesitate to consult the help: [https://rstudio.github.io/learnr](https://rstudio.github.io/learnr/).&#x20;

As before, the easiest way is to host your RStudio project including your tutorial on [GitHub](https://github.com/) or [GitLab](https://about.gitlab.com/). You can take example on the following demo repository: [https://github.com/RLesur/learnr-onixya](https://github.com/RLesur/learnr-onixya). In your repository, declare your dependencies in the `DESCRIPTION` file and add a script that will be executed when the RStudio server is launched on the Onyxia platform: you can modify the `onyxia.sh` script that you will find in this repository.     &#x20;

Then, go to the Onyxia[ service catalog](https://onyxia.euw1.prod.sgcip.io/catalog), select the RStudio service and in the Init tab paste the URL to the launch script. Be careful to use a raw URL to your script. With the previous repository, the URL is [https://raw.githubusercontent.com/RLesur/learnr-onixya/master/onyxia.sh.](https://raw.githubusercontent.com/RLesur/learnr-onixya/master/onyxia.sh)  &#x20;

![Configure an Rstudio Service - Initialization Script](../../../.gitbook/assets/frame-60.png)

You can then copy the link by clicking on the icon at the top right and keep it to allow direct access to your training. Now make your tutorial visible and accessible within the Cloud SGCIP community:

{% content-ref url="referencer-son-contenu-sur-le-site-sspcloud.fr.md" %}
[referencer-son-contenu-sur-le-site-sspcloud.fr.md](referencer-son-contenu-sur-le-site-sspcloud.fr.md)
{% endcontent-ref %}
