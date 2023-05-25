# Role Assignments

When giving other resources access to the cosmos account, it can be done with role assignments using RBAC. Comos has some different roles that are used for access. However these specific roles can not be seen from the UI. I don't know if this is a bug or if it is intentional. In order to assign the role one neeed to execute following command in Azure CLI:

``
az cosmosdb sql role assignment create --account-name comos-db-no-sql --resource-group comsos-db-rg --scope "/" --principal-id xxxxx --role-definition-id /subscriptions/xxxxx/resourceGroups/comsos-db-rg/providers/Microsoft.DocumentDB/databaseAccounts/comos-db-no-sql/sqlRoleDefinitions/00000000-0000-0000-0000-000000000002
``

