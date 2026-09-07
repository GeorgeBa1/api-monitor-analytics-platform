# A.P.I. Sentinel v3.0.0
> **Current release: v3.0.0 — Enterprise A.P.I. Sentineling, Analytics & Observability Platform.

## How It Works

### Overview

Το A.P.I. Sentinel είναι μια Enterprise A.P.I. Sentineling & Observability Platform για συνεχή παρακολούθηση REST APIs, health analysis, SLA monitoring, trend analytics, alerting και reporting.

Η έκδοση **v3.0.0** επεκτείνει το monitoring engine με ολοκληρωμένο Web Dashboard, Alert Analytics και Alert History.

---


## Current v3.0.0 Runtime Flow

The current implementation adds operational monitoring around the existing pipeline:

```text
Monitoring Worker
      ↓
Monitoring Cycle
      ↓
Endpoint Checks
      ↓
Metrics / Health Analytics
      ↓
Reports / Charts / Alerts
      ↓
Heartbeat Update
      ↓
Web Dashboard Live Status
```

The dashboard can retrieve the current monitoring state through `/api/dashboard-status`.
The alert interface can retrieve current alert analytics through `/api/alerts-status`.

# Monitoring Flow

Η βασική ροή του συστήματος είναι:

```text
Configuration
      ↓
Authentication
      ↓
API Testing
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
Alert Engine
      ↓
Alert History
      ↓
Notifications
      ↓
Web Dashboard
      ↓
Reports
```

---

# Step 1 - Load Configuration

Η εφαρμογή φορτώνει το configuration από:

```text
config.yaml
```

Παράδειγμα:

```yaml
timeout: 30

method_discovery: true

parallel_execution: true

max_workers: 10

endpoints:

  - name: API Test

    url: https://example.com/api

    method: GET

    expected_status: 200

    warning_threshold_ms: 1000

    critical_threshold_ms: 3000
```

---

# Step 2 - Authentication

Εάν απαιτείται authentication, το σύστημα πραγματοποιεί authentication πριν από το API monitoring.

Υποστηρίζονται:

```text
No Authentication

Basic Authentication

Bearer Token Authentication
```

---

# Step 3 - API Testing

Κάθε endpoint ελέγχεται από το monitoring engine.

Συλλέγονται:

```text
HTTP Status Code

Response Time

Response Size

Response Payload

DNS Status

SSL Status

Availability Status

Performance Status
```

---

# Step 4 - Validation

Το σύστημα πραγματοποιεί validation στα αποτελέσματα.

Ελέγχονται:

```text
Expected HTTP Status

JSON Structure

Required Fields

Expected Values

Response Time Thresholds
```

Παράδειγμα:

```text
HTTP Code: 200
Status: SUCCESS
```

---

# Step 5 - Performance Analysis

Το response time συγκρίνεται με τα thresholds του endpoint.

Παράδειγμα:

```text
Response Time: 500 ms
Performance: OK
```

```text
Response Time: 1500 ms
Performance: WARNING
```

```text
Response Time: 5000 ms
Performance: CRITICAL
```

---

# Step 6 - Health Analysis

Το σύστημα υπολογίζει την υγεία του endpoint.

Metrics:

```text
Health Score

Health Rating

Health Status

Performance Risk
```

Παράδειγμα:

```text
Health Score     : 100

Health Rating    : EXCELLENT

Health Status    : HEALTHY

Performance Risk : LOW
```

---

# Step 7 - Historical Tracking

Τα monitoring executions αποθηκεύονται ιστορικά.

Το ιστορικό SLA αποθηκεύεται στο:

```text
reports/sla_history.csv
```

Τα δεδομένα χρησιμοποιούνται για:

```text
Historical Checks

Successful Checks

Failed Checks

Availability

SLA Rating

Trend Analytics
```

---

# Step 8 - SLA Analytics

Το σύστημα υπολογίζει:

```text
Historical Checks

Successful Checks

Failed Checks

Availability SLA

SLA Rating
```

Formula:

```text
Availability (%) =
(Successful Checks / Total Checks) * 100
```

Παράδειγμα:

```text
Historical Checks : 100

Successful Checks : 99

Failed Checks     : 1

Availability SLA  : 99.00%

SLA Rating        : WARNING
```

---

# Step 9 - Trend Analytics

Το σύστημα αναλύει ιστορικά δεδομένα.

Υπολογίζονται:

```text
Average Response Time

Minimum Response Time

Maximum Response Time

Response Trend

Availability Trend
```

Παράδειγμα:

```text
Average Response Time : 111.01 ms

Minimum Response Time : 55.08 ms

Maximum Response Time : 320.72 ms

Response Trend        : IMPROVING

Availability Trend    : STABLE
```

