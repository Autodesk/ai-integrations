<h1 align="center">Autodesk Product Help MCP</h1>

<p align="center">
  <b>Give any MCP-compatible AI client read-only access to Autodesk's official Help and Support documentation.</b>
</p>

<p align="center">
  <a href="https://modelcontextprotocol.io"><img src="https://img.shields.io/badge/Model_Context_Protocol-compatible-000000?logo=modelcontextprotocol&logoColor=white" alt="MCP compatible"></a>
  <img src="https://img.shields.io/badge/Transport-Streamable_HTTP-0696D7" alt="Streamable HTTP">
  <img src="https://img.shields.io/badge/Authentication-None-2EBC4F" alt="No authentication">
  <img src="https://img.shields.io/badge/Access-Read--only-2EBC4F" alt="Read-only">
</p>

<p align="center">
  <a href="#getting-started"><b>Getting started</b></a> ·
  <a href="#tools"><b>Tools</b></a> ·
  <a href="#example-prompts"><b>Examples</b></a> ·
  <a href="#troubleshooting"><b>Troubleshooting</b></a> ·
  <a href="https://help.autodesk.com/view/ADSKMCP/ENU/?guid=ADSKMCP_KnowledgeMcp_autodesk_product_help_mcp_server_html"><b>Docs</b></a>
</p>

---

Autodesk® Product Help is a Model Context Protocol (MCP) Server that connects AI agents directly to Autodesk’s official product documentation across 110+ products including Autodesk Fusion®, AutoCAD®, Revit®, Inventor®, Maya®, Civil 3D®, and more. As a secure, read-only interface, it allows AI tools to search, navigate, and retrieve trusted Autodesk help content. This enables support for natural language queries, accelerates onboarding, and provides a reliable foundation for intelligent agents built on authoritative Autodesk product documentation.

**Key Features:**

- Ask support questions using natural language.
- Learn and onboard to Autodesk products faster.
- Create a foundation for AI agents and automation.
- Available in 10 languages and 40 locales.

**Requirements:**

- No special requirements.

**About Autodesk**

