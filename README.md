# Running Spring Boot + GraalVM native images on Azure Functions

This sample application shows how to:

- Compile a Spring Boot application using GraalVM
- Deploy and run that application on [Azure Functions](https://docs.microsoft.com/en-us/azure/azure-functions/?WT.mc_id=github-social-judubois)

## Prerequisites

- An Azure account with an active subscription. [Create an account for free](https://azure.microsoft.com/en-us/free/?WT.mc_id=github-social-judubois).

## Configure environment variables

You need to configure the following environment variables:

```bash
AZ_LOCATION=westeurope
AZ_RESOURCE_GROUP=azure-native-spring-function
AZ_FUNCTION_NAME_APP=<your-unique-name>
AZ_STORAGE_NAME=<your-unique-name>
```

- `AZ_LOCATION` ➡ The name of the Azure location to use. Use `az account list-locations` to list available locations. Common values are `eastus`, `westus`, `westeurope`.
- `AZ_RESOURCE_GROUP` ➡ The resource group in which you will work. It should be unique in your subscription, so you can probably keep the default `azure-native-spring-function`.
- `AZ_FUNCTION_NAME_APP` ➡ Functions will run into an application, and its name should be unique across Azure.
- `AZ_STORAGE_NAME` ➡ Functions binaries and configuration will be stored inside a storage account. Its name should also be unique across Azure. It must be between 3 and 24 characters in length and may contain numbers and lowercase letters only.

In order not to type those values again, you can store them in a `.env` file at the root of this project:

- This `.env` file will be ignored by Git (so it will remain on your local machine and won't be shared)
- You will be able to set those environment variables by running `source .env`

## Configure Azure Credentials

```bash
az ad sp create-for-rbac --name http://azure-native-spring-function --role contributor --scopes /subscriptions/10494bac-4dc9-4f66-9563-996f688d9c6c/resourceGroups/azure-native-spring-function --sdk-auth
```
