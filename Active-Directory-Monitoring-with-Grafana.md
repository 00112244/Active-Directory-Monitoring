# Active Directory Monitoring with Grafana

## Introduction

Grafana is an open-source platform for monitoring and observability. It provides an intuitive interface and flexible dashboards to visualize Active Directory (AD) metrics, making it easier to monitor the **health, performance, and security events** of AD infrastructure in real time.

In this project, I implemented a **complete Active Directory monitoring setup** using:

* **Grafana** for dashboards and alerts.
* **Prometheus** for time-series data collection.
* **Prometheus Windows Exporter** for collecting AD server performance and security metrics.

---

## Lab Setup and Tools

* **Windows Server** with Active Directory Domain Services (AD DS)
* **Prometheus Windows Exporter** (installed on AD server to expose metrics)
* **Prometheus** (installed on monitoring server)
* **Grafana** (installed on monitoring server and connected with Prometheus)

---

## Tool Installation

### 1. Install Prometheus Windows Exporter

* Download the Windows Exporter from the official Prometheus GitHub repository.
* Run the installer silently via PowerShell:

```powershell
Start-Process -FilePath .\windows_exporter-<version>-amd64.msi -ArgumentList /quiet
```

* Configure the exporter to run as a service:

```powershell
New-Service -Name "wmi_exporter" -BinaryPathName "C:\Program Files\wmi_exporter\wmi_exporter.exe" -DisplayName "WMI Exporter" -StartupType Automatic
Start-Service -Name "wmi_exporter"
```

* By default, metrics will be available at `http://<AD_server_IP>:9182/metrics`.

---

### 2. Install Prometheus

* Download and extract Prometheus.
* Edit `prometheus.yml` to scrape metrics from the Windows Exporter:

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

* Access Prometheus at `http://<prometheus_server_IP>:9090`.

---

### 3. Install Grafana

* Download Grafana and install it on the monitoring server.
* Start Grafana:

```bash
sudo systemctl start grafana-server
sudo systemctl enable grafana-server
```

* Access Grafana at: `http://<grafana_server_IP>:3000`
* Default credentials: **admin/admin** (change password after first login).

---

## Exercises

### Exercise 1: Setting up Prometheus Data Source in Grafana

**Steps:**

1. Log in to Grafana.
2. Navigate to **Configuration > Data Sources**.
3. Click **Add data source** → Select **Prometheus**.
4. Enter the Prometheus server URL (`http://<prometheus_server_IP>:9090`).
5. Click **Save & Test**.

**Output:**
Grafana successfully connects to Prometheus, confirming data ingestion.

---

### Exercise 2: Creating a Dashboard for AD Metrics

**Steps:**

1. Go to **Create > Dashboard**.
2. Add a new panel → Select metric (e.g., `windows_logical_disk_free_bytes`).
3. Choose visualization type (Graph, Gauge, etc.).
4. Click **Apply**.

**Output:**
A dashboard panel displaying **real-time AD system metrics** such as disk usage, memory, and CPU load.

---

### Exercise 3: Monitoring AD User Logon Events

**Steps:**

1. Ensure Windows Exporter is collecting event log metrics.
2. Create a new panel in Grafana.
3. Select metrics related to logon events (e.g., `windows_eventlog_security_logon`).
4. Filter event IDs (e.g., `4624` for successful logon, `4625` for failed logon).

**Output:**
A panel showing **user logon activities**, categorized into successful and failed attempts.

---

### Exercise 4: Setting Up Alerts for AD Performance Issues

**Steps:**

1. Edit a panel monitoring CPU usage or memory utilization.
2. Go to the **Alert** tab.
3. Set condition (e.g., **CPU usage > 80% for 5 minutes**).
4. Configure alert channels (e.g., email, Slack, webhook).
5. Save the alert rule.

**Output:**
Admins receive **real-time alerts** whenever AD servers experience performance issues.

---

### Exercise 5: Visualizing AD Security Events

**Steps:**

1. Create a dedicated **Security Dashboard**.
2. Add panels for:

   * Failed logon attempts (`4625`).
   * Account lockouts (`4740`).
   * Privilege escalation events.
3. Apply filters to highlight suspicious activity.
4. Arrange panels for a security overview.

**Output:**
A **security-focused dashboard** that gives visibility into failed logons, account lockouts, and elevated privilege activity in Active Directory.

---

## Final Outcome

By completing this project, I built a **comprehensive Active Directory monitoring system** using:

* **Prometheus Windows Exporter** to collect AD performance and security event metrics.
* **Prometheus** for log scraping and data storage.
* **Grafana** for real-time dashboards, performance visualization, and alerting.

This setup provides end-to-end visibility into **AD health, performance, and security events**, making it useful for **SOC operations, incident response, and AD administration**.

