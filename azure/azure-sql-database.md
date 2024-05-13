# Azure SQL Database

### Create Azure SQL databases

Login and set context

`az account set -s "Subscription Name"`

Set a password as a secure string

`[SecureString]$password = Read-Host -Prompt "Password for sql admin" -AsSecureString`

Create the SQL server

`az sql server create --name "sql-server-name" --resource-group "resource-group" --location "location" --admin-user "username" --admin-password "$password"`

Configure a firewall rule for Azure services

`az sql server firewall-rule create --resource-group "resource-group" --server "sql-server-name" --name "Allow Azure services" --start-ip-address 0.0.0.0 --end-ip-address 0.0.0.0`

Create a database on the server

`az sql db create --resource-group "resource-group" --server "sql-server-name" --name "DbName" --edition "Basic"`
