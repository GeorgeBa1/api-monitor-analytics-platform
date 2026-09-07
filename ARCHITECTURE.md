# A.P.I. Sentinel Architecture
> **Current release: v3.0.0 — Enterprise A.P.I. Sentineling, Analytics & Observability Platform.

## Overview

Το **A.P.I. Sentinel** ακολουθεί modular architecture με ξεχωριστά components για monitoring, analytics, reporting, alerting, notifications και web observability.

Στην **v3.0.0**, το Web Dashboard αποτελεί πλέον βασικό component της πλατφόρμας.

Η αρχιτεκτονική χωρίζεται σε:

```text
Monitoring Layer
        ↓
Analytics Layer
        ↓
Health / SLA Layer
        ↓
Alert Layer
        ↓
Reporting Layer
        ↓
Notification Layer
        ↓
Web Dashboard Layer
```

---


## Current v3.0.0 Operational Additions

The current implementation also includes:

- Background monitoring worker and monitoring process management.
- Monitoring heartbeat data with timestamp, status and age.
- Dashboard live status through `/api/dashboard-status`.
- Live alert status through `/api/alerts-status`.
- Session-based authentication and role-based authorization.
- ADMIN, OPERATOR and USER roles.
- RUN and STOP monitoring controls for ADMIN and OPERATOR.
- ADMIN-only RESET monitoring data control.
- Dynamic chart versioning based on generated static chart file timestamps.
- File-based historical storage for monitoring, SLA, trend and alert data.

# High Level Architecture

```text
                    ┌─────────────────────┐
                    │    Configuration    │
                    │   config_manager.py │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │   A.P.I. Sentineling    │
                    │    api_testing.py   │
                    └──────────┬──────────┘
                               │
              ┌────────────────┼────────────────┐
              │                │                │
              ▼                ▼                ▼
        DNS / SSL        Performance       Validation
        Checks           Monitoring         Engine
              │                │                │
              └────────────────┼────────────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │    SLA Metrics      │
                    │    sla_metrics.py   │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │   Trend Analytics   │
                    │   trend_metrics.py  │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │   Health Analytics  │
                    │ Health / Performance│
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │     Alert Engine    │
                    │   alert_engine.py   │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │  Alert Analytics    │
                    │ alert_analytics.py  │
                    └──────────┬──────────┘
                               │
                 ┌─────────────┼──────────────┐
                 │             │              │
                 ▼             ▼              ▼
            Reporting     Notifications   Web Dashboard
                 │             │              │
                 ▼             ▼              ▼
             CSV/Excel      Email/Teams   Flask API/UI
                 │                            │
                 ▼                            ▼
               PDF                     Live Dashboard
```

---

# Application Flow

```text
main.py
    ↓
config_manager.py
    ↓
authentication.py
    ↓
api_testing.py
    ↓
sla_metrics.py
    ↓
trend_metrics.py
    ↓
health analytics
    ↓
alert_engine.py
    ↓
alert_history.py
    ↓
alert_analytics.py
    ↓
reporting.py
    ↓
pdf_reporting.py
    ↓
notifications.py
    ↓
teams_notifications.py
    ↓
Web Dashboard / Flask API
```

---

# Core Modules

## main.py

Application entry point.

Responsibilities:

* Load configuration
* Initialize monitoring
* Execute endpoint tests
* Generate reports
* Generate charts
* Generate PDF reports
* Trigger alerts
* Trigger notifications
* Display summary

---

# config_manager.py

Handles:

* Configuration loading
* Configuration validation
* Endpoint configuration
* Monitoring settings
* Notification configuration

---

# authentication.py

Handles:

* Username / Password authentication
* Basic Authentication
* Bearer Token Authentication

---

# api_testing.py

Core monitoring engine.

Responsibilities:

* REST API requests
* HTTP status validation
* DNS validation
* SSL validation
* JSON validation
* Required field validation
* Expected value validation
* Response time monitoring
* Response size monitoring
* Retry logic
* Health score collection

---

# method_discovery.py

Discovers supported HTTP methods.

Supported methods:

```text
GET
POST
PUT
PATCH
DELETE
HEAD
OPTIONS
```

---

# parallel_runner.py

Handles parallel endpoint execution.

Responsibilities:

* Multi-threaded endpoint monitoring
* ThreadPoolExecutor
* Worker configuration
* Parallel scan execution

---

# scheduler.py

Handles scheduled monitoring execution.

Responsibilities:

* Periodic scans
* Scheduled endpoint monitoring
* Continuous monitoring execution

---

