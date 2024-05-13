# Azure CLI

Set subscription context

`az account set -s "Subscription Name"`

### Authentication

**Access token for a resource**

Kusto cluster

`az account get-access-token --scope https://cluster.kusto.windows.net/.default`
