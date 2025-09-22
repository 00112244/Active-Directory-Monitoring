# Active Directory Monitoring Projects



This repository contains a collection of practical projects focused on monitoring **Active Directory (AD)** environments using modern observability and SIEM tools. Each project demonstrates real-world use cases relevant to **log monitoring, security event detection, visualization, and alerting** for AD infrastructure.

---

## Purpose

* Demonstrate how to monitor and analyze Active Directory logs using different platforms.
* Showcase integration with visualization and alerting tools.
* Apply monitoring queries, dashboards, and alerts for detecting anomalies.
* Provide reproducible steps for building hands-on AD monitoring lab environments.

---

## Project List

### 1. Active Directory Monitoring with Grafana

**Description:** Demonstrates how to collect and visualize Active Directory metrics using Grafana and Prometheus Windows Exporter, enabling real-time monitoring of AD health, performance, and security events.

**Key Features:**
* Full setup of Prometheus Windows Exporter on Windows Server hosting AD DS.
* Prometheus configuration for scraping AD metrics.
* Grafana dashboards for CPU, memory, disk, and AD-specific events.
* Setting up real-time alerts for performance and security issues.

**Highlights:**
* Visualizing user logon events, failed logons, and account lockouts.
* Monitoring AD performance metrics like CPU, memory, and disk usage.
* Security-focused dashboards showing failed logons, account lockouts, and privilege escalations.
* Real-time notifications via Grafana alerts for critical AD events.

**[View Project](https://github.com/00112244/Active-Directory-Monitoring/blob/main/Active-Directory-Monitoring-with-Grafana.md)**

---

### 2. Active Directory Logs and Insights with Splunk

**Description:** Demonstrates how to collect, analyze, and visualize Active Directory logs using Splunk Enterprise and Universal Forwarder, enabling real-time monitoring of AD security and operational events.

**Key Features:**
* Full setup of Splunk Universal Forwarder on AD DS servers.
* Forwarding and indexing Windows Event Logs (System, Security, Application).
* Creating dashboards for logon events, failed logons, and account lockouts.
* Setting up real-time alerts for anomalies and critical AD events.

**Highlights:**
* Monitoring user logon and account activity.
* Detection of security events such as failed logons and privilege escalations.
* Visual dashboards for AD operational and security insights.
* Scheduled reports for ongoing AD activity analysis.

**[View Project](https://github.com/00112244/Active-Directory-Monitoring/blob/main/Active-Directory-Logs-and-Insights-with-Splunk.md)** 

---

### 3. Real-time Active Directory Metrics with Datadog

**Description:** Demonstrates how to collect, visualize, and monitor Active Directory metrics in real time using Datadog Agent, enabling administrators to track AD health, performance, and security events.

**Key Features:**
* Full setup of Datadog Agent on AD DS servers.
* Collection of Windows Event Logs (System, Security, Application) and performance metrics.
* Dashboards for CPU, memory, logon events, and AD security metrics.
* Real-time alerts for performance issues and anomalous activity.

**Highlights:**
* Monitoring user logon events and account activity.
* Tracking failed logons, account lockouts, and security events.
* Visual dashboards for AD operational and security insights.
* Real-time notifications via Datadog monitors for critical AD events.

**[View Project](https://github.com/00112244/Active-Directory-Monitoring/blob/main/Real-time-Active-Directory-Metrics-with-Datadog.md)**

---




