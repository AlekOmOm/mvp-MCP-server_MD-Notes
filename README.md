minimal MCP server design 
- retrieving and reading notes.

## Requirements

1. Create a minimal MCP server that implements the Model-Context-Protocol
2. Provide capability to retrieve and read markdown notes
3. Use the provided notes_MCP as knowledge source
4. Keep implementation minimal (MVP)
5. Use plain JavaScript (no TypeScript)

## Tech Stack

- **Runtime**: Node.js
- **Framework**: Express.js (lightweight web framework)
- **Dependencies**:
  - express (HTTP server)
  - cors (Cross-Origin Resource Sharing)
  - fs (Node.js file system for reading notes)
  - path (Path manipulation utilities)

## Architecture

A simple client-server architecture:
```
+-------------------+       +-------------------+       +-----------------+
| LLM Host          | ----> | MCP Server        | ----> | File System     |
| (Claude/other LLM)|       | (Express Server)  |       | (Notes Storage) |
|                   | <---- |                   | <---- |                 |
+-------------------+       +-------------------+       +-----------------+
```

## Directory Structure

```
mcp-notes-server/
├── package.json
├── server.js              # Main entry point
├── routes/
│   └── mcp-router.js      # MCP protocol router
├── tools/
│   └── notes-tool.js      # Notes retrieval implementation
└── notes/                 # Directory containing your markdown notes
    └── ... (your .md files)
```

## Components

### 1. MCP Router

Handles MCP protocol requests:
- Discovery endpoint (`/discover`): Returns available tools and functions
- Invocation endpoint (`/invoke`): Processes tool function calls

### 2. Notes Tool

Implements note retrieval functions:
- `list_notes`: Lists available notes
- `read_note`: Retrieves content of a specific note
- `search_notes`: Simple search functionality for notes

## Implementation Plan

1. Set up basic Express server with CORS support
2. Implement MCP router with discovery and invocation endpoints
3. Create notes tool with basic file operations
4. Connect components and test with an LLM host

