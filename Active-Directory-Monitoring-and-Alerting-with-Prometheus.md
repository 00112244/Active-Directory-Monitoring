# Active Directory Monitoring and Alerting with Prometheus

## Introduction

Prometheus is an open-source monitoring and alerting toolkit with powerful data collection and querying capabilities. It can be used to **monitor Active Directory metrics in real time** and set up alerts for performance and security events.

In this project, I implemented a **comprehensive AD monitoring and alerting system** using:

* **Prometheus** for time-series data collection.
* **Prometheus Windows Exporter** for exposing AD metrics.
* **Alertmanager** for handling alerts.
* **Grafana** for dashboards and visualization.

---

## Lab Setup and Tools

* **Windows Server** with Active Directory Domain Services (AD DS)
* **Prometheus** installed on a monitoring server
* **Prometheus Windows Exporter** on AD DS servers
* **Alertmanager** for alert handling
* **Grafana** for dashboards

---

## Tool Installation

### 1. Install Prometheus Windows Exporter

* Download the exporter from the official Prometheus website.
* Install it on the Windows Server hosting AD DS:

```powershell
Start-Process -FilePath .\windows_exporter-<version>-amd64.msi -ArgumentList /quiet
```

* Configure it as a Windows service:

```powershell
New-Service -Name "windows_exporter" -BinaryPathName "C:\Program Files\windows_exporter\windows_exporter.exe" -DisplayName "Windows Exporter" -StartupType Automatic
Start-Service -Name "windows_exporter"
```

---

### 2. Install Prometheus

* Download Prometheus and extract the files.
* Configure `prometheus.yml` to scrape metrics from Windows Exporter:

```yaml
scrape_configs:
  - job_name: 'windows_exporter'
    static_configs:
      - targets: ['<AD_server_IP>:9182']
```

* Start Prometheus:

```bash
./prometheus --config.file=prometheus.yml
```

---

### 3. Install Alertmanager

* Download and extract Alertmanager.
* Configure `alertmanager.yml` to handle alerts:

```yaml
global:
  resolve_timeout: 5m
route:
  receiver: 'email-alert'
receivers:
  - name: 'email-alert'
    email_configs:
      - to: 'admin@example.com'
        from: 'alertmanager@example.com'
        smarthost: 'smtp.example.com:587'
        auth_username: 'alertmanager@example.com'
        auth_password: 'password'
```

* Start Alertmanager:

```bash
./alertmanager --config.file=alertmanager.yml
```

---

## Exercises

### Exercise 1: Configuring Prometheus Data Source

**Steps:**

1. Open `prometheus.yml`.
2. Ensure scraping of Windows Exporter metrics is configured correctly.
3. Add Alertmanager configuration:

```yaml
alerting:
  alertmanagers:
    - static_configs:
        - targets:
          - 'localhost:9093'
rule_files:
  - "alert.rules"
```

4. Restart Prometheus:

```bash
./prometheus --config.file=prometheus.yml
```

**Output:**
Prometheus scrapes data from Windows Exporter and sends alerts to Alertmanager.

---

### Exercise 2: Creating a Dashboard for AD Metrics

**Steps:**

1. Access Prometheus web interface: `http://<prometheus_server_ip>:9090`.
2. Verify Windows Exporter targets under **Status > Targets**.
3. Create a Grafana dashboard:

   * Log in to Grafana.
   * Add Prometheus as a data source.
   * Create panels for CPU usage, memory usage, logon events, etc.

**Output:**
A Grafana dashboard displaying **real-time AD metrics**.

---

### Exercise 3: Monitoring AD Logon Events

**Steps:**

1. Ensure Windows Exporter collects Event Log metrics.
2. Create a Prometheus alert rule for logon events (`alert.rules`):

```yaml
groups:
  - name: AD_Logon_Events
    rules:
      - alert: HighLogonEvents
        expr: increase(windows_eventlog_security{EventID="4624"}[5m]) > 10
        for: 10m
        labels:
          severity: warning
        annotations:
          summary: "High number of logon events"
          description: "More than 10 logon events in the last 5 minutes."
```

3. Include the alert rule file in `prometheus.yml` under `rule_files`.

**Output:**
Prometheus monitors logon events and triggers alerts for **high activity**.

---

### Exercise 4: Setting Up Alerts for AD Performance Issues

**Steps:**

1. Create a Prometheus alert rule for CPU usage:

```yaml
groups:
  - name: AD_Performance
    rules:
      - alert: HighCPUUsage
        expr: windows_cpu_time{mode="user"} > 80
        for: 5m
        labels:
          severity: critical
        annotations:
          summary: "High CPU Usage"
          description: "CPU usage is above 80% for more than 5 minutes."
```

2. Add the alert rule to `prometheus.yml`.
3. Restart Prometheus to apply changes.

**Output:**
Prometheus alerts administrators when CPU usage exceeds the threshold.

---

### Exercise 5: Visualizing AD Security Metrics

**Steps:**

1. Ensure Windows Exporter collects security metrics.
2. Create Grafana panels for:

   * Failed logon attempts: `windows_eventlog_security{EventID="4625"}`
   * Account lockouts: `windows_eventlog_security{EventID="4740"}`
3. Configure each panel’s visualization and arrange them on the dashboard.

**Output:**
A **security-focused Grafana dashboard** displaying key AD security metrics.

---

## Final Outcome

By completing this project, I implemented a **robust Active Directory monitoring and alerting system** using Prometheus, Alertmanager, and Grafana, enabling:

* Real-time visualization of AD performance metrics.
* Monitoring of logon events, failed logons, and account lockouts.
* Alerts for performance and security anomalies.
* Comprehensive dashboards for SOC operations and AD administration.
