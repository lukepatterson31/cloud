# Azure Networking

### Set up a virtual network with Powershell

Select a resource group, if it doesn't exist create it
```
Get-AzResourceGroup -Name <alias>-rg -ErrorVariable notPresent -ErrorAction SilentlyContinue
if ($notPresent)
{
    New-AzResourceGroup -Name <alias>-rg -Location "East US"
}
```

Create subnets
```
$appsSubnet = New-AzVirtualNetworkSubnetConfig -Name apps -AddressPrefix "10.0.0.0/24"
$dataSubnet  = New-AzVirtualNetworkSubnetConfig -Name data  -AddressPrefix "10.0.1.0/24"
```

Create virtual network
```
$virtualNetwork = New-AzVirtualNetwork -ResourceGroupName <alias>-rg -Location EastUs -Name contosoads-vnet -AddressPrefix 10.0.0.0/16 -Subnet $appsSubnet,$dataSubnet
```

View the virtual network (very limited response)
```
$virtualNetwork
```

Check the address space and subnets
```
$virtualNetwork.AddressSpace
$virtualNetwork.Subnets
```

### Set up a virtual network with Azure CLI

Set subscription context in az
```
az account set -s "<SubscriptionName>"
```

Create a virtual network
```
az network vnet create -g "<alias>-rg" -n "contosoads-vnet" --address-prefix 10.0.0.0/16 --subnet-name Apps --subnet-prefixes 10.0.0.0/24
```

Add a subnet to an existing network

```
az network vnet subnet create -g "<alias>-rg" --vnet-name "contosoads-vnet" -n Data --address-prefixes 10.0.1.0/24
```

View a virtual network (use `--query` to filter response)
```
az network vnet show -g "<alias>-rg" -n "contosoads-vnet"
```

List subnets (use `-o` to set output format, e.g. json, table, tsv)
```
az network vnet subnet list -g "<alias>-rg" --vnet-name "contosoads-vnet" -o table
```

### Security Groups

[Tutorial](https://learn.microsoft.com/en-us/azure/virtual-network/tutorial-filter-network-traffic)

**Application Security Group (ASG)**

Define security controls at the application level, useful for grouping VMs together by purpose (web server, SQL server, etc.)

**Network Security Group (NSG)**

Filter network traffic to and from Azure resources. Can be associated with subnets or individual VMs (more granular)

ASGs and NSGs are *not* mutually exclusive