The world's designers, engineers, builders, and creators trust Autodesk to help them design and make anything. From the buildings we live and work in, to the cars we drive and the bridges we drive over. From the products we use and rely on, to the movies and games that inspire us. Autodesk's Design and Make Platform unlocks the power of data to accelerate insights and automate processes, empowering our customers with the technology to create the world around us and deliver better outcomes for their business and the planet. For more information, visit [autodesk.com](https://www.autodesk.com).

> [!IMPORTANT]
> Autodesk hosts and operates this service, so there is nothing to install or run locally. This folder of the [ai-integrations](https://github.com/Autodesk/ai-integrations) repository contains the [MCP Registry](https://registry.modelcontextprotocol.io/) metadata ([`server.json`](./server.json)) and setup documentation.

## Example prompts

Once connected, try asking your assistant:

- **How-to:** "In AutoCAD, how do I create and manage layers using Layer Properties Manager?" or "In AutoCAD or Civil 3D, how do I create and assign a custom property to piping components using the Spec Editor?"
- **Troubleshooting:** "In Revit, why are my linked CAD files not visible in a view, and how can I troubleshoot the issue?" or "What does AutoCAD error 1603 mean?"
- **Getting started:** "I'm new to Revit. Show me a beginner tutorial for placing walls." or "Which Autodesk products does this help cover?"
- **Account and billing:** "How do I sign in to my Autodesk account?" or "How do I upgrade my trial to a paid subscription?"

## Getting started

**Endpoint:** `https://api.aps.autodesk.com/knowledge/public/v1/mcp`

Any MCP client that supports remote servers over Streamable HTTP can connect to this URL. No credentials are needed. A health check is available at `https://api.aps.autodesk.com/knowledge/public/health`.

### Use it in Claude or ChatGPT

Autodesk Product Help is listed in both apps, so you can connect it without any configuration:

- **Claude:** [Autodesk Product Help in the Claude directory](https://claude.ai/directory/autodesk-product-help)
- **ChatGPT:** [Autodesk Product Help in ChatGPT](https://chatgpt.com/plugins/plugin_asdk_app_6a2bbff65e5081919f78f51d2f79e3d7)

### Add the server to your client

<details>
<summary><b>Claude Code</b></summary>

```bash
claude mcp add --transport http autodesk-product-help \
  https://api.aps.autodesk.com/knowledge/public/v1/mcp
```

</details>

<details>
<summary><b>Cursor</b></summary>

<a href="https://cursor.com/en/install-mcp?name=autodesk-product-help&config=eyJ1cmwiOiJodHRwczovL2FwaS5hcHMuYXV0b2Rlc2suY29tL2tub3dsZWRnZS9wdWJsaWMvdjEvbWNwIn0%3D"><img src="https://cursor.com/deeplink/mcp-install-dark.svg" alt="Add to Cursor" height="32"></a>

Or add it manually to `~/.cursor/mcp.json` (all projects) or `.cursor/mcp.json` (one project):

```json
{
  "mcpServers": {
    "autodesk-product-help": {
      "url": "https://api.aps.autodesk.com/knowledge/public/v1/mcp"
    }
  }
}
```

</details>

<details>
<summary><b>VS Code</b></summary>

<a href="https://insiders.vscode.dev/redirect/mcp/install?name=autodesk-product-help&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fapi.aps.autodesk.com%2Fknowledge%2Fpublic%2Fv1%2Fmcp%22%7D"><img src="https://img.shields.io/badge/VS_Code-Install_server-0098FF?logo=visualstudiocode&logoColor=white" alt="Install in VS Code" height="28"></a>

Or add it manually to `.vscode/mcp.json` in your workspace:

```json
{
  "servers": {
    "autodesk-product-help": {
      "type": "http",
      "url": "https://api.aps.autodesk.com/knowledge/public/v1/mcp"
    }
  }
}
```

You can also run **MCP: Add Server** from the Command Palette, choose **HTTP**, and paste the endpoint URL.

</details>

<details>
<summary><b>Windsurf</b></summary>

Add the server to `~/.codeium/windsurf/mcp_config.json`, then restart Windsurf:

```json
{
  "mcpServers": {
    "autodesk-product-help": {
      "serverUrl": "https://api.aps.autodesk.com/knowledge/public/v1/mcp"
    }
  }
}
```

</details>

<details>
<summary><b>Other clients and SDKs</b></summary>

For other clients, add a remote HTTP server that points to the endpoint URL. The configuration key names vary, so check your client's MCP documentation.

To call the server from your own code, use an official MCP SDK.

**Python** (`pip install "mcp>=2"`):

```python
import asyncio

from mcp import ClientSession
from mcp.client.streamable_http import streamable_http_client

MCP_URL = "https://api.aps.autodesk.com/knowledge/public/v1/mcp"

async def main() -> None:
    async with streamable_http_client(MCP_URL) as (read, write):
        async with ClientSession(read, write) as session:
            await session.initialize()
            result = await session.call_tool(
                "search_help_content",
                {"query": "AutoCAD error 1603", "locale": "en_US"},
            )
            structured = result.structured_content or {}
            for doc in structured.get("results", []):
                print(doc["title"], doc["url"])


if __name__ == "__main__":
    asyncio.run(main())
```

**TypeScript / Node.js** (`npm install @modelcontextprotocol/sdk`):

```ts
import { Client } from "@modelcontextprotocol/sdk/client/index.js";
import { StreamableHTTPClientTransport } from "@modelcontextprotocol/sdk/client/streamableHttp.js";

const MCP_URL = "https://api.aps.autodesk.com/knowledge/public/v1/mcp";

const client = new Client({ name: "example", version: "1.0.0" });
await client.connect(new StreamableHTTPClientTransport(new URL(MCP_URL)));

const { structuredContent } = await client.callTool({
  name: "search_help_content",
  arguments: { query: "AutoCAD error 1603", locale: "en_US" },
});

for (const doc of structuredContent?.results ?? []) {
  console.log(doc.title, doc.url);
}

await client.close();
```

</details>

### Let your agent set it up

Paste this into your AI coding agent:

```text
Add the Autodesk Product Help MCP server to this environment.
Use the setup documentation at https://github.com/Autodesk/ai-integrations/tree/main/product-help/remote-mcp-server
and the endpoint https://api.aps.autodesk.com/knowledge/public/v1/mcp
(Streamable HTTP, no authentication). Verify the connection with initialize and tools/list.
```

### Verify the connection

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

The server exposes two tools. Both are annotated as read-only, non-destructive, and idempotent.

| Tool | Purpose |
|---|---|
| [`get_available_products`](#get_available_products) | List the supported Autodesk products, with their product codes and release codes |
| [`search_help_content`](#search_help_content) | Search Help and Support documentation and return ranked results with source URLs |

### `get_available_products`

Returns the product catalog as a list of `{ product_name, product_code, release_codes }` objects. It takes no arguments.

Call it when you need a valid `product_code` or `release_code` to narrow a search. Release codes are identifiers such as `2025`, not display names such as "AutoCAD 2025". The catalog can change over time, so treat this tool as the authoritative list rather than hardcoding values.

### `search_help_content`

Searches Autodesk documentation and support articles and returns the most relevant documents.

| Parameter | Required | Description |
|---|---|---|
| `query` | Yes | Keyword-rich search text, 2 to 1500 characters. Include the product, the feature or task, and any exact error codes. Write it in the same language as `locale`. |
| `locale` | Yes | Language and region for search and results, for example `en_US`, `de_DE`, `ja_JP`, or `zh_CN`. The tool accepts regional locale values, several of which can map to the same language (for example `de_DE`, `de_AT`, and `de_CH` are all German). The tool schema lists every accepted value. |
| `product_code` | No | Limits results to one product. Must be a value from `get_available_products`. Preferred over `product_name`. |
| `product_name` | No | Alternative to `product_code`. If both are set, they must refer to the same product. |
| `release_code` | No | Limits results to one release, for example `2025`. Requires `product_code` or `product_name`, and must be a valid release for that product. |
| `sources` | No | `sfdc_articles` (support knowledge base articles), `product_documentation` (official product documentation), or both. Searches both if omitted. |
| `max_results` | No | Number of results to return, 1 to 50. Defaults to 5. |

Each result includes `title`, `url`, `locale`, `body` (full text or an excerpt), `media_type`, and `source`. The response also includes `total_results`.

**Example call:**

```json
{
  "name": "search_help_content",
  "arguments": {
    "query": "AutoCAD Error 1603 install failed",
    "locale": "en_US",
    "product_code": "ACD",
    "max_results": 3
  }
}
```

### Best practices for agents

- Call `search_help_content` directly when the product is already known. Call `get_available_products` only when you need to look up or validate a product or release code.
- If you cannot map a product or release to an exact value from `get_available_products`, leave that filter out rather than guessing.
- Make `query` keyword-rich: include the product and the feature or task, keep the user's wording where possible, and include exact error text or codes.
- Write `query` in the same language as `locale`, and take `locale` from the user's context rather than guessing it.
- Cite the `url` of each result you use, so users can read the original article.

## Troubleshooting

MCP clients and SDKs handle the HTTP details for you. The HTTP errors below mostly affect custom integrations that call the endpoint directly.

### HTTP errors

| Response | Cause and fix |
|---|---|
| `400 Invalid Content-Type header` | Send `Content-Type: application/json` with every request. |
| `404 The requested resource does not exist` | The URL is wrong. Use the endpoint exactly as shown in [Getting started](#getting-started), without a trailing slash. |
| `405 Method Not Allowed` | The endpoint accepts JSON-RPC messages sent with `POST`. It does not offer a `GET` event stream. |
| `406 Not Acceptable` | Send `Accept: application/json, text/event-stream`. |
| `429 Too Many Requests` | The public endpoint applies fair-use rate limits. Slow down and retry with exponential backoff. The `ratelimit-remaining` response header shows how much of your allowance is left. |
| `500` with `PayloadParsingError` | The request body is not valid JSON. |

### Tool errors

When a tool call fails, the HTTP request still succeeds. The tool result has `isError: true`, and its text starts with one of the codes below, followed by what went wrong and how to fix it. Most agents can read this message and correct their own request.

| Code | Cause and fix |
|---|---|
| `INVALID_ARGUMENTS` | An argument is missing or invalid, for example a missing `locale`, a `query` shorter than 2 characters, a `max_results` above 50, or a `product_code` or `locale` value that is not in the tool schema. Use the exact values from the tool schema and `get_available_products`. |
| `INVALID_RELEASE_CODE` | The release is not available for the chosen product. The error message lists the valid release codes. |
| `RELEASE_CODE_REQUIRES_PRODUCT` | `release_code` was sent without `product_code` or `product_name`. Add a product, or remove the release filter. |
| `INVALID_PRODUCT_SCOPE` | `product_code` and `product_name` refer to different products. Send only `product_code`. |
| `INTERNAL_ERROR` | The call could not be completed. First check that the tool name matches `tools/list` exactly, because an unknown tool name also returns this code. Otherwise it is a temporary server-side problem: retry later, and [open an issue](https://github.com/Autodesk/ai-integrations/issues) if it persists. |

### No results

If `search_help_content` returns `total_results: 0`, remove the `release_code`, `product_code`, and `sources` filters one at a time, or rephrase `query` using the product's own terms for the feature.

### Reporting a problem

Send an `x-request-id` header with a new UUID on each request. The server returns the same value in its response. Include that value when you [open an issue](https://github.com/Autodesk/ai-integrations/issues) so the request can be traced.

## Security and data handling

- The service is read-only. The tools only retrieve published Help and Support content and cannot change any data.
- The public endpoint does not require authentication and does not access Autodesk accounts or customer data.
- Do not put passwords, license keys, access tokens, or other personal or sensitive data in `query` or in any other tool argument.
- To report a security vulnerability, follow the [Autodesk Vulnerability Disclosure Policy](https://www.autodesk.com/trust/security/vulnerability-disclosure-policy) and submit your report through [Autodesk on HackerOne](https://hackerone.com/autodesk). Do not open a public issue for security reports.

## About this repository

The [ai-integrations](https://github.com/Autodesk/ai-integrations) repository is the official distribution point for Autodesk AI integrations. This folder, `product-help/remote-mcp-server`, holds the Autodesk Product Help MCP files.

```text
product-help/remote-mcp-server/
├── server.json   # MCP Registry metadata
├── README.md     # Setup and usage documentation
└── LICENSE.md
```

[`server.json`](./server.json) follows the [MCP Registry schema](https://static.modelcontextprotocol.io/schemas/2025-12-11/server.schema.json) and is used to publish the server to the [Official MCP Registry](https://registry.modelcontextprotocol.io/).

See [`server.json`](./server.json) for the current registry name, version, and remote endpoint.

`server.json` is maintained by Autodesk and changes only when a new version of the service is published.

## Contributing

Contributions to the documentation and client setup examples are welcome.

1. Fork the repository and create a branch for your change.
2. Open a pull request that describes the change and how you tested it, for example with the `curl` check above.

The hosted service is not built from this repository. For feature requests or problems with the service itself, [open an issue](https://github.com/Autodesk/ai-integrations/issues).

## Support

- **Setup, registry metadata, or this documentation:** [open an issue](https://github.com/Autodesk/ai-integrations/issues).
- **Questions about Autodesk products:** visit the [Autodesk Community forums](https://forums.autodesk.com).

## License and terms

[`LICENSE.md`](./LICENSE.md) covers the files in this repository only. It does not cover the hosted service or the Autodesk content that the service returns.

Use of the Autodesk Product Help MCP server is subject to the Autodesk [Terms of Use](https://www.autodesk.com/company/terms-of-use/en/general-terms) and [Privacy Statement](https://www.autodesk.com/company/legal-notices-trademarks/privacy-statement).
