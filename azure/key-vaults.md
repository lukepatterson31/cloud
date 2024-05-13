# Azure Key Vaults

Documentation

https://azure.microsoft.com/en-us/documentation/services/key-vault/


### Creating an Azure Key Vault

Set the subscription context to an existing subscription

`Set-AzContext -SubscriptionName "Subscription Name Here"`

Create a new Key vault resource

`New-AzKeyVault -VaultName 'alias-orgname-keyvault' -ResourceGroupName 'alias-rg' -Location 'Region Here' -EnabledForDeployment`

Set access policies - [Documentation](https://learn.microsoft.com/en-gb/powershell/module/az.keyvault/set-azkeyvaultaccesspolicy?view=azps-11.6.0#syntax) (use `All` to enable all permissions, except Purge, for a category)

`Set-AzKeyVaultAccessPolicy -VaultName 'alias-orgname-keyvault' -ResourceGroupName 'alias-rg' -UserPrincipalName 'name@domain.com' -PermissionsToKeys set,values,here -PermissionsToSecrets set,values,here -PermissionsToCertificates set,values,here`

### Creating a secret

Set the subscription context to an existing subscription

`Set-AzContext -SubscriptionName "Subscription Name Here"`

Create a secure string

`[SecureString]$secretvalue = Read-Host -Prompt "Enter secret" -AsSecureString`

Set the secret in Key Vault

`$secret = Set-AzKeyVaultSecret -VaultName "alias-orgname-keyvault" -Name "SecretName" -SecretValue $secretvalue`

Display the secret metadata

`$secret`

### Listing secrets in a Key Vault

List all secrets in a vault (filter values with `| select Name, Id` etc.)

`Get-AzKeyVaultSecret -VaultName "alias-orgname-keyvault"`

Retrieve a secret's value

`Get-AzKeyVaultSecret -VaultName "alias-orgname-keyvault" -Name "SecretName" -AsPlainText`

### Creating and storing certificates in Key Vault

Login with Azure Account

`Connect-AzAccount`

Set the subscription context to an existing subscription

`Set-AzContext -SubscriptionName "Subscription Name Here"`

Create a certificate policy

`$policy = New-AzKeyVaultCertificatePolicy -SubjectName "CN=aliasTest" -IssuerName Self -ValidityInMonths 12`

Add a certificate

`Add-AzKeyVaultCertificate -VaultName "alias-orgname-keyvault" -Name "CertificateName" -CertificatePolicy $policy`

The previous command is asynchronous, check the status

`Get-AzKeyVaultCertificateOperation -VaultName "alias-orgname-keyvault" -Name "CertificateName"`

### Retrieving a public key for a certificate (thumbprint)

`Get-AzKeyVaultCertificate -VaultName "alias-orgname-keyvault" -Name "CertificateName"`
