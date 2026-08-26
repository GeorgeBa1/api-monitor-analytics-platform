# Changelog

All notable changes to this project will be documented in this file.

---

## v1.9.1 - Alert History Release

### Added

- Alert History
- Alert Analytics
- Alert Statistics
- Alert Dashboard
- Current Success Streak
- Last Failure
- Alert Trend Analytics

### Generated Files

```text
alerts.csv

## v1.9.0 - Executive PDF Reporting Release

### Added

- PDF Executive Reporting
- PDF Dashboard
- Executive Cover Page
- Generated Timestamp
- PDF Footer
- KPI Dashboard
- Availability Trend PDF Charts
- Health Score Trend PDF Charts
- Response Time Trend PDF Charts
- PDF Executive Summary
- PDF Footer
- KPI Dashboard
- Colorized KPI Metrics
- Analytics Chart Integration

### Improved

- PDF Layout
- Analytics Visualization
- Executive Reporting
- Report Readability
- Dashboard Presentation

### Dashboard Features

```text
Availability SLA

Health Score

Health Rating

Performance Risk
```

### Generated Files

```text
report.pdf
```

## v1.8.0 - Analytics & Executive Dashboard Release

### Trend Analytics

Added:

- Average Response Time
- Minimum Response Time
- Maximum Response Time
- Response Trend
- Availability Trend
- Historical Performance Analysis
- Historical Health Tracking

### Health Analytics

Added:

- Health Score Engine
- Health Rating Engine
- Health Status Analytics
- Performance Risk Analytics
- Health Trend Analytics

### Executive Dashboard

Added:

- Executive Dashboard
- Health Rating Dashboard
- Health Status Dashboard
- Performance Risk Dashboard
- Recommendation Engine
- Endpoint Insights

### Charts & Visual Analytics

Added:

- Response Time Trend Charts
- Health Score Trend Charts
- Availability Trend Charts
- Historical Performance Visualizations

Generated Files:

```text
response_time_chart.png

health_score_chart.png

availability_chart.png
```

### Reporting

Added:

- trend_report.csv
- trend_report.xlsx
- Enhanced HTML Dashboard
- Analytics Dashboard Sections
- Historical Trend Reporting
- Response Preview Section

### Notifications

Added:

- Alert Engine
- Health Score Alert Rules
- Availability Alert Rules
- Response Time Alert Rules

### Improved

- HTML Reporting Engine
- Historical Analytics
- Health Calculations
- Dashboard Visibility
- Endpoint Health Insights
- Reporting Architecture

### New Metrics

```text
Health Score

Health Rating

Health Status

Performance Risk

Recommendation

Response Trend

Availability Trend
```

### New Dashboard Sections

```text
SLA Analytics

Trend Analytics

Executive Dashboard

Health Analytics

Response Time Charts

Health Score Charts

Availability Charts

Response Preview

## v1.7.0 - SLA Metrics & Availability Analytics Release

### Added

- SLA Metrics
- Availability Analytics
- Historical Availability Tracking
- Historical Availability Reports
- SLA History Storage
- Historical Statistics
- Historical Checks Tracking
- Successful Checks Tracking
- Failed Checks Tracking
- SLA Rating Classification
- SLA Analytics in Console Summary
- SLA Analytics in HTML Reports
- SLA Analytics in Excel Reports

### Improved

- Console Summary
- Availability Visibility
- Historical Monitoring Capabilities
- Reporting Engine
- Excel Report Analytics
- HTML Report Analytics

### New Metrics

The platform now calculates:

- Historical Checks
- Successful Checks
- Failed Checks
- Availability SLA %
- SLA Rating

### SLA Classification

```text
EXCELLENT  >= 99.99%

GOOD       >= 99.90%

WARNING    >= 99.00%

CRITICAL   < 99.00%
```

### Historical Data

Added:

```text
sla_history.csv
```

for long-term availability tracking and SLA calculations.

---

## v1.6.0 - Teams Notifications Release

### Added

- Microsoft Teams Alerting Integration
- Microsoft Teams Webhook Support
- Power Automate Workflow Integration
- Adaptive Card Notification Support
- Teams Alert Messages
- Failed Endpoint Alerts
- Critical Performance Alerts
- Teams Delivery Logging

### Alert Information

Teams alerts include:

- Endpoint Name
- Status
- Performance Status
- HTTP Status Code
- Response Time
- Response Size
- DNS Validation Status
- SSL Validation Status
- Health Score

### Improved

- Conditional Teams Alerting Logic
- Teams Notification Diagnostics
- Teams Logging Visibility

Teams notifications are sent only when:

```text
Endpoint Status = FAILED
```

or

```text
Performance Status = CRITICAL
```

### Fixed

- Adaptive Card Schema Issues
- InvalidBotAdaptiveCard Errors
- Teams Payload Formatting
- Teams Webhook Delivery Issues
- Malformed Schema Configuration

