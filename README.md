# A.P.I. Sentinel

> **Enterprise API Monitoring, Analytics & Observability Platform**

**Version:** 3.0.0  
**Status:** Stable Release

A.P.I. Sentinel is a centralized platform for monitoring, testing, analyzing and reporting on APIs and web services. It combines operational monitoring, health and SLA analytics, alerting, reporting, user management and a unified web dashboard in one solution.

## What A.P.I. Sentinel Provides

- Multi-API / multi-endpoint monitoring
- HTTP method discovery
- Parallel monitoring execution
- Endpoint health checks and health scoring
- Availability and SLA analytics
- Response-time and performance analysis
- DNS and SSL validation
- JSON structure, required-field and expected-value validation
- Configurable alert rules and alert history
- Email and Microsoft Teams notifications
- Executive PDF reporting
- CSV, Excel and HTML reporting
- Historical trend analytics
- Endpoint overview and drill-down analysis
- Role-based user management
- Secure credential storage through the OS credential store when available
- Integrated Dashboard Manual / User Guide
- Windows standalone deployment path

## Platform Areas

| Area | Purpose |
|---|---|
| **Dashboard** | Executive and operational view of API health, availability and performance |
| **APIs** | Add, edit, remove and reactivate monitored API definitions |
| **Endpoints** | Review active monitored endpoints and open endpoint details |
| **Analytics** | Historical health, availability, response-time and trend analysis |
| **Alerts** | Alert status, severity, trends and historical insights |
| **Reports** | Generate and review CSV, Excel, HTML and PDF reports |
| **Settings** | General monitoring, SMTP, Teams and external API authentication configuration |
| **Users** | Role-based administration and account lifecycle management |
| **Dashboard Manual** | Integrated operational and user documentation |

## Monitoring Workflow

```text
API Management
      ↓
Monitoring Worker
      ↓
Endpoint Checks
      ↓
Validation & Performance Analysis
      ↓
Health / SLA Analytics
      ↓
Alert Engine
      ↓
Notifications & Historical Storage
      ↓
Dashboard / Analytics / Reports
```

## API Monitoring

Supported HTTP methods include **GET, POST, PUT, PATCH, DELETE, HEAD and OPTIONS**. API definitions can be managed from the web UI without requiring manual edits to the monitoring configuration.

Each endpoint can define expected HTTP status and response-time thresholds. Protected APIs can use authentication configured through the supported credential mechanisms.

## Analytics & SLA

The platform records monitoring history and derives operational metrics such as:

- Availability percentage
- Successful and failed checks
- Average / minimum / maximum response time
- Health score and health rating
- Performance risk
- Availability trends
- Response-time trends
- Historical endpoint health

PostgreSQL is the production database target. SQLite remains available for local development and automated tests. Database-backed monitoring history is the authoritative source for analytics and reporting.

## Alerts & Notifications

Alerts can be driven by health score, availability, response time and endpoint health/performance conditions. Alert history supports lifecycle states such as **ACTIVE, ACKNOWLEDGED, RESOLVED and CLOSED** where applicable.

Notifications can be delivered through SMTP email and Microsoft Teams / Power Automate workflows with Adaptive Cards. Secrets should never be committed to source control.

## Reporting

A.P.I. Sentinel provides operational and executive reporting in:

- CSV
- Excel
- HTML
- PDF

Report files are exports/presentation artifacts. The database remains the authoritative source of monitoring history.

## Security & Production

The production configuration includes secure session cookies, HttpOnly, SameSite protections, production-only Secure cookies, security headers and HSTS when HTTPS production mode is enabled. Production deployments should use HTTPS and a strong application secret.

Credentials are intended to be stored through the OS credential store when available rather than embedded in source code or the executable.

## Windows Deployment

Version 3.0.0 includes the documentation and packaging path for a Windows standalone deployment using PyInstaller and an installer workflow. Runtime configuration, logs, reports and writable state are designed to be separated from immutable application assets so application updates do not overwrite operational data.

## Documentation

- [QUICK_START.md](QUICK_START.md)
- [INSTALLATION.md](INSTALLATION.md)
- [USER_MANUAL.md](USER_MANUAL.md)
- [HOW_IT_WORKS.md](HOW_IT_WORKS.md)
- [ARCHITECTURE.md](ARCHITECTURE.md)
- [DATABASE_ARCHITECTURE.md](DATABASE_ARCHITECTURE.md)
- [MULTI_API_MANAGEMENT.md](MULTI_API_MANAGEMENT.md)
- [SETTINGS_GUIDE.md](SETTINGS_GUIDE.md)
- [USER_MANAGEMENT.md](USER_MANAGEMENT.md)
- [PRODUCTION_HARDENING.md](PRODUCTION_HARDENING.md)
- [PRODUCTION_DATABASE_OPERATIONS.md](PRODUCTION_DATABASE_OPERATIONS.md)
- [EXE_CONFIGURATION_ARCHITECTURE.md](EXE_CONFIGURATION_ARCHITECTURE.md)
- [TROUBLESHOOTING.md](TROUBLESHOOTING.md)
- [COMMERCIAL_READINESS.md](COMMERCIAL_READINESS.md)
- [RELEASE_3_0_0.md](RELEASE_3_0_0.md)
- [CHANGELOG.md](CHANGELOG.md)

## Project Status

A.P.I. Sentinel 3.0.0 represents the transition from a development-oriented monitoring utility to a structured enterprise software platform with centralized operations, analytics, alerting, reporting and deployment documentation.

## License

See the repository license file for licensing terms.
