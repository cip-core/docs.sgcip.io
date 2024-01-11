---
description: Presentation of the main principles of the Datalab
---

# Principles of Datalab

## A pooling platform

The Onyxia project is based on the observation of common difficulties encountered by data scientists in the public sector: :

* Agents who are often isolated, due to the relative scarcity of data skills in the administration;
* Inadequate infrastructure, both in terms of resources and technology, which hinders innovation;
* Difficulty in moving from experimentation to production, due to multiple separations (physical separation, development language, working methods) between business departments and IT production

Faced with this situation, the SGCIP Datalab was built to offer a multi-level pooling platform:

* Sharing a modern infrastructure, centered around the deployment of services via containers, and sized for data science uses;
* Sharing of methods, through the pooling of proposed data science services, to which everyone can contribute;
* Knowledge sharing, through training associated with the Datalab as well as the constitution of mutual aid communities focused on its use.

{% hint style="info" %}
Onyxia, Datalab SGCIP Datalab: what are the differences? [Onyxia](https://github.com/InseeFrLab/onyxia) is an open-source project that offers a platform of data science services, accessible via a web application. The [SGCIP Datalab ](https://onyxia.euw1.prod.sgcip.io/home)is an instance of the Onyxia project, hosted at INSEE.
{% endhint %}

## Principle fundamentals

The architecture of the Datalab is based on a set of fundamental principles:

* Data-science-oriented production, by offering an infrastructure sized for most uses and a catalogue of services covering the entire life cycle of data projects;
* Choices that promote the autonomy of users, avoiding any proprietary confinement and allowing access to the lower layers of the infrastructure to cover advanced and specific needs;
* A 100% cloud-native, but also cloud-agnostic project, allowing simple deployment on any infrastructure;
* A completely open-source project, both from the point of view of its constituent bricks and its distribution (MIT license).

## Services offered

The Datalab is accessible through a modern and responsive [user interface](https://onyxia.euw1.prod.sgcip.io/home), focused on the user experience. This constitutes the technical link between the different components of Onyxia:

* Open-source technologies that are the state of the art in container deployment and orchestration, storage, and security;
* A catalogue of services and tools to support data science projects;
* A training and documentation platform to facilitate onboarding on the proposed technologies.

![Fundamental components of the Onyxia Datalab](<../../.gitbook/assets/Screenshot from 2021-11-12 21-25-15.png>)

The catalog of services is designed to accommodate most of the uses of data scientists, from self-service development to the production of processing or applications. The entire life cycle of a data project is thus covered, and the catalog of services is regularly extended to meet the new needs of users.

![A comprehensive service catalog for data science projects](<../../.gitbook/assets/Screenshot from 2021-11-12 21-25-27.png>)

## An open project

The Onyxia Datalab project is resolutely open, on multiple levels:

* The Datalab is accessible via its [Web interface](https://onyxia.euw1.prod.sgcip.io/home) to all public service employees (via AgentConnect or an email address in gouv.fr) as well as to students of statistics schools linked to INSEE (Cefil, Ensai, Ensae);
* The open source code and modularity of the project make it possible to deploy a custom Onyxia instance on any Kubernetes cluster-based infrastructure;
* The project is open to external contributions, whether they concern the catalogue of services, the graphical interface or the arrangement of the software bricks that constitute it.
