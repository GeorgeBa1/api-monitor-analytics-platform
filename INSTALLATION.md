# A.P.I. Sentinel v3.0.0
> **Current release: v3.0.0 — Enterprise A.P.I. Sentineling, Analytics & Observability Platform.

# Installation Guide

## Requirements

* Python 3.10+
* pip
* Internet Connectivity

---


## Current v3.0.0 Runtime Notes

Η τρέχουσα εφαρμογή περιλαμβάνει Flask Web Dashboard, background monitoring worker, monitoring heartbeat, live dashboard/alert APIs και session-based authentication.

Το production runtime χρησιμοποιεί τα υπάρχοντα project paths για configuration, reports, charts, logs και historical data.

# Clone Repository

```bash
git clone https://github.com/YOUR_USERNAME/api-monitor.git

cd api-monitor
```

---

# Create Virtual Environment

```bash
python -m venv .venv
```

---

# Activate Virtual Environment

## Windows

```bash
.venv\Scripts\activate
```

## Linux / macOS

```bash
source .venv/bin/activate
```

---

# Install Dependencies

```bash
pip install requests pandas pyyaml openpyxl schedule rich matplotlib flask
```

ή:

```bash
pip install requests pandas pyyaml openpyxl schedule rich matplotlib flask
```

Εάν υπάρχει `requirements.txt`, προτιμάται:

```bash
pip install -r requirements.txt
```

---

# Configuration

Δημιούργησε:

```text
runtime configuration
```

Παράδειγμα:

```yaml
timeout: 30

method_discovery: true

parallel_execution: false

max_workers: 10

email_notifications: true

teams:

  enabled: true

  webhook_url: YOUR_WEBHOOK_URL

alerts:

  health_score_threshold: 80

  availability_threshold: 99

  response_time_threshold: 1000

endpoints:

  - name: API Test

    url: https://jsonplaceholder.typicode.com/todos/1

    method: GET

    expected_status: 200

    warning_threshold_ms: 1000

    critical_threshold_ms: 3000

    payload: {}
```

---

# Run Monitoring

```bash
python main.py
```

---

# Run Web Dashboard

Εάν το Web Dashboard εκκινεί από το Flask application:

```bash
python dashboard.py
```

Στη συνέχεια άνοιξε το dashboard από τον browser στη διεύθυνση που εμφανίζει το Flask application.

Το Alerts Dashboard χρησιμοποιεί:

```text
/api/alerts-status
```

για live ενημέρωση.

---

# Supported Features

Η έκδοση v3.0.0 υποστηρίζει:

✅ Multiple Endpoint Monitoring

✅ GET

✅ POST

✅ PUT

✅ PATCH

✅ DELETE

✅ HEAD

✅ OPTIONS

✅ Basic Authentication

✅ Bearer Token Authentication

✅ DNS Validation

✅ SSL Validation

✅ Response Time Monitoring

✅ Response Size Monitoring

✅ JSON Validation

✅ Required Fields Validation

✅ Expected Values Validation

✅ Retry Mechanism

✅ Parallel Execution

✅ HTTP Method Discovery

✅ Health Score

✅ Health Rating

✅ Health Status

✅ Performance Risk

✅ Recommendation Engine

✅ SLA Metrics

✅ Availability Analytics

✅ Historical Tracking

✅ Trend Analytics

✅ Response Time Trends

✅ Availability Trends

✅ Health Score Trends

✅ Alert Engine

✅ Smart Alert Rules

✅ Alert History

✅ Alert Analytics

✅ Alert Status Tracking

✅ Web Dashboard

✅ Live Alert Dashboard

✅ Email Notifications

✅ Microsoft Teams Notifications

✅ Power Automate Integration

✅ Adaptive Cards

✅ CSV Reports

✅ Excel Reports

✅ HTML Reports

✅ PDF Reports

---

# Generated Files

```text
reports/

├── report.csv
├── report.xlsx
├── report.html
├── report.pdf
├── trend_report.csv
├── trend_report.xlsx
├── alerts.csv
├── sla_history.csv
│
├── JSON_Test_response_time_chart.png
├── JSON_Test_health_score_chart.png
└── JSON_Test_availability_chart.png
```

Logs:

```text
logs/

└── transactions.log
```

---

# Alert History

Το Alert History αποθηκεύεται:

