# Azure Pipelines

Azure Pipelines is a service within Azure DevOps that makes it easy to build, test and deploy software automatically. A pipeline consists of different tasks where each task represents a single step in the build pipline that takes an input and produces an output. As an example, we can pass a .NET project as input and run the dotnet build command. Afterwards we can add addtional tasks such as running tests and checking for vulnerabilities. Pipelines are defined as a YAML file that becomes part of the project and can be tracked by source control. 
