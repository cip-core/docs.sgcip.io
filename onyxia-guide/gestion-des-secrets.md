---
description: Tutorial to use secrets as environment variables in Datalab services.
---

# Secrets Management

### Environment variables

Sometimes some information needs to be made available to a large number of applications, or it doesn't have to be in plain text in your code (access tokens, passwords, etc.). The use of environment variables makes it possible to access this information from any service.

When a service is launched, several environment variables are already injected automatically — for example, [GitHub ](../docs/onyxia-guide/projet-de-demonstration-r-avec-onyxia.md)and [MinIO](http://localhost:5000/o/PJE4wAHZSTsTbfQZzqlZ/s/zGooQhLS0mJUxkbJDe0X/) access tokens.&#x20;

![](../.gitbook/assets/secret.png)

### Creating and managing secrets&#x20;

On the platform, environment variables are secrets written to [Vault](https://www.vaultproject.io/) (the Datalab vault) and are encrypted. This allows you to store tokens, logins and passwords there. The [My Secrets](https://onyxia.euw1.prod.sgcip.io/my-secrets) page takes the form of a file explorer where you can sort and prioritize your variables into folders.

#### First :

* Create a new folder&#x20;
* Then in this folder, create a new secret
* Open your secret

![](../.gitbook/assets/toolbarsecret.png)

Each secret can contain several variables, composed of key-value pairs.

* `+ Add a variable`

![](../.gitbook/assets/secrettable.png)

{% hint style="info" %}
Keys (variable name) always start with $and contain only letters, numbers, and the underscore character (\_). By convention, keys are written in UPPERCASE.
{% endhint %}

* Fill in the key name field and then its value.

### Convert secrets to environment variables&#x20;

Once your secret is edited, with its different variables, you are ready to use it in your service.

* Copy the secret path by clicking the `Use in service button`
* PThen when configuring your service, go to the Vault tab and paste the path of the secret into the dedicated field

![](../.gitbook/assets/servicesconfig.png)

* Create and open your service

To verify that your environment variables have been created, you can run the following commands in the service terminal:

```bash
# Lister toutes les variables d'environnement disponibles
env 

# Afficher la valeur d'une variable d'environnement
echo $MA_VARIABLE 

# Trouver toutes les variables d'environnement qui contiennent un pattern donné
env | grep -i "<PATTERN>"
```
