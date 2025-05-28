# Model Context Protocol (MCP) 

MCP is a protocol which defines a standard that defines how to integrate external tools to your LLM Chat (Agent).
The tools we integrate can be APIs, databases, files and other resources that can be accessed by a computer.

MCP is made of 3 different parts:
- MCP host: The host is an AI tool that wants to access external data.
- MCP client: The client runs inside an IDE or agent app and connects to the MCP server.
- MCP Server: The server exposes specific capabilities e.g. access to APIs and other datasets. 
