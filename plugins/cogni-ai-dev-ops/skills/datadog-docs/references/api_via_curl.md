# Datadog API cURL Examples

## Commands / Usage Patterns

Fetch a specific Dashboard by ID:

```bash
curl -s -X GET "https://api.datadoghq.com/api/v1/dashboard/<dashboard_id>" \
  -H "DD-API-KEY: ${DD_API_KEY}" \
  -H "DD-APPLICATION-KEY: ${DD_APP_KEY}"
```

Search for Monitors by tag or name:

```bash
curl -s -X GET "https://api.datadoghq.com/api/v1/monitor/search?query=tag:env:prod" \
  -H "DD-API-KEY: ${DD_API_KEY}" \
  -H "DD-APPLICATION-KEY: ${DD_APP_KEY}"
```

Query Timeseries Metrics (Unix epoch timestamps):

```bash
curl -s -X GET "https://api.datadoghq.com/api/v1/query?query=system.cpu.idle{*}&from=$(date -d '1 hour ago' +%s)&to=$(date +%s)" \
  -H "DD-API-KEY: ${DD_API_KEY}" \
  -H "DD-APPLICATION-KEY: ${DD_APP_KEY}"
```

Get a specific Monitor's details:

```bash
curl -s -X GET "https://api.datadoghq.com/api/v1/monitor/<monitor_id>" \
  -H "DD-API-KEY: ${DD_API_KEY}" \
  -H "DD-APPLICATION-KEY: ${DD_APP_KEY}"
```
