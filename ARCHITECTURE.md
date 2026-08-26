# API Monitor Architecture

## Overview

API Monitor follows a modular architecture.

Each module has a dedicated responsibility.

---

## High Level Architecture

```text
Configuration
      ↓
Authentication
      ↓
API Testing
      ↓
SLA Metrics
      ↓
Trend Analytics
      ↓
Health Analytics
      ↓
Executive Dashboard
      ↓
Chart Generation
      ↓
PDF Reporting
      ↓
Alert Engine
      ↓
Notifications
      ↓
Summary
```

---

## High Level Flow

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
response_time_chart.py
    ↓
health_score_chart.py
    ↓
availability_chart.py
    ↓
reporting.py
    ↓
pdf_reporting.py
    ↓
alert_engine.py
    ↓
alert_history.py
    ↓
notifications.py
    ↓
teams_notifications.py
    ↓
summary.py
```

---

# Module Overview

## main.py

Application entry point.

Responsibilities:

- Load Configuration
- Execute Endpoint Tests
- Generate Reports
- Generate Charts
- Generate PDF Reports
- Trigger Notifications
- Display Summary

---

## config_manager.py

Handles:

- Configuration Loading
- Configuration Validation

---

## authentication.py

Handles:

- Username / Password Authentication
- Bearer Token Authentication

---

## api_testing.py

Core monitoring engine.

Handles:

- REST API Calls
- DNS Validation
- SSL Validation
- JSON Validation
- Performance Monitoring
- Health Score Collection
- Retry Logic

---

## method_discovery.py

Handles:

- GET Discovery
- POST Discovery
- PUT Discovery
- PATCH Discovery
- DELETE Discovery
- HEAD Discovery
- OPTIONS Discovery

---

## sla_metrics.py

Handles:

- Historical Tracking
- Availability Analytics
- SLA Calculations
- SLA Rating Calculations

Generated File:

```text
sla_history.csv
```

---

## trend_metrics.py

Handles:

- Average Response Time
- Minimum Response Time
- Maximum Response Time
- Response Trend
- Availability Trend
- Health Score
- Health Rating
- Health Status
- Performance Risk
- Recommendation Engine

Generated Files:

```text
trend_report.csv

trend_report.xlsx
```

---

## reporting.py

Handles:

- CSV Reports
- Excel Reports
- HTML Reports
- Executive Dashboard
- SLA Reporting

Generated Files:

```text
report.csv

report.xlsx

report.html
```

---

## pdf_reporting.py

Handles:

- Executive PDF Reports
- KPI Dashboard
- SLA Analytics
- Health Analytics
- Executive Dashboard
- Charts Integration

Generated File:

```text
report.pdf
```

---

## response_time_chart.py

Handles:

- Response Time Charts
- Historical Performance Visualization

Generated File:

```text
response_time_chart.png
```

---

## health_score_chart.py

Handles:

- Health Score Charts
- Health Trend Visualization

Generated File:

```text
health_score_chart.png
```

---

## availability_chart.py

Handles:

- Availability Charts
- Historical Availability Visualization

Generated File:

```text
availability_chart.png
```

---

## alert_engine.py

Handles:

- Alert Decision Logic
- Threshold Evaluation

Supported Rules:

```text
Health Score Threshold

Availability Threshold

Response Time Threshold
```

---

## alert_history.py

Handles:

- Alert Storage
- Alert History
- Alert Tracking

Generated File:

```text
alerts.csv
```

---

## notifications.py

Handles:

- SMTP Notifications
- Email Alert Delivery

---

## teams_notifications.py

Handles:

- Microsoft Teams Integration
- Adaptive Cards
- Power Automate Integration
- Teams Alert Delivery

---

## summary.py

Handles:

- Console Summary
- SLA Summary
- Trend Summary
- Health Summary

---

# Data Flow

```text
Endpoint
    ↓
DNS Check
    ↓
SSL Check
    ↓
HTTP Request
    ↓
Validation
    ↓
Performance Analysis
    ↓
SLA Analytics
    ↓
Trend Analytics
    ↓
Health Analytics
    ↓
Executive Dashboard
    ↓
Chart Generation
    ↓
PDF Reporting
    ↓
Alert Engine
    ↓
Notifications
    ↓
Reports & Logs
```

---

# Dashboard Architecture

```text
HTML Dashboard
        │
        ├─ Endpoint Summary
        ├─ SLA Analytics
        ├─ Trend Analytics
        ├─ Health Analytics
        ├─ Executive Dashboard
        ├─ Recommendation Engine
        ├─ Response Time Chart
        ├─ Health Score Chart
        ├─ Availability Chart
        └─ Response Preview
```

---

# PDF Architecture

```text
PDF Executive Report
        │
        ├─ Cover Page
        ├─ KPI Dashboard
        ├─ Endpoint Summary
        ├─ SLA Analytics
        ├─ Executive Dashboard
        ├─ Analytics Charts
        └─ Response Preview
```

---

# Notification Flow

```text
FAILED Endpoint
        ↓
Alert Engine
        ↓
Alert History
        ↓
Email Notification
        ↓
Teams Notification
```

OR

```text
CRITICAL Performance
        ↓
Alert Engine
        ↓
Alert History
        ↓
Email Notification
        ↓
Teams Notification
```

---

# Current Version

```text
API Monitor v1.9.0
```

Status:

```text
Production Ready
```

---

# Architecture Highlights v1.9.0

Added:

- PDF Reporting Engine
- Alert Engine
- Alert History
- Executive Dashboard
- Executive KPI Dashboard
- Availability Charts
- Health Score Charts
- Response Time Charts
- Recommendation Engine
- Trend Analytics
- PDF Executive Reporting
- PDF Footers
- Executive Cover Page
- KPI Dashboard

Status:

```text
Stable Release

Production Ready
```