---
name: draft-clause
description: Draft, revise, and explain contract clauses through the ClauseBuilder MCP server. Use for any ClauseBuilder-related request to generate or modify a contract clause, select ClauseBuilder options, or explain a ClauseBuilder result.
disable-model-invocation: false
metadata:
  displayName: Draft a Clause
  shortDescription: Draft clauses through ClauseBuilder
  defaultPrompt: Use /draft-clause to draft a contract clause.
  requiredTools:
    - type: mcp
      value: clause-builder
      transport: http
      url: https://mcp.adr.org/clause-builder/mcp
---

# Clause drafting

Use the `clause-builder` MCP server for every request within this skill's scope. Do not draft, revise, or select clause content from general knowledge, web sources, or another tool.

1. Inspect the available `clause-builder` MCP tools and their input requirements when needed.
2. Use the MCP server to obtain the requested clause, options, or explanation.
3. Preserve the server result faithfully. Clearly label any explanation that is not part of the server result.
4. Ask a focused follow-up question when the server needs missing information.

## Standard-clause intake

After using the MCP server to draft and present a new standard clause, ask: "Would you like to add any provisions to your standard clause?"

Do not ask this question when the user already expresses provision intent, including by requesting provisions, optional language, add-ons, or named extra terms. Do not ask it for clause revisions, explanations, or other non-drafting requests.

If the user wants provisions, use the MCP server to obtain the available options and continue from the user's selection. If the user declines, the standard-clause workflow is complete.

## Preserve exact language

Preserve and present any disclaimer returned by the `clause-builder` MCP server. Do not imply that any output is legal advice.

If the MCP server is unavailable or cannot complete the request, say so. Do not substitute a manually drafted clause.
