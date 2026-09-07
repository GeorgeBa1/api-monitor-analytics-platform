# Multi-API Management
> **Current release: v3.0.0 — Enterprise A.P.I. Sentineling, Analytics & Observability Platform.

## What was added

The platform now supports multiple monitored APIs from the web UI instead of requiring manual edits to `config.yaml`.

### API Management tab

Admins can open **APIs** and:

- Add a new API
- Edit an existing API
- Remove an API from the monitoring configuration
- Set name, URL, HTTP method, expected status and response-time thresholds

Credentials are intentionally not stored in the web form. Protected APIs continue to use the existing environment credential mechanism.

## Multi-API analytics

When two or more APIs are configured and monitoring runs:

- Dashboard endpoint counters are calculated per API.
- Analytics shows total APIs, healthy/at-risk/unhealthy APIs, total checks, successful/failed checks, overall availability and average response time.
- Aggregate availability, health-score and response-time charts are regenerated automatically.
- Each API is drawn as a separate series; Matplotlib's default color cycle gives the series different colors.
- Adding another API automatically adds another series as soon as that API has monitoring history.

Individual API detail pages remain available for endpoint-specific analysis.

## Important

Adding an API changes the monitoring configuration immediately. The new API appears in the next monitoring execution; historical charts for that API start after its first checks.


## v3.0.0 Operational Notes

The current release uses the unified Premium UI across the Dashboard, APIs, Endpoints, Analytics, Alerts, Reports and Users areas. Monitoring controls are now operationally verified: Run checks worker startup, Stop clears stale worker state, and Reset removes monitoring history from the database and generated artifacts while preserving users and API definitions. Worker startup output is available in `monitoring.log`.