### Verification

- Webhook Connectivity Validated
- Adaptive Card Rendering Validated
- Teams Delivery Confirmed
- HTTP 202 Responses Confirmed

---

## v1.5.0 - Parallel Execution Release

### Added

- Parallel Execution
- Multi-threaded Endpoint Testing
- ThreadPoolExecutor Support
- Configurable Worker Threads
- Faster Multi Endpoint Monitoring

### Improved

- Scan Performance
- Large Scale Endpoint Monitoring

---

## v1.4.1 - Email Notifications Release

### Added

- Performance Alert Notifications
- SMTP Email Alert Integration
- Yahoo SMTP Support
- Yahoo App Password Authentication
- Performance Threshold Monitoring
- Performance Classification

Performance Levels:

- OK
- WARNING
- CRITICAL

- Response Time Performance Reporting
- Performance Status in HTML Reports
- Performance Status in Console Summary
- Email Alerts for Failed Endpoints
- HTML Report Enhancements

### Improved

- Project Documentation
- Reporting Engine
- HTML Report Formatting
- Monitoring Visibility
- Email Notification Framework

### Fixed

- SMTP Connection Issues
- SMTP SSL/TLS Configuration
- Reporting Module Issues
- HTML Report Generation Issues

---

## v1.4.0 - Threshold Monitoring Release

### Added

- Threshold Monitoring
- Performance Classification

Performance Levels:

- OK
- WARNING
- CRITICAL

- Email Notification Framework
- SMTP Support
- HTML Report Enhancements

---

## v1.3.0 - Method Discovery Release

### Added

- HTTP Method Discovery
- Automatic Method Detection
- HEAD Support
- OPTIONS Support
- Endpoint Capability Analysis
- Modular Architecture
- Summary Module
- Constants Module
- Configuration Module

### Refactored

- Project Structure
- Configuration Loading
- Reporting Logic
- Logging Logic

---

## v1.2.0 - Reporting Enhancements

### Added

- Progress Bar
- Excel Report Export
- Enhanced Reporting
- Improved Logging
- Response Preview Support
- Health Score Reporting

### Improved

- CSV Report Generation
- Error Handling
- Console Output

---

## v1.1.0 - Authentication Release

### Added

- Authentication Support
- Bearer Token Support
- Scheduler
- Multi Endpoint Monitoring
- Retry Mechanism
- Dynamic Payload Support
- Response Time Monitoring
- Response Size Monitoring
- Availability Metrics

### Improved

- API Testing Engine
- Configuration Flexibility

---

## v1.0.0 - Initial Release

### Features

- GET Requests
- POST Requests
- DNS Resolution Checks
- SSL Certificate Checks
- JSON Validation
- CSV Reports
- Basic Logging
- HTTP Status Validation
- Endpoint Availability Monitoring

---

## Project Evolution

```text
v1.0.0
├─ Core API Testing
├─ DNS Checks
├─ SSL Checks
└─ CSV Reports

v1.1.0
├─ Authentication
├─ Bearer Tokens
├─ Scheduler
└─ Multi Endpoint Monitoring

v1.2.0
├─ Excel Reports
├─ Progress Bar
├─ Health Score
└─ Enhanced Logging

v1.3.0
├─ Method Discovery
├─ Modular Architecture
├─ Summary Module
└─ Configuration Module

v1.4.0
├─ Threshold Monitoring
├─ Performance Classification
└─ Email Notification Framework

v1.4.1
├─ SMTP Integration
├─ Yahoo Support
├─ Email Alerts
├─ Performance Alerts
└─ HTML Reporting Enhancements

v1.5.0
├─ Parallel Execution
├─ Multi-threaded Endpoint Testing
├─ ThreadPoolExecutor Support
└─ Configurable Worker Threads

v1.6.0
├─ Microsoft Teams Notifications
├─ Teams Webhook Integration
├─ Power Automate Workflows
├─ Adaptive Cards
├─ Failed Endpoint Alerts
├─ Critical Performance Alerts
└─ Teams Message Formatting

v1.7.0
├─ SLA Metrics
├─ Availability Analytics
├─ Historical Availability Tracking
├─ SLA History Storage
├─ Historical Checks Tracking
├─ Successful Checks Tracking
├─ Failed Checks Tracking
├─ SLA Rating Classification
├─ Summary SLA Analytics
├─ HTML SLA Analytics
└─ Excel SLA Analytics

v1.8.0
├─ Trend Analytics
├─ Response Trend Detection
├─ Availability Trend Detection
├─ Health Score Engine
├─ Health Rating Engine
├─ Health Status Analytics
├─ Performance Risk Analytics
├─ Recommendation Engine
├─ Executive Dashboard
├─ Response Time Charts
├─ Health Score Charts
├─ Availability Charts
├─ Alert Engine
├─ Trend Reports
└─ Enhanced HTML Dashboard
