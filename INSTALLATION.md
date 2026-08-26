# API Monitor Installation Guide

## Requirements

- Python 3.10+
- pip
- Internet Connectivity

---

## Clone Repository

```bash
git clone https://github.com/YOUR_USERNAME/api-monitor.git

cd api-monitor
```

---

## Create Virtual Environment

```bash
python -m venv .venv
```

---

## Activate Virtual Environment

### Windows

```bash
.venv\Scripts\activate
```

### Linux / macOS

```bash
source .venv/bin/activate
```

---

## Install Dependencies

```bash
pip install requests
pip install pandas
pip install pyyaml
pip install openpyxl
pip install schedule
pip install rich
pip install matplotlib
```

or

```bash
pip install requests pandas pyyaml openpyxl schedule rich matplotlib
```

---

## Configure

Create:

```text
config.yaml
```

Example:

```yaml
timeout: 30

method_discovery: true

parallel_execution: false

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

## Supported Features

The platform supports:

✅ Multiple Endpoint Monitoring

✅ HTTP Method Discovery

✅ Bearer Token Authentication

✅ Basic Authentication

✅ DNS Validation

✅ SSL Validation

✅ Response Time Monitoring

✅ Performance Classification

✅ JSON Validation

✅ Required Field Validation

✅ Expected Value Validation

✅ SLA Metrics

✅ Historical Availability Tracking

✅ Trend Analytics

✅ Health Rating Engine

✅ Health Status Analytics

✅ Performance Risk Analytics

✅ Recommendation Engine

✅ Executive Dashboard

✅ Response Time Charts

✅ Health Score Charts

✅ Availability Charts

✅ Email Notifications

✅ Microsoft Teams Notifications

✅ Alert Engine

---

## Run

```bash
python main.py
```

---

## Generated Files

```text
reports/

├── report.csv
├── report.xlsx
├── report.html
├── trend_report.csv
├── trend_report.xlsx
├── JSON_Test_response_time_chart.png
├── JSON_Test_health_score_chart.png
├── JSON_Test_availability_chart.png
└── sla_history.csv

logs/

└── transactions.log
```

---

## Verify Installation

Expected output:

```text
============================================================
API Monitor v1.8.0
============================================================

Loading configuration...

Testing APIs...

✅ SCAN COMPLETED

Total Endpoints : 1

Successful      : 1

Failed          : 0

Availability    : 100.0%

SLA Rating      : EXCELLENT

Health Rating   : EXCELLENT
```

---

## HTML Dashboard

The platform automatically generates an HTML Executive Dashboard.

Dashboard Includes:

✅ Endpoint Summary

✅ SLA Analytics

✅ Executive Dashboard

✅ Health Rating

✅ Health Status

✅ Performance Risk

✅ Recommendation Engine

✅ Response Time Trend Chart

✅ Health Score Trend Chart

✅ Availability Trend Chart

✅ Response Preview

Output:

```text
reports/report.html
```

---

## Troubleshooting

### Missing Python Package

```text
ModuleNotFoundError
```

Install dependencies:

```bash
pip install requests pandas pyyaml openpyxl schedule rich matplotlib
```

---

### Teams Notifications Not Working

Verify:

```yaml
teams:

  enabled: true

  webhook_url: YOUR_WEBHOOK_URL
```

---

### Charts Not Generated

Verify that:

```text
reports/

JSON_Test_response_time_chart.png

JSON_Test_health_score_chart.png

JSON_Test_availability_chart.png
```

are created after execution.

---

### HTML Report Not Generated

Verify:

```text
api_tester/templates/report_template.html
```

exists and is accessible.

---

## Installation Completed

Successful installation should generate:

```text
CSV Reports

Excel Reports

HTML Dashboard

SLA Analytics

Trend Analytics

Health Analytics

Availability Analytics