---

# Step 10 - Alert Engine

Το Alert Engine αξιολογεί τα monitoring results.

Alert conditions:

```text
Health Score Threshold

Availability Threshold

Response Time Threshold

Health Status

Performance Risk
```

Παράδειγμα:

```text
Health Score < 80
```

ή:

```text
Availability < 99%
```

ή:

```text
Response Time > 1000 ms
```

---

# Step 11 - Alert History

Όταν δημιουργείται ή αξιολογείται ένα alert, καταγράφεται στο:

```text
reports/alerts.csv
```

Το Alert History περιέχει πληροφορίες όπως:

```text
Timestamp

Endpoint

Severity

Reason

Alert Status
```

Το alert lifecycle χρησιμοποιεί:

```text
ACTIVE

ACKNOWLEDGED

RESOLVED

CLOSED
```

---

# Alert Status Logic

Το Alert Status προκύπτει από την κατάσταση υγείας του endpoint.

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

Εάν δεν υπάρχει διαθέσιμη πληροφορία:

```text
UNKNOWN
```

---

# Step 12 - Alert Analytics

Το Web Dashboard υπολογίζει:

```text
Total Alerts

Critical Alerts

Warning Alerts

Alert Trend

Alert Status

Alert History
```

Παράδειγμα:

```text
Total Alerts    : 10

Critical Alerts : 2

Warning Alerts  : 3

Alert Trend     : MEDIUM
```

---

# Step 13 - Alert Trend

Το Alert Trend βασίζεται στον αριθμό των alerts.

```text
0 Alerts
    ↓
STABLE
```

```text
1 - 5 Alerts
    ↓
LOW
```

```text
6 - 15 Alerts
    ↓
MEDIUM
```

```text
16+ Alerts
    ↓
HIGH
```

---

# Step 14 - Notifications

Τα alerts μπορούν να σταλούν μέσω:

```text
Email

Microsoft Teams

Power Automate

Adaptive Cards
```

Παράδειγμα:

```text
A.P.I. Sentinel Alert

Endpoint: API Test

Status: FAILED

Performance: CRITICAL

HTTP Code: 500

Health Score: 20

Recommendation:
Immediate investigation required
```

---

# Step 15 - Web Dashboard

Η έκδοση v3.0.0 περιλαμβάνει Web Dashboard.

Το dashboard παρέχει:

```text
Dashboard

Endpoints

Analytics

Alerts

Reports
```

---

# Alert Dashboard

Το Alerts Dashboard περιλαμβάνει:

```text
Alert Analytics

Total Alerts

Critical Alerts

Warning Alerts

Alert Status

Alert Trend

Alert History
```

Το Alert History ανανεώνεται live μέσω:

```text
/api/alerts-status
```

Το frontend πραγματοποιεί polling κάθε:

```text
5 seconds
```

---

# Step 16 - Chart Generation

Το σύστημα δημιουργεί ιστορικά charts:

```text
Response Time Trend

Health Score Trend

Availability Trend
```

Generated files:

```text
response_time_chart.png

health_score_chart.png

availability_chart.png
```

---

# Step 17 - Reports

Το σύστημα παράγει:

```text
report.csv

report.xlsx

report.html

report.pdf

trend_report.csv

trend_report.xlsx

alerts.csv

sla_history.csv
```

---

# Step 18 - Executive Dashboard

Το Executive Dashboard παρουσιάζει:

```text
Health Rating

Health Status

Performance Risk

Recommendation

SLA Analytics

Trend Analytics

Availability

Historical Performance
```

---

# Step 19 - PDF Executive Reporting

Το PDF report περιλαμβάνει:

```text
Executive Cover Page

KPI Dashboard

Endpoint Summary

SLA Analytics

Health Analytics

Trend Analytics

Executive Dashboard

Analytics Charts

Response Preview
```

---

# Generated Logs

Το σύστημα δημιουργεί transaction logs:

```text
logs/transactions.log
```

Τα logs περιέχουν:

```text
Request Information

Response Information

HTTP Status

Response Time

Errors

Execution Details
```

---

# Complete System Flow

```text
config.yaml
      ↓
Authentication
      ↓
API Testing
      ↓
DNS / SSL Validation
      ↓
HTTP Validation
      ↓
Performance Analysis
      ↓
Health Score
      ↓
SLA Analytics
      ↓
Trend Analytics
      ↓
Alert Engine
      ↓
Alert History
      ↓
Email / Teams
      ↓
Web Dashboard
      ↓
CSV / Excel / HTML / PDF
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
