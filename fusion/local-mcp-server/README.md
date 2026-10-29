# Autodesk Fusion MCP

MCP server for [Autodesk Fusion](https://www.autodesk.com/products/fusion-360/overview): create, modify and
inspect CAD geometry in a running Fusion session from any MCP client.

Registry name: `com.autodesk.aps.api/fusion`

## How it works

This package is a thin **bridge**. The MCP server itself is built into the Fusion desktop application;
the bundle proxies stdio to it over `http://127.0.0.1:<port>/mcp` (default port `27182`) using
[`mcp-remote`](https://www.npmjs.com/package/mcp-remote). Everything stays on your machine.

This server requires Autodesk Fusion. If you don't already have it, [download Fusion (www.autodesk.com)](https://www.autodesk.com/products/fusion-360/overview) to get started.

## Requirements

- Autodesk Fusion, installed and **running**. Without it there is nothing for the client to connect to.
- The MCP server enabled in Fusion (see [Find your port and URL](#find-your-port-and-url)).
- An MCP client: Claude Desktop (MCPB bundle) or Cursor (manual config).

## Find your port and URL

1. In Fusion, open **Preferences > General > API**.
2. Under "Preferences for Scripting and Programming", tick **Fusion MCP Server** (runs locally on this device).
3. Read **Fusion MCP Server Port**. The field label shows the full endpoint, by default `http://127.0.0.1:27182/mcp`.
4. Click **Apply** or **OK**. If you change the port, use the same value in your client.

## Install

### Claude Desktop

Download `fusion_mcpb.mcpb` from the [Fusion MCP release](https://github.com/Autodesk/ai-integrations/releases)
and open it with Claude Desktop. The bundle asks for the port Fusion's MCP server listens on (default `27182`).

### Cursor

Open **Settings > Cursor Settings > Tools & MCPs** and add Fusion to your MCP configuration (`~/.cursor/mcp.json`, or `.cursor/mcp.json` in a project):

```json
{
  "mcpServers": {
    "fusion": {
      "url": "http://127.0.0.1:27182/mcp"
    }
  }
}
```

Make sure the port matches the one shown in Fusion's preferences. See the
[Fusion blog post](https://www.autodesk.com/products/fusion-360/blog/build-your-own-fusion-add-ins-with-the-fusion-mcp/)
for more.

## Documentation

<https://help.autodesk.com/view/ADSKMCP/ENU/?guid=ADSKMCP_FusionDesktopMcp_autodesk_fusion_mcp_server_html>

## Directory layout

| Path | Purpose |
|---|---|
| `server.json` | MCP registry listing (`mcp-publisher publish` reads this) |
| `THIRD-PARTY-NOTICES.md` | Licenses of redistributed dependencies |
| `LICENSE` | MIT |

## License

[LICENSE](./LICENSE) covers files under this directory. It does not cover Autodesk Fusion, the Fusion MCP server built into it, or any content or data that Fusion returns through it. Use of Autodesk Fusion and Autodesk Fusion MCP server is subject to Autodesk's [Terms of Use](https://www.autodesk.com/company/terms-of-use/en/general-terms) and [Privacy Statement](https://www.autodesk.com/company/legal-notices-trademarks/privacy-statement).
