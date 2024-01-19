# Health Check

It is a good idea to add health checks to apps and APIs. ASPNET Core has following way of adding a basic default health check for the app. 

``` 
var builder = WebApplication.CreateBuilder(args);

builder.Services.AddHealthChecks();

var app = builder.Build();

app.MapHealthChecks("/healthz");

app.Run(); 
 ```