# Installing the qrlia MCP server (for AI assistants)

qrlia is a hosted remote MCP server. There is nothing to clone, build or run.

1. Add a remote MCP server named `qrlia` with:
   - URL: `https://mcp.qrlia.com/mcp`
   - Transport: Streamable HTTP
   - No API key or environment variables are needed: the server uses OAuth.
2. Example client configuration:

   ```json
   {
     "mcpServers": {
       "qrlia": { "type": "http", "url": "https://mcp.qrlia.com/mcp" }
     }
   }
   ```

   For clients that only support local stdio servers, use a remote bridge:

   ```json
   {
     "mcpServers": {
       "qrlia": { "command": "npx", "args": ["-y", "mcp-remote", "https://mcp.qrlia.com/mcp"] }
     }
   }
   ```
3. On first use the client opens a browser window. The user enters their qrlia workspace name, signs in and allows access. If they have no workspace yet, they can create a free one at https://qrlia.com/apply.
4. Verify by asking for "my QR codes" (tool `qrs_list`) or "my qrlia workspace" (tool `workspace_get`).

Scripts and CI can authenticate with an API key instead (paid plans) by sending `Authorization: Bearer qrc_…` to the same URL.
