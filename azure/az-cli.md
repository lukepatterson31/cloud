# Azure CLI

Set subscription context

`az account set -s "Subscription Name"`

Check VM location subscription restrictions

`az vm list-skus --location centralus --resource-type virtualMachines --zone --all --output table`

### Authentication

**Access token for a resource**

Kusto cluster

`az account get-access-token --scope https://cluster.kusto.windows.net/.default`

### App Service Plan

**Create a Linux App Service Plan**

`az appservice plan create --name <service-plan-name> --resource-group <resource-group> --location <region> --sku <size> --is-linux`

**Deploy a webapp to a service plan**

`az webapp create --resource-group <resource-group-name> --plan <app-service-plan> --name <webapp-name> --deployment-container-image-name <container-registry-name>.azurecr.io/<image-name>:v<version-number>`

### Web App Config

**Set envrionment variables"

`az webapp config appsettings set --resource-group <resource-group-name> --name <web-app-name> --settings ENVIRONMENT_VARIABLE=VALUE