# sla_metrics.py

Handles SLA and availability analytics.

Responsibilities:

* Historical checks
* Successful checks
* Failed checks
* Availability calculation
* SLA rating
* Historical availability

Generated file:

```text
sla_history.csv
```

---

# trend_metrics.py

Handles historical trend analytics.

Responsibilities:

* Average response time
* Minimum response time
* Maximum response time
* Response trend
* Availability trend
* Historical performance
* Historical health tracking

Generated files:

```text
trend_report.csv

trend_report.xlsx
```

---

# Health Analytics

The Health Analytics layer calculates:

```text
Health Score
Health Rating
Health Status
Performance Risk
Recommendation
```

Example:

```text
Health Score     : 100

Health Rating    : EXCELLENT

Health Status    : HEALTHY

Performance Risk : LOW

Recommendation   : No action required
```

---

# alert_engine.py

Responsible for determining when an alert should be generated.

Supported rules:

```text
Health Score Threshold

Availability Threshold

Response Time Threshold
```

Example:

```text
Health Score < 80
        ↓
Alert

Availability < 99%
        ↓
Alert

Response Time > 1000 ms
        ↓
Alert
```

---

# alert_history.py

Responsible for persistent alert history.

Generated file:

```text
reports/alerts.csv
```

Responsibilities:

* Store alert records
* Maintain historical alerts
* Record alert events
* Preserve alert information

---

# alert_analytics.py

Το `alert_analytics.py` αποτελεί το analytics layer για το Alert History.

Responsibilities:

* Read `alerts.csv`
* Normalize CSV values
* Clean alert records
* Derive Alert Status
* Calculate Total Alerts
* Calculate Critical Alerts
* Calculate Warning Alerts
* Calculate Alert Types
* Calculate Alert Trend
* Sort Alert History
* Provide data to the Web Dashboard

---

# Alert Status Architecture

Το σύστημα χρησιμοποιεί τρία διαφορετικά status concepts.

```text
┌───────────────────────┐
│ API Check Status      │
├───────────────────────┤
│ SUCCESS               │
│ FAILED                │
└───────────┬───────────┘
            │
            ▼
┌───────────────────────┐
│ Health Status         │
├───────────────────────┤
│ HEALTHY               │
│ DEGRADED              │
│ UNHEALTHY             │
│ CRITICAL              │
└───────────┬───────────┘
            │
            ▼
┌───────────────────────┐
│ Alert Status          │
├───────────────────────┤
│ ACTIVE                │
│ RESOLVED              │
│ UNKNOWN               │
└───────────────────────┘
```

---

# Alert Status Derivation

Το Alert Status δεν προέρχεται απευθείας από το API `status`.

Αντίθετα, παράγεται από το health information.

```text
health_status
      │
      ▼
Alert Analytics
      │
      ▼
alert_status
```

Rules:

```text
UNHEALTHY
    ↓
ACTIVE
```

```text
CRITICAL
    ↓
ACTIVE
```

```text
DEGRADED
    ↓
ACTIVE
```

```text
WARNING
    ↓
ACTIVE
```

```text
HEALTHY
    ↓
RESOLVED
```

Fallback:

```text
No health information
        ↓
UNKNOWN
```

---

# Example Alert State Transition

```text
Initial State

HEALTHY
   ↓
RESOLVED
```

Endpoint degradation:

```text
HEALTHY
   ↓
DEGRADED
   ↓
ACTIVE
```

Endpoint failure:

```text
DEGRADED
   ↓
UNHEALTHY
   ↓
ACTIVE
```

Endpoint recovery:

```text
UNHEALTHY
   ↓
HEALTHY
   ↓
RESOLVED
```

---

# Important Data Model

A monitoring record can contain:

```text
timestamp

endpoint_name

url

status

performance_status

response_time_ms

http_code

health_score

health_rating

health_status

performance_risk

recommendation

historical_checks

successful_checks

failed_checks

availability_sla

sla_rating
```

The Alert Analytics layer derives:

```text
alert_status
```

from the health information.

---

# Web Dashboard Architecture

The Web Dashboard is built around Flask routes and HTML templates.

High-level flow:

```text
Browser
   │
   ▼
Flask Application
   │
   ├── Dashboard
   ├── Endpoints
   ├── Analytics
   ├── Alerts
   └── Reports
           │
           ▼
      Analytics Modules
           │
           ▼
       Data Sources
```

---

# Dashboard Navigation

