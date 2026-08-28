# AAA ClauseBuilder MCP Server

[![Model Context Protocol compatible](https://img.shields.io/badge/Model_Context_Protocol-compatible-000000?logo=modelcontextprotocol&logoColor=white)](https://modelcontextprotocol.io)
[![License: Apache 2.0](https://img.shields.io/badge/License-Apache--2.0-blue.svg)](LICENSE)

ClauseBuilder is a hosted Model Context Protocol (MCP) service from the American Arbitration Association (AAA). It enables compatible AI clients to draft, revise, and explain arbitration and mediation clauses through the ClauseBuilder service.

## Connect an AI client

Use the hosted endpoint below with an MCP-compatible client:

```json
{
  "mcpServers": {
    "clause-builder": {
      "type": "http",
      "url": "https://mcp.adr.org/clause-builder/mcp"
    }
  }
}
```

The repository provides client-native configuration for Claude Code, Agent Plugins v1, and the MCP Registry. See the relevant manifest for each client; all configurations point to the same hosted endpoint.

## Supported packages

| Format           | Configuration                                                                           | Shared components       |
| ---------------- | --------------------------------------------------------------------------------------- | ----------------------- |
| Agent Plugins v1 | [`plugin.json`](plugin.json) and [`mcp.json`](mcp.json)                                 | [`skills/`](skills/)    |
| Claude Code      | [`.claude-plugin/plugin.json`](.claude-plugin/plugin.json) and [`.mcp.json`](.mcp.json) | [`skills/`](skills/)    |
| MCP Registry     | [`server.json`](server.json)                                                            | Hosted-service metadata |

`mcp.json` and `.mcp.json` intentionally use different transport vocabulary for their respective clients. Keep their endpoint values aligned.

## Skill behavior

The included [`draft-clause`](skills/draft-clause/SKILL.md) skill requires the ClauseBuilder MCP server for all drafting, revision, selection, and explanation requests. It preserves server-provided language and disclaimers and does not replace unavailable server output with manually drafted clauses.

## Important notice

ClauseBuilder output is provided by the hosted service. It is not legal advice. Preserve any disclaimer returned by the service and consult qualified counsel for legal guidance.

## License

Licensed under the [Apache License 2.0](LICENSE).
