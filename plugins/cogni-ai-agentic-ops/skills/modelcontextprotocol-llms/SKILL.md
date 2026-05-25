---
name: modelcontextprotocol-llms
description: 'Reference and APIs for retrieving Model Context Protocol (MCP) documentation programmatically for LLMs. You MUST load this skill when asked to search or retrieve MCP documentation.'
license: MIT
---

# modelcontextprotocol-llms

<!-- markdownlint-disable MD013 MD023 MD031 MD032 -->

## When to Use

- **Documentation Search**: Locating specific Model Context Protocol (MCP) documentation articles.
- **Article Retrieval**: Fetching the full rendered markdown of a specific MCP docs page via its `llms.txt` or related context.

## When Not to Use

- **MCP Protocol Operations**: Interacting with live MCP servers or building servers. Use appropriate tools or SDKs for that.

## Core Process

1. **Identify the Need**: Determine whether you need to search for a topic or fetch a specific known documentation path.
2. **Execute the Query**: Use `webfetch` to fetch the data from the llms.txt reference or relevant URLs.
3. **Process Content**: Extract the relevant information to answer the user's query or inform the ongoing task.

## References

To fully utilize this skill, you MUST read at least one of the links relevant to the current context:

- [Model Context Protocol](https://modelcontextprotocol.io/llms.txt)
- [Model Context Protocol Full](https://modelcontextprotocol.io/llms-full.txt) — **Caution**: Very large file (~1.3MB+). File is already plain text; must be filtered using targeted `grep`/`rg` for specific topics or sections to avoid context overflow. Use `llms.txt` first for navigation.