```text
┌─────────────────────────────┐
│ Dashboard                   │
├─────────────────────────────┤
│ Endpoints                   │
├─────────────────────────────┤
│ Analytics                   │
├─────────────────────────────┤
│ Alerts                      │
├─────────────────────────────┤
│ Reports                     │
└─────────────────────────────┘
```

---

# Alerts Dashboard Architecture

```text
Alerts Page
     │
     ▼
GET /api/alerts-status
     │
     ▼
Flask Route
     │
     ▼
alert_analytics.py
     │
     ▼
reports/alerts.csv
     │
     ▼
JSON Response
     │
     ▼
JavaScript
     │
     ├── Total Alerts
     ├── Critical Alerts
     ├── Warning Alerts
     ├── Alert Status
     ├── Alert Trend
     └── Alert History
```

---

# `/api/alerts-status`

The live dashboard endpoint:

```text
GET /api/alerts-status
```

returns the current alert analytics.

Conceptual response:

```json
{
    "monitoring_status": "RUNNING",
    "total_alerts": 0,
    "critical_alerts": 0,
    "warning_alerts": 0,
    "alert_trend": "STABLE",
    "alert_status": "NORMAL",
    "alerts": []
}
```

---

# Live Update Architecture

The Alerts Dashboard uses client-side polling.

```text
Browser
   │
   │ every 5 seconds
   ▼
/api/alerts-status
   │
   ▼
Flask
   │
   ▼
alert_analytics.py
   │
   ▼
alerts.csv
   │
   ▼
JSON
   │
   ▼
Browser
   │
   ├── Update KPIs
   ├── Update Trend
   ├── Update Status
   └── Update Alert History
```

Refresh interval:

```text
5000 ms
```

---

# Dashboard Alert Table

The Alert History table contains:

```text
Timestamp
Endpoint
Severity
Reason
Status
```

Status is the derived Alert Status:

```text
ACTIVE
ACKNOWLEDGED
RESOLVED
CLOSED
UNKNOWN
```

The analytics layer primarily derives:

```text
ACTIVE
RESOLVED
UNKNOWN
```

while the dashboard presentation can support additional lifecycle states when supplied by the underlying data.

---

# Reporting Architecture

```text
Monitoring Data
       │
       ├───────────────┐
       │               │
       ▼               ▼
   reporting.py   pdf_reporting.py
       │               │
       ▼               ▼
 CSV / Excel / HTML    PDF
```

Generated files:

```text
report.csv

report.xlsx

report.html

report.pdf
```

---

# Chart Architecture

```text
Historical Data
       │
       ├───────────────┐
       │               │
       ▼               ▼
Response Time      Health Score
Chart              Chart
       │               │
       └───────┬───────┘
               │
               ▼
        Availability Chart
```

Modules:

```text
response_time_chart.py

health_score_chart.py

availability_chart.py
```

---

# Notification Architecture

```text
Alert Engine
     │
     ▼
Alert History
     │
     ├──────────────┐
     │              │
     ▼              ▼
   Email          Teams
     │              │
     ▼              ▼
   SMTP       Power Automate
                    │
                    ▼
              Adaptive Card
```

---

# Email Notification Flow

```text
Monitoring Result
      ↓
Alert Condition
      ↓
Alert Engine
      ↓
notifications.py
      ↓
SMTP Server
      ↓
Email Recipient
```

---

# Microsoft Teams Flow

```text
Monitoring Result
      ↓
Alert Engine
      ↓
teams_notifications.py
      ↓
Power Automate Webhook
      ↓
Adaptive Card
      ↓
Microsoft Teams
```

---

# Complete Data Flow

```text
                    CONFIGURATION
                         │
                         ▼
                  API MONITORING
                         │
          ┌──────────────┼──────────────┐
          ▼              ▼              ▼
        DNS            SSL          HTTP/API
          │              │              │
          └──────────────┼──────────────┘
                         ▼
                   VALIDATION
                         │
                         ▼
                  PERFORMANCE
                         │
                         ▼
                   HEALTH SCORE
                         │
                         ▼
                    SLA METRICS
                         │
                         ▼
                  TREND ANALYTICS
                         │
                         ▼
                  HEALTH ANALYTICS
                         │
                         ▼
                   ALERT ENGINE
                         │
                         ▼
                  ALERT HISTORY
                         │
                         ▼
                 ALERT ANALYTICS
                         │
             ┌───────────┼────────────┐
             ▼           ▼            ▼
         Reporting   Notifications  Dashboard
             │           │            │
             ▼           ▼            ▼
         CSV/Excel    Email/Teams   Flask API
             │                        │
             ▼                        ▼
            PDF                 Web Interface
```

