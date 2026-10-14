# Autodesk Product Help MCP Server

A hosted [Model Context Protocol](https://modelcontextprotocol.io) server that gives AI assistants
read-only access to Autodesk Help and Support documentation.

Ask an assistant *"how do I add a property set in AutoCAD Plant 3D?"* or *"what does AutoCAD error
1603 mean?"* and it can search Autodesk's official documentation and answer from the real articles,
with links, instead of from memory.

| | |
|---|---|
| Endpoint | `https://api.aps.autodesk.com/knowledge/public/v1/mcp` |
| Transport | Streamable HTTP |
| Authentication | None — the public endpoint is open |
| Access | Read-only. Nothing is written, and no Autodesk account is required |

> **This repository contains no server code.** The server is a hosted service operated by Autodesk;
> there is nothing here to install or run. This repo holds the registry metadata
> ([`server.json`](./server.json)) and this documentation.

## Connecting a client

### Claude Code

```bash
claude mcp add --transport http autodesk-product-help \
  https://api.aps.autodesk.com/knowledge/public/v1/mcp
```

### Claude Desktop, Cursor, VS Code, and other clients

Add the server to your client's MCP configuration:

```json
{
  "mcpServers": {
    "autodesk-product-help": {
      "type": "http",
      "url": "https://api.aps.autodesk.com/knowledge/public/v1/mcp"
    }
  }
}
```

The exact key names vary by client — check your client's MCP documentation. Any client supporting
**Streamable HTTP** remote servers will work.

### Verifying the connection

```bash
curl -sS -X POST https://api.aps.autodesk.com/knowledge/public/v1/mcp \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json, text/event-stream' \
  -d '{"jsonrpc":"2.0","id":1,"method":"initialize","params":{
        "protocolVersion":"2025-06-18","capabilities":{},
        "clientInfo":{"name":"curl","version":"1.0"}}}'
```

A successful response reports `serverInfo.name` as `autodesk-knowledge-public-v1-mcp-server`.

## Tools

| Tool | What it does |
|---|---|
| `search_help_content` | Searches Autodesk Help and Support documentation and returns the most relevant articles — title, URL, locale, and body text. Optionally filtered by product, release, and content source. |
| `get_available_products` | Returns the Autodesk product catalog — product names, product codes, and release codes. Assistants call this to discover or validate the values accepted by `search_help_content`. |

Both tools are read-only and idempotent.

### Notes on using `search_help_content`

- `query` and `locale` are required. Write the query in the same language as the locale, keep it
  keyword-rich, and include exact error text or codes where relevant.
- `locale` accepts 40 language/region values (`en_US`, `fr_FR`, `ja_JP`, `zh_CN`, and others).
- `product_code` is preferred over `product_name`. Validate either against
  `get_available_products` rather than guessing — unrecognised values are better omitted.
- `sources` restricts the search to `sfdc_articles` (support knowledge base) or
  `product_documentation` (official product docs). Omit it to search both.
- `max_results` defaults to 5, maximum 50.

## Coverage

Documentation across 240+ Autodesk products, including AutoCAD, Revit, Civil 3D, Inventor, Fusion,
Maya, 3ds Max, Navisworks, and the Autodesk Construction Cloud products. Call
`get_available_products` for the authoritative list.

## Support

Please open an issue on this repository. For questions about the underlying products or
documentation themselves, use the [Autodesk Community forums](https://forums.autodesk.com).

## Licence and terms

See [`LICENSE.md`](./LICENSE.md) for the licence covering the files in this repository.

The repository licence covers **only the contents of this repository** — this documentation and
`server.json`. It does not license the hosted service. Your use of the Autodesk Product Help MCP
endpoint is governed by Autodesk's own terms of service and privacy statement.
