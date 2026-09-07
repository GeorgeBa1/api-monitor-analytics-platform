# Changelog — A.P.I. Sentinel

All notable changes to A.P.I. Sentinel are documented here.

## v3.0.0 — Enterprise Platform Release

### Added / Consolidated

- Unified premium web navigation across Dashboard, APIs, Endpoints, Analytics, Alerts, Reports, Settings and Users.
- Integrated Dashboard Manual accessible from the common application navigation.
- Database-authoritative API management for active and disabled API definitions.
- API reactivation support while preserving historical monitoring records.
- HEAD and OPTIONS HTTP methods.
- JSON request payload support for POST, PUT and PATCH.
- HTTP method discovery before parallel monitoring when enabled.
- Parallel endpoint execution with configurable worker count.
- Database-backed monitoring history and analytics.
- Availability, health-score and response-time chart consistency based on persisted monitoring checks.
- Alert analytics, history and notification workflows.
- PDF, CSV, Excel and HTML reporting.
- User and role management.
- Secure credential storage through OS keyring support when available.
- Windows standalone packaging and installer documentation.
- Runtime data separation for Windows deployments.

### Operational

- Run / Stop / Reset monitoring workflows verified against the current worker architecture.
- Reset preserves API definitions and users while clearing monitoring history and generated monitoring artifacts.
- Production database guidance is centered on PostgreSQL, with SQLite retained for local development and tests.

### Security

- Production session and browser security hardening documented for deployment.
- Secrets are not intended to be stored in source code or compiled into the executable.

---

## v2.7.10 — API visibility and reactivation fix

- API Management now displays both ACTIVE and DISABLED API definitions, so soft-deleted APIs are never invisible.
- Re-adding an API whose definition was previously soft-deleted now reactivates and updates the existing database row instead of reporting a misleading duplicate-name error.
- Added explicit **Reactivate** action for disabled APIs.
- API edit can now open disabled API definitions.
- Monitoring still receives ACTIVE APIs only.
- Historical monitoring records remain preserved because API removal continues to use soft deletion.

> **Current release: v3.0.0 — Enterprise A.P.I. Sentineling, Analytics & Observability Platform.

## 2.7.10 — Database-Authoritative API Management & HTTP Methods

- API Management is now authoritative for monitoring: background/on-demand monitoring loads API definitions from the database instead of the legacy `config.yaml` endpoint list.
- Newly added APIs therefore appear in the Dashboard/Analytics and are actually monitored on the next run.
- Added HEAD and OPTIONS to the supported HTTP methods.
- Added JSON request payload support to Add/Edit API for POST, PUT and PATCH.
- Added client-side JSON validation and server-side JSON parsing.
- Preserved duplicate-name protection and per-API credentials via environment variables.

## 2.7.8 — Database-Backed Chart Data Fix

- Availability, health-score and response-time charts now share one deterministic database-backed data loader.
- Chart points are ordered by real monitoring check ID, so equal timestamps cannot reorder history.
- Availability is plotted as cumulative availability after each real check.
- Health Score uses the persisted per-check health score from `monitoring_checks`.
- Response Time uses the persisted per-check response time from `monitoring_checks`.
- Multi-API charts use the same database values and ordering as individual endpoint charts.
- Matplotlib figures are explicitly closed after saving and use the non-interactive Agg backend for server/worker safety.
- Added regression coverage for real chart values.

## 2.7.7 — Live Chart Refresh

- Dashboard chart freshness is now driven by the monitoring database check ID.
- Added stale-chart recovery when the web process starts after a monitoring worker restart.
- Added cache-safe chart URLs and browser refresh tokens.
- Added `/api/analytics-status` for live Analytics metrics and chart refresh.
- Reset removes chart freshness markers so the first new check starts a fresh chart history.
- Added regression tests for chart freshness state handling.

## 2.7.6 — Analytics & Alerts UI Density Fix
- Fixed oversized Analytics layout caused by legacy full-width chart blocks.
- Analytics KPI cards now use a compact responsive grid and charts render in a 3-column desktop layout.
- Fixed Alerts KPI/status cards wrapping into an unnecessary second row on wide screens.
- Added page-specific shell hooks while preserving the unified premium navigation.
- Reduced excess vertical and horizontal whitespace without changing monitoring functionality.

## 2.7.3
- Fixed Reset Monitoring Data for the DB-backed architecture: monitoring checks and alerts are now deleted from the database as well as report/chart files. API definitions and users are preserved.
- Prevented stale response-time history from reappearing after reset.


- Rebuilt the dashboard as a commercial-style monitoring command center.
- Added fixed sidebar navigation, responsive mobile navigation and top status bar.
- Added premium KPI cards, health ring, alert center, platform overview and endpoint health table.
- Restyled analytics chart containers and modernized Matplotlib chart rendering.
- Preserved live dashboard refresh, monitoring controls and existing backend routes.

