Model Context Protocol 

From beginner to Advance in one single thread

Model Context Protocal is the protocol developed by Anthropic to make it easier for AI Applications to easily integrate APIs, Datasources and other resources to LLMs.

There are 3 main builing blocks of MCP
- Tools
- Resources
- Prompts

Tools - LLM Driven
Action that can be performed by MCP servers
- example, searching the web, adding a calendar entry

Resources - Application Driven
Data, static files, etc. 

Prompts - User Driven
Built in prompts that user can use.


## 3 Main Participants
1. MCP Hosts: AI application that coordinates and manages one or multiple servers (Example: VS Code, or application you are building)
2. MCP Client: A component that maintains a connection to an MCP Server and obtains context from an MCP Server for MCP Host to use (Example, MCP Client object that VS Code or your application can instantiate to connect to your MCP Server)
3. MCP Server: A program that provides context to MCP Clients (Such as Filesystem MCP Server or Postgres MCP Server that you have built)


## 2 Layers
1. Data Layer: Defines JSON-RPC based protocol for client server communication including lifecycle management, and core primittives, such as tools, resources, prompts and notifications
2. Transport Layer: Defines the communication mechanisms and channels that enable data exchange between clients and servers, including transport-specific connection establishment, message framing and authorization

Data layer -> inner layer
Transport layer -> outer layer

## 2 Types of transports
1. Stdio Transport
2. Streamable Http Transport

## Data Layer

### Primitives Exposed by MCP Servers

1. Tools
2. Resources
3. Prompts

Each primitive type has associated methods for discovery (`*/list`), retrieval (`*/get`), and in some cases, execution (`tools/call`)

### Primitives Exposed by MCP Clients

1. Sampling (`sampling/complete` method)
2. Elicitation (`elicitation/request` method)
3. Logging

## Notifications
Real-times notifications to enable dynamic updates between servers and clients. Notifications are send as JSON-RPC 2.0 notification messages.