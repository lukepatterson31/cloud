# Azure Container Apps

### Setup

**Register providers: Microsoft App and Operational Insights""

```
az provider register --namespace Microsoft.App
az provider register --namespace Microsoft.OperationalInsights
```

**Create a Container App environment**

`az container app create --name <environment-name> --resource-group <resource-group> --location <region>`

**Check environment status**

`az containerapp env show --name <environment-name> --resource-group <resource-group>`

**Delete an environment**

`az containerapp env delete --resource-group <resource-group> --name <environment-name>`

### Creating and deleting container apps

**Create a container app**

`az containerapp create --name <container-name> --resource-group <resource-group-name> --environment <environment-name> --image <registry-name>.azurecr.io/<image-name>:v<version-number> --target-port 5000 --ingress 'external' --query properties.configuration.ingress.fqdn --registry-server <registry-name>.azurecr.io --registry-username <acr-username> --registry-password <acr-password>`

**Delete a container app**

`az containerapp delete --resource-group <resource-group> --name <container-app-name>`
