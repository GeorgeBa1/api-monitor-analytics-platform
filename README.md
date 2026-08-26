# API Monitor & Analytics Platform

Current Version: 1.9.1

Release Name:
Alert Analytics Release

Status:
Stable Release

Previous Version:
v1.9.0

Next Planned Version:
v2.0.0 - Web Dashboard & Observability Platform

---

## Documentation

- README.md
- INSTALLATION.md
- USER_MANUAL.md
- HOW_IT_WORKS.md
- CHANGELOG.md
- VERSION.md

## Overview

Το API Monitor είναι ένα εργαλείο Python για monitoring, health checking και testing REST APIs.

Μπορεί να ελέγχει:

- Endpoint Availability
- DNS Resolution
- SSL Certificates
- Response Time
- Response Time Thresholds
- Response Size
- HTTP Status Codes
- JSON Responses
- Required Fields
- Expected Values
- Multiple Endpoints
- Retry Mechanism
- Authentication (Username / Password)
- Bearer Token Authentication
- CSV Reports
- Excel Reports
- HTML Reports
- Request / Response Logs
- Health Score
- Availability %
- SLA History Tracking
- Historical Availability Analytics
- SLA Rating Engine
- Historical Health Metrics
- HTTP Method Discovery
- Performance Classification
- Trend Analytics
- Response Trend Detection
- Availability Trend Detection
- Health Rating Engine
- Health Status Analytics
- Performance Risk Analytics
- Recommendation Engine
- Endpoint Insights Dashboard
- Trend Report Analytics
- Historical Health Tracking
- Historical Response Time Charts
- Historical Health Score Charts
- Availability Charts
- Executive Dashboard
- Alert Engine
- Smart Alert Rules
- Email Notifications
- SMTP Support
- Microsoft Teams Notifications
- Adaptive Card Notifications
- Power Automate Integration

---

# Features

## HTTP Methods

Υποστηρίζονται:

- GET
- POST
- PUT
- PATCH
- DELETE
- HEAD
- OPTIONS

---

## Method Discovery

Το εργαλείο μπορεί να ελέγξει αυτόματα ποιες HTTP Methods υποστηρίζει ένα endpoint.

Παράδειγμα:

```text
METHOD DISCOVERY

GET       200
POST      401
PUT       401
PATCH     401
DELETE    401
HEAD      200
OPTIONS   200
```

Configuration:

```yaml
method_discovery: true
```

---

## Authentication

Υποστηρίζονται:

### No Authentication

Public APIs.

### Username / Password

Basic Authentication μέσω credentials.

### Bearer Token

Αυτόματο login και χρήση Bearer Token.

---

## Monitoring Features

✅ Endpoint Availability

✅ DNS Resolution

✅ SSL Validation

✅ HTTP Status Validation

✅ Response Time Monitoring

✅ Response Time Threshold Monitoring

✅ Response Size Monitoring

✅ JSON Validation

✅ Required Fields Validation

✅ Expected Values Validation

✅ Health Score Calculation

✅ Availability Percentage

✅ SLA History Tracking

✅ Availability Analytics

✅ Historical Success Tracking

✅ Historical Failure Tracking

✅ SLA Rating Calculation

✅ Performance Classification

✅ Email Alert Notifications

✅ Health Rating Analytics

✅ Health Status Analytics

✅ Performance Risk Analytics

✅ Recommendation Engine

✅ Executive Dashboard

✅ Trend Report Analytics

✅ Availability Trend Analytics

---

## Performance Monitoring

Κάθε endpoint μπορεί να έχει δικά του performance thresholds.

Παράδειγμα:

```yaml
warning_threshold_ms: 1000

critical_threshold_ms: 3000
```

Παράδειγμα αποτελεσμάτων:

```text
Response Time: 450 ms
Performance: OK
```

```text
Response Time: 1500 ms
Performance: WARNING
```

```text
Response Time: 4500 ms
Performance: CRITICAL
```

Τα αποτελέσματα εμφανίζονται:

- Console Summary
- CSV Report
- Excel Report
- HTML Report

---

## Trend Analytics

The platform stores historical performance metrics
and calculates trends automatically.

