# Real-time Active Directory Metrics with Datadog

## Introduction

Datadog is a monitoring and analytics platform for cloud and on-premise applications. It provides **real-time visibility into Active Directory metrics**, enabling administrators to ensure the **health, performance, and security** of AD DS servers.

In this project, I implemented a **complete Active Directory monitoring setup** using:

* **Datadog Agent** for collecting Windows performance metrics and Event Logs.
* **Datadog dashboards** for real-time visualization.
* Monitors and alerts for tracking AD performance and security events.

---

## Lab Setup and Tools

* **Windows Server** with Active Directory Domain Services (AD DS)
* **Datadog Agent** installed on AD DS servers

---

## Tool Installation

### 1. Sign Up for Datadog

* Create an account on the [Datadog website](https://www.datadoghq.com/).
* Obtain your **API key** for agent installation.

---

### 2. Install Datadog Agent on AD DS Servers

* Download the Datadog Agent for Windows.
* Install the agent on each AD server using PowerShell or CMD:

```powershell
msiexec.exe /i datadog-agent-<version>.msi APIKEY=<Your_API_Key>
```

* Configure the agent to collect Windows Event Logs and performance metrics by editing `datadog.yaml`:

```yaml
logs_enabled: true

init_config:

instances:
  - type: eventlog
    channel_path: "System"
  - type: eventlog
    channel_path: "Security"
  - type: eventlog
    channel_path: "Application"
```

---

## Exercises

### Exercise 1: Configuring the Datadog Agent

**Steps:**

1. Log in to the Datadog web interface.
2. Navigate to **Integrations > Agent > Configuration**.
3. Verify the agent is installed and reporting metrics.
4. Configure additional AD-specific metrics if needed.

**Output:**
The Datadog Agent is actively collecting data from AD DS servers.

---

### Exercise 2: Creating a Dashboard for AD Metrics

**Steps:**

1. Go to **Dashboards** → Click **New Dashboard**.
2. Add widgets for key AD metrics (CPU usage, memory usage, logon events).
3. Configure visualization type and data source for each widget.
4. Arrange widgets and save the dashboard.

**Output:**
A **dashboard displaying real-time AD metrics** is created.

---

### Exercise 3: Monitoring AD Logon Events

**Steps:**

1. Ensure the Datadog Agent collects Windows Event Logs.
2. Add a new widget to the dashboard for logon events.
3. Filter logon events using the query:

```text
source:win32_event_log eventID:4624
```

4. Configure the widget and save changes.

**Output:**
A widget displaying **real-time logon events** is added to the dashboard.

---

### Exercise 4: Setting Up Alerts for AD Performance Issues

**Steps:**

1. Go to **Monitors** → Click **New Monitor**.
2. Select the metric to monitor (e.g., CPU usage).
3. Define alert conditions (e.g., CPU usage > 80% for 5 minutes).
4. Configure notification channels and save the monitor.

**Output:**
Admins are notified in real time about **AD performance issues**.

---

### Exercise 5: Visualizing AD Security Metrics

**Steps:**

1. Create widgets in the dashboard for security metrics (failed logon attempts, account lockouts).
2. Use appropriate queries to filter data.
3. Configure visualizations for each widget.
4. Arrange widgets for a **comprehensive security overview**.

**Output:**
A security-focused section of the dashboard displays **key AD security metrics** in real time.

---

## Final Outcome

By completing this project, I implemented a **real-time Active Directory monitoring system** using Datadog, enabling:

* Visualization of AD performance metrics.
* Tracking of logon events, failed logons, and account lockouts.
* Creation of dashboards, alerts, and monitoring rules for SOC operations and AD administration.
