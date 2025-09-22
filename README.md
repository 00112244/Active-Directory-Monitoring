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

### 4. Active Directory Monitoring and Alerting with Prometheus

**Description:** Demonstrates how to monitor Active Directory metrics and set up alerts using Prometheus, Windows Exporter, Alertmanager, and Grafana, enabling real-time visibility into AD performance and security events.

**Key Features:**
* Full setup of Prometheus Windows Exporter on AD DS servers.
* Collection of CPU, memory, disk, and Event Log metrics.
* Grafana dashboards for real-time visualization of AD metrics.
* Prometheus alert rules and Alertmanager notifications for anomalies.

**Highlights:**
* Monitoring user logon events, failed logons, and account lockouts.
* Alerts for high CPU usage and other performance issues.
* Security-focused dashboards displaying key AD events.
* Real-time notifications for critical AD anomalies.

**[View Project](https://github.com/00112244/Active-Directory-Monitoring/blob/main/Active-Directory-Monitoring-and-Alerting-with-Prometheus.md)** 

---

## Learning Outcomes

1. **Active Directory Monitoring:**

   * Collected and analyzed AD performance and security metrics, including logon activity, account lockouts, privilege escalations, and system health indicators.

2. **Hands-on Tool Experience:**

   * Gained experience configuring and using **Grafana, Prometheus, Splunk, and Datadog** for comprehensive AD monitoring.
   * Learned to integrate data sources like Universal Forwarder, Windows Exporter, and Datadog Agent for real-time monitoring.

3. **Alerting and Incident Response:**

   * Designed and implemented alerts for performance thresholds and anomalous activities.
   * Built actionable dashboards to support SOC operations and proactive incident response.

4. **Integration and Automation:**

   * Automated metric collection, dashboard visualization, and alert notifications.
   * Developed workflows that connect monitoring agents, visualization platforms, and alert managers.

5. **Security and Operational Awareness:**

   * Improved skills in identifying and responding to AD security events.
   * Enhanced understanding of monitoring best practices for critical enterprise services.
     
---   

## Conclusion

This collection of Active Directory monitoring projects provided a comprehensive, hands-on experience in setting up, configuring, and managing monitoring solutions across enterprise environments. Through these exercises, I gained practical skills in **collecting, visualizing, and analyzing AD metrics**, while also understanding the operational and security aspects of Active Directory infrastructure.

By working with tools such as **Grafana, Prometheus, Splunk, and Datadog**, I was able to implement real-time dashboards, alerting mechanisms, and reporting systems that replicate real-world SOC and system administration scenarios. These projects demonstrate the ability to **proactively monitor AD health and security**, ensuring timely detection of anomalies and threats.




