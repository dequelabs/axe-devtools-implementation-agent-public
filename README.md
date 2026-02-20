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

### Using in IDE AI Chat

Before starting, confirm you are in the project you wish to implement Axe DevTools in.

⚠️ It is recommended to run the Implementation Agent on a non-production branch. The `adt-start` command will check the branch before continuing with the implementation.

🤖 Make sure your IDE's AI chat is in Agent mode.

Once configured, use these commands in your IDE's AI chat:

#### **Complete Workflow (Recommended):**
```
#adt-start           → Step 1: Initial setup & Git branch management
#adt-discovery       → Step 2: Scan frameworks & create config files  
#adt-solution        → Step 3: Get personalized recommendations
#adt-watcher         → Step 4a: Implement axe-watcher (results → Developer Hub)
#adt-api             → Step 4b: Implement axe DevTools API (local scan results)
#adt-reporter        → Step 4c: Add HTML/CSV/XML report generation (after API only)
#adt-setup-precommit → Step 5: Complete pre-commit hook integration (web frameworks)
```

#### **Individual Commands:**
- **`#adt-hello`** - Test the MCP server connection
- **`#adt-start`** - **Step 1**: Initial setup & Git branch management
- **`#adt-discovery`** - **Step 2**: Scan current project for testing frameworks, verify package access (npm/Maven/pip), and create config files
- **`#adt-solution`** - **Step 3**: Get personalized accessibility integration recommendations
- **`#adt-watcher`** - **Step 4a**: Implement axe-watcher with framework-specific instructions (Cypress, Playwright, Java Selenium). Results go directly to axe Developer Hub — no local reporter needed
- **`#adt-api`** - **Step 4b**: Implement axe DevTools API with framework-specific instructions (Playwright, Cypress, Java Selenium, Python Robot Framework). Produces local scan results
- **`#adt-reporter`** - **Step 4c**: Add HTML/CSV/XML report generation (only after `#adt-api` implementation — not used with `#adt-watcher`)
- **`#adt-cli`** - Standalone page/workflow accessibility testing without framework changes
- **`#adt-setup-precommit`** - **Step 5**: Complete pre-commit integration workflow for web frameworks
- **`#adt-set-python-venv`** - Set or change the Python virtual environment path, validate it, and test pip access to Deque packages

## Video Demo

▶️ [Watch the Demo on YouTube](https://www.youtube.com/watch?v=PkagCwknrfA)
