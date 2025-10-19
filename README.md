# MCP Client

A Python client for the Model Context Protocol (MCP) that enables interactive chat sessions with Claude AI, leveraging tools from any MCP server.

## Overview

This client connects to MCP servers (Python or Node.js) and provides an interactive chat interface where Claude can use the server's available tools to answer your queries. It acts as a bridge between Claude's AI capabilities and MCP server functionalities.

## Features

- **Multi-language server support**: Connect to MCP servers written in Python or Node.js
- **Interactive chat loop**: Conversational interface for querying Claude with tool access
- **Automatic tool discovery**: Automatically lists and makes available all tools from the connected server
- **Tool execution**: Seamlessly executes tool calls and returns results to Claude for processing

## Prerequisites

- Python 3.14 or higher
- An Anthropic API key (set in `.env` file)

## Installation

Install dependencies using [uv](https://github.com/astral-sh/uv):

```bash
uv sync
```

## Configuration

Create a `.env` file in the project root with your Anthropic API key:

```
ANTHROPIC_API_KEY=your_api_key_here
```

## Usage

Run the client by providing the path to an MCP server script:

```bash
uv run client.py <path_to_server_script>
```

### Example

```bash
uv run client.py C:\Users\Zachary\Dev\weather\weather.py
```

Once connected, you'll enter an interactive chat session where you can ask Claude questions. Claude will automatically use the tools provided by the MCP server to answer your queries.

Type `quit` to exit the session.

## How It Works

1. **Connection**: The client connects to the specified MCP server using stdio transport
2. **Tool Discovery**: Retrieves all available tools from the server
3. **Chat Loop**: Accepts user queries and sends them to Claude along with available tools
4. **Tool Execution**: When Claude decides to use a tool, the client executes it via the MCP server
5. **Response**: Results are sent back to Claude, which formulates the final response

## Dependencies

- `anthropic` - Claude AI API client
- `mcp` - Model Context Protocol SDK
- `python-dotenv` - Environment variable management
