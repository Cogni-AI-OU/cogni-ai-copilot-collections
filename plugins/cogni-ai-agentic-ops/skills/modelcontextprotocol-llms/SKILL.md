---
name: modelcontextprotocol-llms
description: 'Reference and APIs for retrieving Model Context Protocol (MCP) documentation programmatically for LLMs. You MUST load this skill when asked to search or retrieve MCP documentation. USE FOR: fetching MCP specs, reading protocol docs, discovering server/client implementations. DO NOT USE FOR: running MCP servers, writing MCP clients, SDK usage.'
license: MIT
---

# modelcontextprotocol-llms

<!-- markdownlint-disable MD013 MD023 MD031 MD032 -->

## When to Use

- **Documentation Search**: Locating specific Model Context Protocol (MCP) documentation articles.
- **Article Retrieval**: Fetching the full rendered markdown of a specific MCP docs page via its `llms.txt` or related context.
- **Spec Verification**: Checking protocol specification details, transport options, or security considerations.
- **Client/Server Discovery**: Finding available MCP server and client implementations.

## When Not to Use

- **MCP Protocol Operations**: Interacting with live MCP servers or building servers. Use appropriate tools or SDKs for that.
- **SDK Usage**: Writing code that uses MCP SDKs directly. This skill only provides documentation context.

## Core Process

1. **Identify the Need**: Determine whether you need to search for a topic or fetch a specific known documentation path.
2. **Execute the Query**: Use `webfetch` to fetch the data from the llms.txt reference or relevant URLs.
3. **Process Content**: Extract the relevant information to answer the user's query or inform the ongoing task.

## Examples

- **Fetching protocol spec**: `webfetch https://modelcontextprotocol.io/llms.txt` and searching for "transport" or "security" sections.
- **Targeted extraction from full docs**: If `llms.txt` is insufficient, fetch `llms-full.txt` and pipe through `rg "## (Servers|Clients|Transports)"` to extract only the relevant section.

## Troubleshooting

- **Large file warning for llms-full.txt**: The full docs file is ~1.3MB+. Always fetch `llms.txt` first as a navigation index before requesting the full file. If you must use `llms-full.txt`, filter aggressively with `rg`/`grep` targeting specific section headers.
- **Stale content**: If fetched content appears outdated, check the MCP changelog or specification repository for the latest updates.

## Common Pitfalls

- **Fetching `llms-full.txt` without narrowing the scope**. Prefer the index or a targeted document when possible, and filter aggressively if you must use the full file.

## References

To fully utilize this skill, you MUST read at least one of the links relevant to the current context:

- [Model Context Protocol](https://modelcontextprotocol.io/llms.txt)
  USE FOR: navigation index, protocol overview, getting started, specification,
  server and client listings, transport options, security best practices.
- [Model Context Protocol Full](https://modelcontextprotocol.io/llms-full.txt)
  USE FOR: deep-dive into any MCP topic when llms.txt index is insufficient.
  **Caution**: Very large file (~1.3MB+). File is already plain text; must be filtered using targeted
  `grep`/`rg` for specific topics or sections to avoid context overflow. Use `llms.txt` first
  for navigation.
