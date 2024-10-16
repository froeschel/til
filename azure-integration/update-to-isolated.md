### Update Function to Isolated Mode

Follow this [guide]("https://learn.microsoft.com/en-us/azure/azure-functions/migrate-dotnet-to-isolated-model?tabs=net8") when migrating .NET apps from the in-process model to the isolated worker model

When updating existing function apps in the portal it is impartant to rember to update the environment variable ```FUNCTIONS_WORKER_RUNTIME``` to donet-isolated and under the 'Configuration tab' to set the .NET version to .NET 8 Isolated. 