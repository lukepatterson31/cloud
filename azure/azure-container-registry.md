# Azure Container Registry

[Azure CLI acr docs](https://learn.microsoft.com/en-us/cli/azure/acr?view=azure-cli-latest)

### Setup

**Create a new registry**

`az acr create --resource-group <resource-group-name> --name <name> --location <region> --admin-enabled true --sku basic`

**Build and upload an image to a repository**

`az acr build --resource-group <resource-group-name> --image <registry-name>.azurecr.io/<image-name>:v<version-number> --registry <registry-name> --file /path/to/Dockerfile .`

**List images in a repository**

`az acr repository list --name <registry-name> --output table`

**Show version tags**

`az acr repository show-tags --name <registry-name> --repository <registry-name>.azurecr.io/<image-name> --output table`
