# Azure CLI

Set subscription context

`az account set -s "Subscription Name"`

Check VM location subscription restrictions

`az vm list-skus --location centralus --resource-type virtualMachines --zone --all --output table`

### Authentication

**Access token for a resource**

Kusto cluster

`az account get-access-token --scope https://cluster.kusto.windows.net/.default`
