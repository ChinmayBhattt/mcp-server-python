# Weather MCP Server
  
A Model Context Protocol (MCP) server built with `FastMCP` that provides US weather forecasts and active alerts using the [National Weather Service (NWS) API](https://api.weather.gov).

## Features (Tools Provided)

When connected to an AI assistant, it provides the following tools:
- **`get_alerts(state: str)`**: Fetches active weather alerts for a US state (e.g. "CA", "NY").
- **`get_forecast(latitude: float, longitude: float)`**: Fetches detailed weather forecasts for a specific geographic coordinate.

## Project Structure

- `weather.py`: The main FastMCP server containing the API calls and tool definitions.
- `.venv/`: The Python virtual environment for isolated dependencies.
- `pyproject.toml` / `main.py`: Other configuration and entry point scripts.

## Installation & Setup

1. Make sure you are using the virtual environment:
   ```bash
   source .venv/bin/activate
   ```
2. Required packages are likely already installed, but if not:
   ```bash
   pip install "mcp[cli]" httpx
   ```

## Testing Locally

You can test the MCP tools locally through a web interface using the MCP Inspector:

```bash
npx @modelcontextprotocol/inspector "/Users/name/mcp servers/.venv/bin/python" "/Users/name/mcp servers/weather.py"
```

## Connecting to AI Clients (e.g., Claude Desktop)

To use this server with Claude Desktop, add the following to your `claude_desktop_config.json` file:

```json
{
  "mcpServers": {
    "weather": {
      "command": "/Users/name/mcp servers/.venv/bin/python",
      "args": [
        "/Users/name/mcp servers/weather.py"
      ]
    }
  }
}
```

Restart Claude and it will now have access to live formatting and tracking for US weather!
