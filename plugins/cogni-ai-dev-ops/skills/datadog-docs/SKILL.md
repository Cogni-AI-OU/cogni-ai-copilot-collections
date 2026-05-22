---
name: datadog-docs
description: 'Reference, APIs, and programmatic access for Datadog documentation and API. Use for docs retrieval or API interaction with cURL.'
license: MIT
---

# Skill: datadog-docs

<!-- markdownlint-disable MD013 MD023 MD031 MD032 -->

Execute Datadog API requests to fetch live objects, metrics, or monitor statuses, and retrieve Datadog documentation via LLM-optimized endpoints.

## When to Use

- **Documentation Search**: Locating specific Datadog documentation articles or reference materials.
- **Article Retrieval**: Fetching Datadog documentation using the provided LLM-optimized endpoints.
- When querying Datadog metrics, logs, or traces directly from the command line in an automated script.
- To retrieve and analyze the status of Datadog monitors.
- When you need to fetch a dashboard configuration JSON to inspect or backup its definition.

## When Not to Use

- When full MCP observability tools (`datadog-mcp`) are available, as they natively format data for LLM context windows.
- If the project uses Pulumi or Terraform for Datadog resource creation (use the respective Infrastructure-as-Code skill).
- When a simple web UI link to the Datadog dashboard would suffice for a human user.
- When you need to configure or install the Datadog Agent. Use `datadog-agent` instead.

## Common Pitfalls

- **Paginating Endlessly**: Running an API query that returns millions of log lines without using `jq` to truncate or filter the output, causing the agent to run out of memory.
- **Leaking API Keys**: Accidentally echoing the `DD-API-KEY` or `DD-APPLICATION-KEY` in the terminal during debugging, exposing it in the workflow logs.
- **Incorrect Endpoint Region**: Sending requests to `datadoghq.com` when the organization's Datadog instance is actually hosted on `datadoghq.eu` or `us3.datadoghq.com`, resulting in HTTP 403 or 404 errors.

## Core Process

1. **Identify the Need**: Determine what Datadog documentation or API resource is needed.
2. **Access API Reference**: Check `references/api_reference.md` for the complete catalog of API endpoint documentation links.
3. **Verify Credentials** (API calls): Ensure `DD-API-KEY` and `DD-APPLICATION-KEY` are available in the environment.
4. **Determine Datadog Site**: Default is `datadoghq.com`, but it could be `datadoghq.eu`, `us3.datadoghq.com`, etc. based on the target environment.
5. **Access Documentation** (docs lookup): Use the provided `llms.txt` to access broader documentation links.
6. **Execute API Call** (API interaction): Use `curl` to construct the API request, passing necessary headers and query parameters.
7. **Process Response**: Use tools like `jq` to parse and extract relevant data from the JSON response.

## Core Principles

- **Secure Headers**: Always pass keys via headers, never in the URL path.
- **Data Pruning**: Use `jq` or `python` to prune large JSON responses, especially when fetching dashboards or monitors.
- **Pagination**: Handle pagination when querying lists of items using `start` or `page` parameters.

## References


- [API Reference](references/api_reference.md)
  MUST be fetched when interacting with the Datadog API.
- [Datadog API cURL Examples](references/api_via_curl.md)
  MUST be fetched when constructing cURL requests for the Datadog API.
- [Datadog MCP (Bits AI)](references/bits_ai.md)
  MUST be fetched when querying or analyzing Datadog telemetry via MCP.
- [Datadog Monitors](references/monitors.md)
  MUST be fetched when designing, debugging, or troubleshooting Datadog monitor queries.
- [Datadog Agent](references/agent.md)
  MUST be fetched when configuring, installing, or troubleshooting the Datadog Agent.
- <https://docs.datadoghq.com/llms.txt> - The official Datadog documentation curated for LLMs.
  MUST be fetched for the full context.
- <https://docs.datadoghq.com/monitors/llms.txt> - The official Datadog Monitors documentation curated for LLMs.
  MUST be fetched when designing, debugging, or interacting with monitors.
- <https://docs.datadoghq.com/agent/llms.txt> - Install and configure the Agent to collect data.
  MUST be fetched when configuring, installing, or troubleshooting the Datadog Agent.
- Datadog API Documentation: <https://docs.datadoghq.com/api/latest/>
  MUST be fetched when looking up specific API endpoints missing from local references.

## Diagnostics and Troubleshooting

- `403 Forbidden`: Check `DD-API-KEY` and `DD-APPLICATION-KEY` validity and ensure they match the correct Datadog site (`datadoghq.com` vs `datadoghq.eu`).
- `429 Too Many Requests`: Implement exponential backoff if hitting API rate limits.
- `404 Not Found`: Verify the ID or endpoint path.

## What to Avoid

- Avoid logging or exposing `DD-API-KEY` or `DD-APPLICATION-KEY` in clear text outputs.
- Do not fetch massive metric datasets without strict `from` and `to` bounds to avoid overloading the context window.

## Limitations

- The agent context window can be easily overwhelmed by full dashboard JSONs. Always filter the response with `jq` when possible.
- For retrieving telemetry (logs, metrics, traces, monitors), **always prefer optimized MCP-based tools** over raw API calls if available, as they are specifically designed to optimize data size for the agent's context window.
