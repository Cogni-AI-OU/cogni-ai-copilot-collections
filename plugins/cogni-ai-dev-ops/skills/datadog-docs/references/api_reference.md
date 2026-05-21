# Datadog API Reference

Execute Datadog API requests to fetch live objects, metrics, or monitor statuses using API keys.

## Core Process

1. **Verify Credentials**: Ensure `DD_API_KEY` and `DD_APP_KEY` are available in the environment.
2. **Determine Datadog Site**: Default is `datadoghq.com`, but it could be `datadoghq.eu`, `us3.datadoghq.com`, etc. based on the target environment.
3. **Execute API Call**: Construct the API request, passing necessary headers and query parameters.
4. **Process Response**: Use text processing tools to parse and extract relevant data from the JSON response.

## Core Principles

- **Secure Headers**: Always pass keys via headers, never in the URL path.
- **Data Pruning**: Prune large JSON responses, especially when fetching dashboards or monitors.
- **Pagination**: Handle pagination when querying lists of items using `start` or `page` parameters.

## Diagnostics and Troubleshooting

- `403 Forbidden`: Check `DD_API_KEY` and `DD_APP_KEY` validity and ensure they match the correct Datadog site (`datadoghq.com` vs `datadoghq.eu`).
- `429 Too Many Requests`: Implement exponential backoff if hitting API rate limits.
- `404 Not Found`: Verify the ID or endpoint path.

## References

- [Datadog API cURL Examples](api_via_curl.md)
- Datadog API Documentation: <https://docs.datadoghq.com/api/latest/>
- [Official Datadog LLM Documentation](https://docs.datadoghq.com/api_reference/llms.txt)
  MUST be fetched for comprehensive catalog of all Datadog API endpoints.
