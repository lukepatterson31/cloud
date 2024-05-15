# Azure Kubernetes Service

### AKS Clusters

**Create a cluster**

`az aks create --resource-group <resource-group> --location westus --name <aks-cluster-name> --node-count 1 --generate-ssh-keys --attach-acr <acr-name>`

**Get credentials for an AKS cluster**

`az aks get-credentials --resource-group <resource-group> --name <cluster-name>`

**Inspect a cluster**

`kubectl get nodes`

**Apply a configuration to a pod**

`kubectl apply -f deploy-service.yaml`

**Get logs from a pod**

`kubectl logs <pod-name> --all-containers`

**Get information on a service**

`kubectl get service <service-name>`
