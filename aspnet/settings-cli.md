# Update web app settings using CLI

With the command we can update or delete a web app setting. Remember that a change to the setting will restart the app. 
The command for updating a setting: 
```azurecli
az webapp config appsettings set -g MyResourceGroup -n MyUniqueApp --settings WEBSITE_NODE_DEFAULT_VERSION=6.9.1
```