Features:

✅ Average Response Time

✅ Minimum Response Time

✅ Maximum Response Time

✅ Response Trend

✅ Availability Trend

Example:

```text
TREND ANALYTICS

Average Response Time : 115.96 ms

Minimum Response Time : 69.94 ms

Maximum Response Time : 320.72 ms

Response Trend        : DEGRADING

Availability Trend    : STABLE


## Email Notifications

Το εργαλείο υποστηρίζει Email Alerts μέσω SMTP.

Υποστηρίζονται:

- Yahoo Mail
- Gmail
- Outlook
- Microsoft 365

Παράδειγμα:

```yaml
email_notifications: true

smtp:

  server: smtp.mail.yahoo.com

  port: 587

  username: myaccount@yahoo.com

  password: APP_PASSWORD

  sender: myaccount@yahoo.com

  recipients:

    - alerts@company.com
```

Τα email αποστέλλονται όταν:

- Endpoint Status = FAILED
- Performance Status = CRITICAL

Παράδειγμα Email Subject:

```text
[API Monitor] API Test FAILED
```

---

---

---

## Alert Engine

The platform includes a configurable alert engine
for proactive monitoring.

Alert Conditions:

✅ Health Score Threshold

✅ Availability Threshold

✅ Response Time Threshold

Example Rules:

```text
Health Score < 80

Availability < 99%

Response Time > 1000 ms
```

Alerts can be delivered through:

✅ Email Notifications

✅ Microsoft Teams Notifications

✅ Adaptive Cards

Example Alert:

```text
🚨 API Monitor Alert

Endpoint: API Test

Health Score: 75

Availability: 98.5%

Performance Risk: HIGH

Recommendation:
Immediate investigation required
```

---

## Executive Dashboard

The platform automatically generates an Executive Dashboard
for each monitored endpoint.

Dashboard Metrics:

✅ Health Rating

✅ Health Status

✅ Performance Risk

✅ Recommendation Engine

Example:

```text
Health Rating     : EXCELLENT

Health Status     : HEALTHY

Performance Risk  : LOW

Recommendation    : No action required

## Microsoft Teams Notifications

Το εργαλείο υποστηρίζει Microsoft Teams Alerts μέσω
Power Automate Workflows.

Οι ειδοποιήσεις εμφανίζονται σε προσωπικό chat ή channel
χρησιμοποιώντας Adaptive Cards.

### Configuration

```yaml
teams:

  enabled: true

  webhook_url: "YOUR_WORKFLOW_WEBHOOK_URL"

---

## Reporting Features

✅ CSV Reports

✅ Excel Reports

✅ HTML Reports

✅ Availability Analytics

✅ SLA Metrics Dashboard

✅ Historical Monitoring Statistics

✅ Transaction Logs

✅ Request Logging

✅ Response Logging

✅ Executive Dashboard

✅ Trend Analytics Dashboard

✅ Health Analytics Dashboard

✅ Response Time Charts

✅ Health Score Charts

✅ Availability Charts

---

## Python Packages

```bash
pip install requests
pip install pandas
pip install pyyaml
pip install openpyxl
pip install schedule
pip install rich
```

ή

```bash
pip install requests pandas pyyaml openpyxl schedule rich
```

---

### Adaptive Card Example

```text
🚨 API Monitor Alert

Endpoint: API Test

Status: FAILED

Performance: CRITICAL

HTTP Code: 500

Response Time: 4500 ms

Health Score: 20
```
---

---

## Analytics Charts

The platform automatically generates historical charts
for monitored endpoints.

Generated Charts:

✅ Response Time Trend Chart

✅ Health Score Trend Chart

✅ Availability Trend Chart

Output:

```text
reports/

JSON_Test_response_time_chart.png

JSON_Test_health_score_chart.png

JSON_Test_availability_chart.png
```

These charts are automatically embedded
into the HTML report dashboard.

---

---

## Endpoint Insights

The platform automatically generates business-oriented
endpoint insights.

Generated Metrics:

✅ Health Rating

✅ Health Status

✅ Performance Risk

✅ Recommendation

✅ Current Success Streak

✅ Last Failure

Example:

```text
Health Rating          : EXCELLENT

