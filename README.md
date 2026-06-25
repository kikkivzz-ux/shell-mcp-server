# Shell MCP Server

A minimal MCP (Model Context Protocol) server that gives your AI agent access to a real shell. One file, zero config.

## What it does

Exposes a single tool `run` — your AI sends a shell command, gets the output back. That's it.

## Requirements

- Python 3.10+
- [FastMCP](https://github.com/jlowin/fastmcp)

## Install

bash
pip install fastmcp

## Run

bash
python shell-mcp-server.py

Server starts on `http://0.0.0.0:8005/sse`

## Connect to your AI

Add this to your MCP client config (e.g. Kelivo, Claude Desktop, etc.):

json
{"mcpServers": {"shell": {"url": "http://your-server-ip:8005/sse"}}
}


Replace `your-server-ip` with your actual server IP or `localhost` if running locally.

## Usage

Once connected, your AI can call:

run("ls -la")
run("cat /etc/hostname")
run("python3 -c 'print(1+1)'")


Timeout is 30 seconds per command.

## ⚠️ Security Note

This server executes arbitrary shell commands. Only expose it on trusted networks. Do NOT open port 8005 to the public internet without proper authentication.

## License

MIT — do whatever you want with it.
