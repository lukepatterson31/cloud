# Azure Kubernetes Service

### AKS Clusters

**Create a cluster**

`az aks create --resource-group <resource-group> --location westus --name <aks-cluster-name> --node-count 1 --generate-ssh-keys --attach-acr <acr-name>`

**Inspect a cluster**

`az aks get-credentials --resource-group <resource-group> --name <cluster-name>`

