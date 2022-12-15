# Use HttpClient in Azure Functions

In some cases it can be relevant to use HttpClient from Azure Functions. This happens when one needs to call an external API.\

When doing this be careful not to use global `DefaultRequestHeaders` for the outgoing request. Instead use the `HttpRequestMessage` object to set headers for the current request. \

In newer Function versions it is also possible to use dependency injection and inject a `HttpClientFactory` to the runtime. From there one can created named clients for the requests. 