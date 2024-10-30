# Launch your first Java application in Azure Container Apps

## Overview
This is the companion repository for the [Azure Container Apps Java quickstart](https://learn.microsoft.com/azure/container-apps/java-get-started). This repository contains Java samples that demonstrate how to use Azure Container Apps.

## Run in Azure Container Apps

Follow the steps to run the Spring PetClinic sample application in Azure Container Apps.

1. Fork this repository to your GitHub account.
2. Sign in to Azure from the CLI and choose your subscription.
    ```
    az login
    ```
   
3. Install or update the Azure Container Apps extension for the CLI
    ```
    az extension add --name containerapp --upgrade --allow-preview true
    ```
   
4. Register the `Microsoft.App` and `Microsoft.OperationalInsights` namespaces.
    ```
    az provider register --namespace Microsoft.App
    ```
    ```
    az provider register --namespace Microsoft.OperationalInsights
    ```
   
5. Build and deploy your first container app from your forked GitHub repository with the `containerapp up` command.
    ```
     az containerapp up \
         --name <your-container-app-name> \
         --resource-group <your-resource-group-name> \
         --location <your-location> \
         --environment <your-container-app-environment-name> \
         --context-path spring-petclinic \
         --repo <YOUR_GITHUB_REPOSITORY_NAME>
    ```
   This command will:
   - Create the resource group
   - Create the Container Apps environment with a Log Analytics workspace
   - Create an Azure Container Registry
   - Create a GitHub Action workflow to build and deploy the container app

6. Copy the domain name returned by the containerapp up to a web browser. You will see your Petclinic app.