---
description: >-
  This project documents population movements around the March 2020 lockdown
  using anonymous indicators from mobile phones combined with annual population
  estimates.
---

# Data visualization: Population movements around the March 2020 lockdown

![population movements around the March 2020 lockdown in France](../../.gitbook/assets/mouvements\_population\_confinement\_mars\_2020.png)

## The project in few words

This project documents population movements around the March 2020 lockdown using anonymous indicators from mobile telephony provided to INSEE by three mobile operators and which INSEE has combined with annual population estimates. To complete these results, a second exploitation was carried out in partnership with CBS (Dutch Statistics Institute) allowing a detailed visualization of population changes observed before, and during, the first confinement. This offers the possibility to observe, interactively and department by department, the changes observed (incoming and outgoing flows). The data mobilized in this visualization are accessible here.

#### → Link to the [datavisualisation](https://inseefrlab.github.io/lockdown-maps-R/inflows\_FR.html)

## The use of the datalab

The project was carried out with Rstudio for data processing and visualization. The use of Github has encouraged exchanges with the CBS (Dutch Statistical Institute) but also the reuse of the code for the analysis of population movement in other countries. In addition, the second exploitation was greatly facilitated by the development, during the first exploitation, of a reproducible code in the form of a proto-package (set of functions) versioned with Git.

## Data

Download: [Données agrégées publiées en mai 2020](https://www.insee.fr/fr/statistiques/fichier/4635407/IA54\_Donnees.xlsx): [Données de la dataviz (données expérimentales), publiées en avril 2021](https://www.insee.fr/fr/statistiques/fichier/5350073/mouvements\_population\_confinement\_2020\_csv.zip) (Reference for aggregates)

See also:[ Déplacements de population lors du confinement au printemps 2020 - Données expérimentales - Bases de données](https://insee.fr/fr/statistiques/5350073)

### Precautions for data use

INSEE considers these results to be **experimental**. It should be emphasized that these are experimental statistics subject to inaccuracies because of the type of data mobilized and their inherent uncertainties. In addition, these new estimates made at the level of each pair department of residence, department of presence, are published rounded to the hundred in order to allow re-aggregations such as those allowing to deploy the visualization tool. However, it is preferable to interpret the crossings and aggregations obtained by rounding to the thousand people.

## Learn more about the project

{% embed url="https://github.com/InseeFrLab/lockdown-maps-R" %}
Lien vers le repo Github
{% endembed %}