```text
reports/alerts.csv
```

Το αρχείο περιέχει:

```text
Timestamp

Endpoint

Severity

Reason

Alert Status
```

Το alert status μπορεί να είναι:

```text
ACTIVE

ACKNOWLEDGED

RESOLVED

CLOSED

UNKNOWN
```

---

# Verify Installation

Μετά την εγκατάσταση, το monitoring engine θα πρέπει να εμφανίσει παρόμοιο αποτέλεσμα:

```text
============================================================

A.P.I. Sentinel v3.0.0

============================================================

Loading configuration...

Testing APIs...

SCAN COMPLETED

Total Endpoints : 1

Successful      : 1

Failed          : 0

Availability    : 100.00%

SLA Rating      : EXCELLENT

Health Rating   : EXCELLENT
```

---

# Web Dashboard Verification

Έλεγξε ότι λειτουργούν:

```text
Dashboard

Endpoints

Analytics

Alerts

Reports
```

Στο Alerts Dashboard πρέπει να εμφανίζονται:

```text
Total Alerts

Critical Alerts

Warning Alerts

Alert Status

Alert Trend

Alert History
```

---

# Live Alert Updates

Το Alerts Dashboard πραγματοποιεί αυτόματη ενημέρωση κάθε:

```text
5 seconds
```

μέσω:

```text
GET /api/alerts-status
```

Το endpoint επιστρέφει:

```json
{
    "monitoring_status": "...",
    "total_alerts": 0,
    "critical_alerts": 0,
    "warning_alerts": 0,
    "alert_trend": "STABLE",
    "alerts": []
}
```

---

# Troubleshooting

## ModuleNotFoundError

Εκτέλεσε:

```bash
pip install -r requirements.txt
```

ή:

```bash
pip install requests pandas pyyaml openpyxl schedule rich matplotlib flask
```

---

## Dashboard Not Starting

Έλεγξε:

```text
app.py
```

και ότι το Flask application ξεκινά χωρίς errors.

---

## Alerts Dashboard Empty

Έλεγξε ότι υπάρχει:

```text
reports/alerts.csv
```

και ότι περιέχει valid CSV data.

---

## Alert History Shows Duplicates

Έλεγξε το `alert_analytics.py`.

Η προσθήκη κάθε alert πρέπει να γίνεται μόνο μία φορά:

```python
alerts.append(clean_row)
```

και όχι:

```python
alerts.append(clean_row)
alerts.append(clean_row)
```

---

## Alert Status Shows UNKNOWN

Έλεγξε τα fields:

```text
health_status

health_rating
```

Το σύστημα χρησιμοποιεί αυτά τα values για να παράγει το `alert_status`.

---

## Charts Not Generated

Έλεγξε ότι υπάρχει εγκατεστημένο το:

```bash
pip install matplotlib
```

---

## HTML Dashboard Not Generated

Έλεγξε ότι υπάρχει το αντίστοιχο HTML template μέσα στο project.

---

# Installation Completed

Μία επιτυχημένη εγκατάσταση πρέπει να παρέχει:

```text
A.P.I. Sentineling

SLA Analytics

Trend Analytics

Health Analytics

Alert Engine

Alert History

Alert Analytics

Web Dashboard

Live Alert Updates

CSV Reports

Excel Reports

HTML Reports

PDF Reports

Email Notifications

Microsoft Teams Notifications
```

---

# Version

```text
A.P.I. Sentinel v3.0.0

Release:
Web Dashboard & Observability Platform

Status:
Stable / Production Ready
```


## v3.0.0 Operational Notes

The current release uses the unified Premium UI across the Dashboard, APIs, Endpoints, Analytics, Alerts, Reports and Users areas. Monitoring controls are now operationally verified: Run checks worker startup, Stop clears stale worker state, and Reset removes monitoring history from the database and generated artifacts while preserving users and API definitions. Worker startup output is available in `monitoring.log`.


## A.P.I. Sentinel 3.0.0 Installation Model

For the current application, API definitions are managed from the **APIs** page and persisted in the database. Do not treat a checked-in YAML file as the authoritative API inventory.

For Windows standalone deployment, use the packaged executable and installer workflow described in `EXE_CONFIGURATION_ARCHITECTURE.md` and `COMMERCIAL_READINESS.md`.