## 2.6.1 — Database Configuration & Migration Hardening

- Database layer now loads `api_tester/.env` consistently.
- Alembic uses the same database URL resolver as the application.
- Production rejects SQLite fallback when `API_SENTINEL_ENV=production`.
- Added migration status CLI command.
- Added guidance for baselining an existing SQLite database with `alembic stamp head`.
- Fixed multi-API Matplotlib generation to use the non-GUI `Agg` backend.
- Prevented empty health-score legends when no series are available.
- Updated Windows and production database operations documentation.
- Added production SQLite fallback regression test.

## 2.6.0 — Database Migration & Production Operations

- Added Alembic production schema migrations.
- Added PostgreSQL connection pooling and pre-ping.
- Added database health/readiness endpoint and CLI.
- Added paginated repository reads with bounded limits.
- Added monitoring/alert retention operations.
- Added PostgreSQL logical backup CLI using `pg_dump`.
- Moved monitoring charts and trend/insight reads from CSV history to the database.
- Report CSV/Excel exports are regenerated from database history.
- Added production database operations documentation.

## 2.5.0 - Security Hardening

## 2.5.0 — PostgreSQL Data Architecture

- PostgreSQL-ready relational persistence layer.
- Users, APIs, monitoring checks and alerts moved to database repositories.
- One-time legacy JSON/YAML/CSV import.
- Database-backed analytics aggregate.
- SQLAlchemy + psycopg production dependencies.

- Secure session cookie configuration
- HttpOnly session cookies
- SameSite=Lax session cookies
- Secure cookies automatically enabled in production
- 1-hour permanent session timeout
- Browser security headers: X-Content-Type-Options, X-Frame-Options, Referrer-Policy, Permissions-Policy
- HSTS enabled in production

# Changelog — A.P.I. Sentinel

All notable changes to the **A.P.I. Sentinel** observability platform are documented in this file.

---

## [2.3.0] - Production Release

### Added
- **Web Dashboard & User Auth:** Πλήρες Flask Web Application με υποστήριξη User Authentication (`dashboard_auth.py`, `user_auth.py`, `users.json`).
- **UI Templates:** Ενσωμάτωση Jinja2 templates (`dashboard.html`, `endpoints.html`, `endpoint_details.html`, `analytics.html`, `alerts.html`, `report.html`, `login.html`).
- **Background Worker & Process Management:** Προσθήκη `monitor_worker.py`, `monitoring_manager.py` και διαχείριση PID μέσω `monitoring.pid`.
- **Payload & Reset Management:** Νέα modules `payload_manager.py` και `reset_manager.py` για την ασφαλή διαχείριση payloads και επανεκκίνηση μετρήσεων.
- **Dynamic Static Assets:** Αυτόματη αποθήκευση και προβολή διαγραμμάτων (`FROST_availability_chart.png`, `FROST_health_score_chart.png`, `FROST_response_time_chart.png`) στον φάκελο `static/`[cite: 1, 5].

### Operational Notes
- **Monitoring Heartbeat:** Προστέθηκε/ενσωματώθηκε monitoring heartbeat με timestamp, status και age για την παρακολούθηση της κατάστασης του monitoring worker.
- **Live Dashboard Status:** Το `/api/dashboard-status` εκθέτει την τρέχουσα monitoring και heartbeat κατάσταση.
- **Role-Based Controls:** Η τρέχουσα web εφαρμογή υποστηρίζει ADMIN, OPERATOR και VIEWER roles, με ADMIN-only RESET.
- **Dynamic Chart Refresh:** Το Dashboard χρησιμοποιεί file modification timestamps για ανανέωση των generated chart images.

### Changed
- **Rebranding:** Πλήρης μεταφορά από το παλιό "A.P.I. Sentinel" στο νέο brand **A.P.I. Sentinel**[cite: 1, 2, 4, 5].
- **Architecture Restructuring:** Διαχωρισμός του Web Dashboard (`dashboard.py` / `app.py`) από το Core Scan Engine (`main.py` / `monitor_worker.py`).

---

## [2.0.0] - Observability & Web Dashboard Infrastructure

### Added
- **Flask REST API:** Ενσωμάτωση του `/api/alerts-status` με live client-side polling ανά 5 δευτερόλεπτα[cite: 2, 3, 5].
- **Alert Status Engine:** Αυτόματος υπολογισμός Alert Status (ACTIVE, RESOLVED, UNKNOWN) μέσω του `alert_analytics.py`[cite: 2, 3, 4].

---

## [1.9.0] - Executive PDF Reporting Release

### Added
- **Executive PDF Engine:** Παραγωγή εταιρικών PDF Reports με εξώφυλλο, KPI Dashboards και γραφήματα μέσω του `pdf_reporting.py`[cite: 1, 2, 4, 5].
- **Alert History:** Καταγραφή ιστορικού ειδοποιήσεων στο `reports/alerts.csv`[cite: 2].
