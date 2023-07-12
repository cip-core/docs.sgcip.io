---
description: >-
  Use MLFlow and pokemons to discover MLOps and automate and improve the quality
  of production models.
---

# MLOps and Random Forest Clustering: Demonstration of MLFlow with Pokémon statistics

## The demonstration in a few words

This demo is a Random Forest model for ranking Pokemon. That is, whether they are legendary or not. Next, we'll apply this pattern in a web application and provide a web service API. The objective of this demonstration is to list the characteristics of Pokémon (attack, defense, speed, life points or combat points, etc.) and to train a Random Forest model in order to classify and predict whether a Pokémon is legendary. We also want to define the importance of each characteristic in distinguishing a legendary Pokemon. Finally, we will apply this model in a web application and provide a web service API, so that everyone can test and verify if their Pokemon is legendary.

## The use of the data lab

This project is originally developed in pure Python without any ML Ops support. It is therefore difficult to continue the integration (CI), to continue the deployment (CD) and to continue the training of the model (CT). By migrating this project to the datalab, we were able to take advantage of the data management and ML Ops service provided by the platform. We want to highlight some advantages :

1. Significant improvement in model performance
2. Shortening the model development lifecycle
3. Automate the model deployment process

#### ML Ops with Datalab

When working as a team to develop a model, you have to experience the painful experience of **logging** the model and how the model is trained (e.g. hyper-parameter settings, training dataset location, etc.). We can easily apply continuous development on our model code using tools like **GitHub**. We know that code is a factor that can impact model performance. But most of the time, tuning the hyper-parameters and the training dataset have even more impact than the code on the model. The datalab provides a service called **MLflow** that solves all these problems.

**Model tracking**

For each trained model, one can track the importance of the Pokémons characteristics, hyper-parameter configurations, location of training data, their validation metrics (accuracy, ROC, AUC, etc.). We can also compare different models to improve it and explain what parameter makes this improvement possible.

![Figure 1 - Model tracking](https://minio.lab.sspcloud.fr/pengfei/diffusion/pokemon/pokemon\_metric.PNG)

![Figure 2 - Model comparison](https://minio.lab.sspcloud.fr/pengfei/diffusion/pokemon/pokemon\_mdoel\_camparing.PNG)

**Model deployment**

To deploy a model, we need to set the version and state of the model, and the deploying application can retrieve the appropriate model based on this information..

![Figure 3 - Model deployment](https://minio.lab.sspcloud.fr/pengfei/diffusion/pokemon/model\_version.PNG)

In the example, our model has four versions: one in production, one in development and two in archive.

**Data management service within Datalab**

Every year, the Pokémon Company releases new types of Pokémon. Each version is called a generation. So far we have seven generations. Accordingly, the raw data of Pokémons is divided into different files for each generation. In many cases, the people collecting and downloading the data are not the people using it to train the model. Therefore, it is a new challenge to find the appropriate data to train your model. Fortunately, the datalab provides us with a data management service called Atlas that allows us to find data easily.

We can search data by their name, type, owner, etc. Figure-4 shows an example of full text search.

We can search for data by its name, type, owner, etc..

![Figure 4 -Text search example (Atlas)](https://minio.lab.sspcloud.fr/pengfei/diffusion/pokemon/atlas\_search\_by\_text.PNG)

If the data manager has configured the classification metadata, we can even search data by generation of Pokemons.

![Figure 5 -Example of search by pokemon generation (Atlas)](https://minio.lab.sspcloud.fr/pengfei/diffusion/pokemon/atlas\_search\_by\_class.png)

After finding the data, we can access all the related metadata such as name, location, owner, size, creation date, etc..

![Figure 6 -Example of metadata for the Pokémon dataset (Atlas)](https://minio.lab.sspcloud.fr/pengfei/diffusion/pokemon/atlas\_data\_detail.PNG)

## Useful links (Data and model)

The full cleansed dataset is available here:

{% embed url="https://minio.lab.sspcloud.fr/pengfei/mlflow-demo/pokemon-cleaned.csv" %}

Source codes on how to train, track and deploy the model are available here :

{% embed url="https://github.com/pengfei99/mlflow-pokemon-example.git" %}

To use the most recently deployed model, you can use the following curl command to query our web service :

```
curl -X POST -H "Content-Type:application/json; format=pandas-split" --data \
'{"columns":["hp","attack","defense","special_attack","special_defense","speed"],"index":[272,293,414,263,49],
"data":[[80,70,70,90,100,70],[64,51,23,51,23,28],[70,94,50,94,50,66],[38,30,41,30,41,60],[70,65,60,90,75,90]]}' \
https://pokemon.lab.sspcloud.fr/invocations ;
```
