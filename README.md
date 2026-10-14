# Autodesk AI Integrations

This repository is where Autodesk releases components that connect Autodesk products and services to AI
assistants and agents, such as [Model Context Protocol](https://modelcontextprotocol.io) (MCP) servers
and their registry metadata.

Each integration lives in its own folder with its own README, license, and release notes.

## Integrations

| Integration | Type | Folder | Registry name |
|---|---|---|---|
| Autodesk Product Help MCP | Hosted (remote), Streamable HTTP | [`product-help/remote-mcp-server`](./product-help/remote-mcp-server) | `com.autodesk.aps.api/product-help-mcp` |
| Autodesk Fusion MCP | Local, runs on your machine alongside Fusion | [`fusion/local-mcp-server`](./fusion/local-mcp-server) | `com.autodesk.aps.api/fusion` |

- **Product Help** gives AI clients read-only access to Autodesk Help and Support documentation. Autodesk
  hosts the service, so there is nothing to install.
- **Fusion** lets an MCP client create, modify, and inspect geometry in a running Autodesk Fusion session.
  Fusion must be installed and running.

## Repository layout

```text
.
├── product-help/
│   └── remote-mcp-server/   # Product Help MCP: server.json, README, LICENSE
├── fusion/
│   └── local-mcp-server/    # Fusion MCP: server.json, README, LICENSE, bundle
└── README.md
```

New integrations are added as `<product-or-area>/<integration-name>/`.

## Getting started

Open the README in the integration's folder for setup instructions for your MCP client.

## Support

Open an [issue](https://github.com/Autodesk/ai-integrations/issues) for problems with setup, registry
metadata, or documentation. Mention which integration it concerns. For questions about Autodesk products,
visit the [Autodesk Community forums](https://forums.autodesk.com).

To report a security vulnerability, follow the
[Autodesk Vulnerability Disclosure Policy](https://www.autodesk.com/trust/security/vulnerability-disclosure-policy)
and submit your report through [Autodesk on HackerOne](https://hackerone.com/autodesk). Do not open a
public issue for security reports.

## License and terms

Each integration is licensed separately. See the `LICENSE` file in its folder. Use of Autodesk products and
services is subject to the Autodesk
[Terms of Use](https://www.autodesk.com/company/terms-of-use/en/general-terms) and
[Privacy Statement](https://www.autodesk.com/company/legal-notices-trademarks/privacy-statement).
