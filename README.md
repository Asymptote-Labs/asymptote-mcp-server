# Asymptote Security MCP Server

An MCP (Model Context Protocol) server for code security scanning and vulnerability detection. Integrate Asymptote’s security policies directly into your AI-powered development workflow to catch vulnerabilities and enforce security rules in real time, and easily add your own custom security rules and policies.

## Installation

```bash
npm install @asymptote-labs/asymptote-security-mcp
```

[![npm](https://img.shields.io/npm/v/@asymptote-labs/asymptote-security-mcp)](https://www.npmjs.com/package/@asymptote-labs/asymptote-security-mcp)

## Configuration

Set the following environment variables:

- `ASYMPTOTE_API_KEY` (required): Your Asymptote API key for authentication
- `ASYMPTOTE_API_URL` (optional): Override the default API endpoint

### Cursor Setup

1. Open Cursor Settings (`Cmd+,` on macOS or `Ctrl+,` on Windows/Linux)
2. Search for "MCP" or navigate to **Features > MCP Servers**
3. Click **"Add new MCP server"**
4. Enter the following configuration:
   - **Name**: `asymptote-security-mcp`
   - **Type**: `command`
   - **Command**: `npx -y @asymptote-labs/asymptote-security-mcp`
5. Click **"Add Server"**
6. In the MCP server list, find `asymptote-security-mcp` and add your environment variable:
   - Click the server entry to expand it
   - Add environment variable: `ASYMPTOTE_API_KEY` = `your-api-key-here`

Alternatively, you can manually edit your Cursor MCP configuration file:

- **macOS**: `~/.cursor/mcp.json`
- **Windows**: `%APPDATA%\Cursor\mcp.json`
- **Linux**: `~/.config/cursor/mcp.json`

```json
{
  "mcpServers": {
    "asymptote-security-mcp": {
      "command": "npx",
      "args": ["-y", "@asymptote-labs/asymptote-security-mcp"],
      "env": {
        "ASYMPTOTE_API_KEY": "your-api-key-here"
      }
    }
  }
}
```

After adding the server, restart Cursor or reload the window for the MCP server to become available.

## Tools

### `get_policies`

Retrieve active security policies in your instance. Use this to see what security rules are being enforced and their settings.

### `evaluate_diff`

Evaluate code changes against your security policies in your instance. Pass in a unified code diff and receive a decision (`allow`, `warn`, or `block`) along with any policy violations found, including remediation guidance.

## Requirements

- Node.js >= 18.0.0
- Valid Asymptote API key

## License

- Apache License 2.0
