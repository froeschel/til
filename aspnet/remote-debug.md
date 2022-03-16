# Remote debug App Service
How to remote debug App Service on Azure:
 - Run build of specific commit in debug configuration.
 - Release the build to a test slot in Azure.
 - Create a local branch based on the same version as the debug build.
 - Create a publish profile for the test slot in Viusal Studio.
 - Pick the 'Attach debugger' option in the hosting section of the publish tab.  
