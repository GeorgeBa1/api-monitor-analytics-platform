# A.P.I. Sentinel — User Manual

**Version 3.0.0**

## 1. Login and First Run

1. Start A.P.I. Sentinel.
2. On a new installation, create the first **ADMIN** account through First Run Setup.
3. Sign in.
4. Confirm that the main navigation is visible.

## 2. Dashboard

The Dashboard provides the operational overview of monitored APIs, including health, availability, performance and alert information. Use the API selector where available to move between monitored APIs.

Use **Run Monitoring** to start monitoring and **Stop Monitoring** to stop the worker. **Reset Monitoring Data** clears monitoring history and generated monitoring artifacts while preserving API definitions and users.

## 3. API Management

Open **APIs** to:

- Add an API
- Edit an API
- Remove an API from active monitoring
- Reactivate a previously disabled API
- Configure HTTP method, expected status and performance thresholds

Adding an API makes it available to the next monitoring execution. Historical charts for a new API begin after its first checks.

## 4. Endpoint Overview and Details

Use **Endpoints** to review active monitored APIs. Open **View API** for endpoint-specific information and historical analysis. Disabled APIs are excluded from active endpoint monitoring views.

## 5. Analytics

Analytics presents historical and aggregate metrics including:

- Total APIs and endpoint checks
- Successful / failed checks
- Availability
- Average response time
- Health score
- Availability, response-time and health trends

## 6. Alerts

The Alerts area provides current status, severity, trends and history. Typical conditions include low health score, low availability and excessive response time.

## 7. Reports

Use Reports to generate or review CSV, Excel, HTML and PDF outputs. Reports are generated from the monitoring data layer and are intended for operational and executive consumption.

## 8. Settings

Use Settings to configure general monitoring behavior and integrations such as SMTP, Microsoft Teams and external API authentication.

Passwords, API credentials and webhook secrets should be stored through secure credential storage when available and must not be committed to Git.

## 9. Users

ADMIN users can manage accounts and roles. Supported roles are **ADMIN, OPERATOR and USER**. Passwords are stored as password hashes rather than plaintext.

## 10. Dashboard Manual

The application includes an integrated **Dashboard Manual** accessible from the main navigation on the application pages.

## 11. Recommended Operational Sequence

```text
Login
  ↓
Add / verify APIs
  ↓
Run Monitoring
  ↓
Review Dashboard
  ↓
Inspect Analytics / Alerts
  ↓
Generate Reports
```

## 12. Reset Guidance

Reset is a history operation, not an API-definition reset. After a reset, the configured APIs and users remain available while monitoring history and generated monitoring artifacts are cleared.
