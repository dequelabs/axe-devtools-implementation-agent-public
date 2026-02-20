# Axe DevTools Implementation Agent

> **⚠️ Disclaimer:** This software is a pre-release and is not officially supported by Deque Systems, Inc. It is provided "as is" without warranty of any kind. Deque shall not be held responsible for any issues, damages, or losses caused by the use of this tool. **Do not run this tool against production branches of your projects.** Always use a dedicated development or feature branch when working with this agent.

**Note:** This is the public facing repository with release binaries only.

The implementation agent is an MCP server that can be installed on a developers workstation and will help with the implementation of Deque's Axe DevTools for Web products using the IDE's AI chat agent.

As of version 0.2.0 the agent supports the implementation of:

- Axe CLI
- Linter Pre-commit Hook
- API and Axe-Watcher
  - Java
    - Selenium
  - Node
    - Cypress
    - Playwright
    - Playwright-test
  - Python
    - Robot (API only)

The MCP server itself is a single self contained executable that does not have any external dependencies like network access or docker.

## Installation Instructions

1. Download the release for you operating system from the Releases section.
2. Once downloaded, place the executable someplace that would be accessible to your IDE.
3. Add MCP configuration to the IDE.

### macOS and Linux Instructions

The downloaded executables will need an extra step on macOS and Linux to make them executable.

**macOS**
```shell
chmod +x axe-imp-agent-macos
xattr -d com.apple.quarantine axe-imp-agent-macos
```

**Linux**
```shell
chmod +x axe-imp-agent-linux
```

## MCP Configurations

### VS Code

Place `mcp.json` in the `.vscode` directory in the root of your project or root of your home directory.

```json
{
    "servers": {
        "axe-imp-agent": {
            "command": "/path/to/axe-imp-agent-executable",
            "args": ["mcp"]
        }
    }
}
```

### Cursor

Place `mcp.json` in the `.cursor` directory in the root of your project or root of your home directory.

```json
{
    "mcpServers": {
        "axe-imp-agent": {
            "command": "/path/to/axe-imp-agent-executable",
            "args": ["mcp"]
        }
    }
}
```

## Start Onboarding the Implementation Agent

1. Confirm you are in the project you wish to implement Axe DevTools in.
2. Make sure your IDE's AI chat is in Agent mode.
3. Run the `#adt-start` tool command to get started.
4. The Implementation Agent will guide the user on next steps.

**Note:** There is a required order the MCP's tools need to be run in. Starting with the `#adt-start` tool command will ensure the implementation goes in the correct order.

## Video Demo

▶️ [Watch the Demo on YouTube](https://www.youtube.com/watch?v=PkagCwknrfA)