---

# Dashboard Architecture v3.0.0

```text
                         WEB DASHBOARD
                              │
        ┌─────────────────────┼─────────────────────┐
        │                     │                     │
        ▼                     ▼                     ▼
    Dashboard             Endpoints             Analytics
        │                     │                     │
        │                     │                     │
        └─────────────────────┼─────────────────────┘
                              │
                              ▼
                           Alerts
                              │
                    ┌─────────┼─────────┐
                    │         │         │
                    ▼         ▼         ▼
                  KPIs      Trend    History
                    │         │         │
                    └─────────┼─────────┘
                              ▼
                     /api/alerts-status
                              │
                              ▼
                     alert_analytics.py
                              │
                              ▼
                       alerts.csv
```

---

# Project Structure

```text
api_tester/
│
├── main.py
├── api_testing.py
├── authentication.py
├── config_manager.py
├── logging_manager.py
├── method_discovery.py
├── reporting.py
├── summary.py
├── notifications.py
├── teams_notifications.py
├── parallel_runner.py
├── scheduler.py
├── sla_metrics.py
├── trend_metrics.py
├── alert_engine.py
├── alert_analytics.py
├── alert_history.py
├── response_time_chart.py
├── health_score_chart.py
├── availability_chart.py
├── pdf_reporting.py
├── constants.py
├── version.py
│
├── config.yaml
├── requirements.txt
├── pyproject.toml
├── .gitignore
│
├── README.md
├── CHANGELOG.md
├── INSTALLATION.md
├── ARCHITECTURE.md
├── USER_MANUAL.md
├── HOW_IT_WORKS.md
├── VERSION.md
│
├── reports/
│   ├── report.csv
│   ├── report.xlsx
│   ├── report.html
│   ├── report.pdf
│   ├── trend_report.csv
│   ├── trend_report.xlsx
│   ├── alerts.csv
│   ├── sla_history.csv
│   ├── response_time_chart.png
│   ├── health_score_chart.png
│   └── availability_chart.png
│
└── logs/
    └── transactions.log
```

---

# Module Dependencies

```text
main.py
 │
 ├── config_manager.py
 ├── authentication.py
 ├── api_testing.py
 ├── parallel_runner.py
 ├── scheduler.py
 ├── sla_metrics.py
 ├── trend_metrics.py
 ├── alert_engine.py
 ├── alert_history.py
 ├── alert_analytics.py
 ├── reporting.py
 ├── pdf_reporting.py
 ├── notifications.py
 ├── teams_notifications.py
 └── summary.py
```

---

# Data Storage

The platform currently uses file-based historical storage.

## Monitoring Reports

```text
reports/report.csv
reports/report.xlsx
reports/report.html
reports/report.pdf
```

## SLA History

```text
reports/sla_history.csv
```

## Alert History

```text
reports/alerts.csv
```

## Logs

```text
logs/transactions.log
```

---

# Observability Layers

The v3.0.0 architecture can be viewed as five observability layers.

```text
1. Monitoring
       ↓
2. Metrics
       ↓
3. Health Analytics
       ↓
4. Alerting
       ↓
5. Visualization
```

### Monitoring

Collects raw endpoint data.

### Metrics

Calculates:

* Response Time
* Availability
* SLA
* Health Score

### Health Analytics

Calculates:

* Health Rating
* Health Status
* Performance Risk
* Recommendation

### Alerting

Calculates:

* Alert Conditions
* Alert Status
* Alert History
* Alert Trend

### Visualization

Presents:

* Web Dashboard
* Analytics
* Alert History
* Charts
* Reports

---

# Architecture Highlights v3.0.0

Added:

* Web Dashboard
* Dashboard Navigation
* Live Alert Dashboard
* Alert Analytics Layer
* Alert Status Derivation
* Alert History Visualization
* Dashboard API
* Live 5-second Updates
* Health-based Alert Status
* Endpoint Observability
* Executive Monitoring Interface

---

# Current Version

```text
A.P.I. Sentinel v3.0.0
```

Release:

```text
Web Dashboard & Observability Platform
```

Status:

```text
Stable Release

Production Ready
```


## v3.0.0 Operational Notes

The current release uses the unified Premium UI across the Dashboard, APIs, Endpoints, Analytics, Alerts, Reports and Users areas. Monitoring controls are now operationally verified: Run checks worker startup, Stop clears stale worker state, and Reset removes monitoring history from the database and generated artifacts while preserving users and API definitions. Worker startup output is available in `monitoring.log`.
