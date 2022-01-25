# Error 'Could not find a part of the path \roslyn\csc.exein Visual Studio 2022'
When running our project on a complete new machine with Visual Studio 2022 installed, we got the following error 'Could not find a part of the path \roslyn\csc.exe'. 
The reason for this error was that the nuget package Microsoft.CodeDom.Providers.DotNetCompilerPlatform was not restored correctly. We removed and installed it again, which solved the issue. 
