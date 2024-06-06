# Developer Certificate is Expired

It can happen that the developer certificate expires on the local machine. Without that you can not start your project on a https endpoint. To fix this, start a command promt in admin-mode. Then execute these command. 

```
dotnet dev-certs https --clean
dotnet dev-certs https --trust

```

Each step needs to be confirmed in a popup window. When tat is done Visual Studio needs to be restarted and a vaild devloper certificate will be ready. 
