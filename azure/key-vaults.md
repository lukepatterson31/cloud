# Azure Key Vaults

### Creating an Azure Key Vault

Set the subscription context to an existing subscription
`Set-AzContext -SubscriptionName "Subscription Name Here"`

Create a new Key vault resource
`New-AzKeyVault -VaultName 'alias-appname-keyvault' -ResourceGroupName 'alias-rg' -Location 'Region Here' -EnabledForDeployment`

Set access policies ([Documentation](https://learn.microsoft.com/en-gb/powershell/module/az.keyvault/set-azkeyvaultaccesspolicy?view=azps-11.6.0#syntax))
`Set-AzKeyVaultAccessPolicy -VaultName 'alias-appname-keyvault' -ResourceGroupName 'alias-rg' -UserPrincipalName 'name@domain.com' -PermissionsToKeys set,values,here -PermissionsToSecrets set,values,here -PermissionsToCertificates set,values,here`