Health Status          : HEALTHY

Performance Risk       : LOW

Recommendation         : No action required

Current Success Streak : 57

Last Failure           : Never
```

The platform calculates advanced health indicators
using historical monitoring data.

Features:

✅ Health Score

✅ Health Rating

✅ Health Status

✅ Performance Risk

✅ Recommendation Engine

Example:

```text
Health Score     : 100

Health Rating    : EXCELLENT

Health Status    : HEALTHY

Performance Risk : LOW
```

The Health Analytics engine combines:

- Historical Availability
- Average Response Time
- Historical Health Metrics
- Endpoint Performance Trends

## Architecture

The project follows a modular architecture to improve maintainability,
readability and future feature expansion.

### Project Structure

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
├── pdf_reporting.py
├── alert_history.py
├── response_time_chart.py
├── health_score_chart.py
├── availability_chart.py
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
│
├── reports/
│   ├── report.csv
│   ├── report.xlsx
│   ├── report.html
│   ├── trend_report.csv
│   ├── trend_report.xlsx
│   ├── report.pdf
│   ├── alerts.csv
│   ├── JSON_Test_response_time_chart.png
│   ├── JSON_Test_health_score_chart.png
│   ├── JSON_Test_availability_chart.png
│   └── sla_history.csv
│
├── logs/
│   └── transactions.log
│
└── sla_history.csv
```

---

## Core Modules

- main.py
- api_testing.py
- authentication.py
- reporting.py
- logging_manager.py
- method_discovery.py
- notifications.py
- teams_notifications.py
- sla_metrics.py
- summary.py
- config_manager.py
- constants.py
- alert_engine.py
- response_time_chart.py
- health_score_chart.py
- availability_chart.py

---

## Example Configuration

```yaml
timeout: 30

method_discovery: true

email_notifications: true

smtp:

  server: smtp.mail.yahoo.com

  port: 587

  username: myaccount@yahoo.com

  password: APP_PASSWORD

  sender: myaccount@yahoo.com

  recipients:

    - alerts@company.com

endpoints:

  - name: Air Test

    url: "https://example.com/api"

    method: GET

    expected_status: 200

    warning_threshold_ms: 1000

    critical_threshold_ms: 3000

    payload: {}
```

---

## Multiple Endpoint Monitoring

Το εργαλείο μπορεί να ελέγχει πολλαπλά APIs από το ίδιο configuration file.

Παράδειγμα:

```yaml
endpoints:

  - name: API 1

    url: "https://api1.company.com"

    method: GET

    expected_status: 200

    payload: {}

  - name: API 2

    url: "https://api2.company.com"

    method: GET

    expected_status: 200

    payload: {}

  - name: API 3

    url: "https://api3.company.com"

    method: POST

    expected_status: 201

    payload: {}
```

---

## Example Summary Output

```text
======================================================================
SLA Summary
======================================================================

Availability: 100.00%
SLA Rating: EXCELLENT
Total Checks: 542
Successful Checks: 542
Failed Checks: 0

==================================================
```
<h2>Availability Analytics</h2>

<table>
    <tr>
        <td>Historical Checks</td>
        <td>{historical_checks}</td>
    </tr>
    <tr>
        <td>Successful Checks</td>
        <td>{successful_checks}</td>
    </tr>
    <tr>
        <td>Failed Checks</td>
        <td>{failed_checks}</td>
    </tr>
    <tr>
        <td>Availability</td>
        <td>{availability}%</td>
    </tr>
    <tr>
        <td>Rating</td>
        <td>{sla_rating}</td>
    </tr>
</table>
 

## SLA Metrics

The API Monitor stores historical execution data and calculates
service availability metrics.

Example:

```text
============================================================

SLA METRICS

============================================================

Historical Checks : 542

Successful Checks : 540

Failed Checks     : 2

Availability SLA  : 99.63%

SLA Rating        : GOOD

============================================================
```

## Example SLA Output

### Example 1

```text
============================================================

SLA METRICS

============================================================

Historical Checks : 500

Successful Checks : 500

Failed Checks     : 0

Availability SLA  : 100.00%

SLA Rating        : EXCELLENT

============================================================
```

