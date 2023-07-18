# FAQ

## 🟠 I can't find the password to access my service.&#x20;

The password is the same for all services and can be accessed from the [My Account ](https://onyxia.euw1.prod.sgcip.io/account)page or the [My Services](https://onyxia.euw1.prod.sgcip.io/my-services) page by clicking on the Services Password button.

## 🟠 When I create an R Studio service, what are the login and password to enter?&#x20;

The RStudio ID is: onyxia The password is the same for all services and can be accessed from the [My Account page](https://onyxia.euw1.prod.sgcip.io/account) or the [My Services](https://onyxia.euw1.prod.sgcip.io/my-services) page by clicking on the Services Password button.

## 🟠 Can I change my Git credentials after the service is created?

Yes, it is possible to edit several account information from the [My Account page](https://onyxia.euw1.prod.sgcip.io/account).&#x20;

## 🟠 I feel like Blazing SQL doesn't work...

In the configuration form, there is the resource tab where you need to reserve the memory (Mi), CPU and GPU of a service before it launches.

## 🟠 My service returns a 403 error.&#x20;

A 403 error is related to the network protection that is applied to the services. Services created from a certain IP are initially only accessible from that IP. This protection is managed in the "Security" tab with the "Enable IP protection" checkbox.

## 🟠 How do I get logs on the launch of my service?

This manipulation requires the use of a terminal in an RStudio service, Jupyter ... First you have to find the name of your Kubernetes pod:

```
kubectl get pod
```

For example rstudio-xxxxxx-x or jupyter-python-xxxxxx-x. To then display the logs of this pod:

```
kubectl logs rstudio-xxxxxx-x
```