### Availability Formula

```text
Availability (%) =
(Successful Checks / Total Checks) * 100
```

Example:

```text
540 / 542 * 100 = 99.63%
```
```text
======================================================================
API SUMMARY
======================================================================

API Test : SUCCESS

HTTP Code: 200

Availability: 100.0%

======================================================================

✅ SCAN COMPLETED

Total Endpoints : 1

Successful      : 1

Failed          : 0

Availability    : 100.0%

Response Time   : 197.54 ms

Performance     : OK

==================================================
```

---

## Current Feature Set
✅ Multiple Endpoint Monitoring

✅ GET Requests

✅ POST Requests

✅ PUT Requests

✅ PATCH Requests

✅ DELETE Requests

✅ HEAD Requests

✅ OPTIONS Requests

✅ Authentication Support

✅ Bearer Token Support

✅ DNS Checks

✅ SSL Checks

✅ Retry Mechanism

✅ JSON Validation

✅ Required Fields Validation

✅ Expected Values Validation

✅ Health Score

✅ Availability Metrics

✅ CSV Reports

✅ Excel Reports

✅ HTML Reports

✅ Transaction Logs

✅ Scheduler

✅ Progress Bar

✅ HTTP Method Discovery

✅ Threshold Monitoring

✅ Performance Classification

✅ SMTP Notifications

✅ Email Alerts

✅ Microsoft Teams Notifications

✅ Adaptive Cards

✅ Power Automate Integration

✅ Failed Endpoint Alerts

✅ Critical Performance Alerts

✅ SLA History Tracking

✅ Historical Availability Analytics

✅ SLA Rating Engine

✅ Adaptive Card Monitoring Alerts

✅ Teams Webhook Integration

✅ Historical Success Metrics

✅ Historical Failure Metrics

✅ Executive Dashboard

✅ Health Rating Engine

✅ Health Status Analytics

✅ Performance Risk Analytics

✅ Recommendation Engine

✅ Trend Analytics

✅ Response Time Trend Detection

✅ Availability Trend Detection

✅ Historical Health Tracking

✅ Health Score Charts

✅ Response Time Charts

✅ Availability Charts

✅ PDF Reports

✅ Executive PDF Reports

✅ KPI Dashboard

✅ PDF Executive Cover Page

✅ PDF Analytics Charts

✅ PDF Footer

✅ Alert Engine

✅ Multiple Endpoint Monitoring

✅ Alert Engine

✅ Smart Alert Rules

✅ Endpoint Insights

✅ Executive Dashboard

✅ Historical Response Time Charts

✅ Historical Health Score Charts

✅ Availability Charts

✅ Trend Reports

✅ Health 

✅ Multiple Endpoint Monitoring

✅ Alert Engine

✅ Executive Dashboard

✅ Availability Charts

---

## Version 1.9.0 Highlights

### New Features

- Executive PDF Reporting
- PDF Cover Page
- PDF Footer
- KPI Dashboard
- PDF Analytics Charts
- Generated Timestamp
- Alert History
- Alert Analytics

### Generated Reports

```text
report.pdf

alerts.csv
```

### Dashboard Features

```text
Executive KPI Dashboard

SLA Analytics

Health Analytics

Availability Charts

Response Time Charts

Health Score Charts
```

## Version 1.8.0 Highlights

### New Features

- Trend Analytics
- Response Time Trend Detection
- Availability Trend Detection
- Health Rating Engine
- Health Status Analytics
- Performance Risk Analytics
- Recommendation Engine
- Executive Dashboard
- Response Time Charts
- Health Score Charts
- Availability Charts
- Alert Engine

### Dashboard Features

### SLA Rating Scale

```text
EXCELLENT : >= 99.99%

GOOD      : >= 99.90%

WARNING   : >= 99.00%

CRITICAL  : < 99.00%
```

### Availability Formula



## Screenshots

### Dashboard

dashboard.png

### Reports

![ports.png

### PDF Report

![port_pdf.png

```text
Availability (%) =
(Successful Checks / Total Historical Checks) * 100
```
