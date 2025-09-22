# Active Directory Logs and Insights with Splunk

## Introduction

Splunk is a powerful platform for searching, monitoring, and analyzing machine-generated data. It is particularly effective for **collecting and analyzing Active Directory (AD) logs**, providing insights into security and operational events.

In this project, I implemented a **comprehensive AD monitoring setup** using:

* **Splunk Enterprise** for data collection, indexing, and visualization.
* **Splunk Universal Forwarder** on AD DS servers for log forwarding.
* Dashboards, alerts, and reports to monitor user activity, security events, and anomalies.

---

## Lab Setup and Tools

* **Windows Server** with Active Directory Domain Services (AD DS)
* **Splunk Enterprise** installed on a monitoring server
* **Splunk Universal Forwarder** installed on AD DS servers

---

## Tool Installation

### 1. Install Splunk Enterprise

* Download Splunk Enterprise from the official Splunk website.
* Follow the OS-specific installation instructions.
* Start Splunk:

```bash
sudo /opt/splunk/bin/splunk start --accept-license
```

* Create an admin account and set the password.

---

### 2. Install Universal Forwarder on AD DS Servers

* Download the Splunk Universal Forwarder from the official Splunk website.
* Install the forwarder silently on each AD server:

```powershell
msiexec.exe /i splunkforwarder-<version>-x64-release.msi /quiet
```

* Configure the forwarder to send Windows Event Logs to the Splunk server:

```powershell
& "C:\Program Files\SplunkUniversalForwarder\bin\splunk.exe" set deploy-poll <Splunk_Server_IP>:8089
& "C:\Program Files\SplunkUniversalForwarder\bin\splunk.exe" add monitor "C:\Windows\System32\winevt\Logs\Security.evtx" -sourcetype "WinEventLog:Security"
& "C:\Program Files\SplunkUniversalForwarder\bin\splunk.exe" restart
```

---

## Exercises

### Exercise 1: Configuring Data Inputs in Splunk

**Steps:**

1. Log in to Splunk.
2. Navigate to **Settings > Data Inputs**.
3. Click **Add New** → Select **Forwarded Data**.
4. Configure the input to receive logs from the Universal Forwarder.

**Output:**
Splunk successfully receives and indexes logs from AD DS servers.

---

### Exercise 2: Creating a Dashboard for AD Logon Events

**Steps:**

1. Go to **Dashboards** → Click **Create New Dashboard**.
2. Add a new panel and select **Search** as the data source.
3. Use the search query to filter logon events:

```spl
sourcetype="WinEventLog:Security" EventCode=4624
```

4. Configure visualization and save the panel.

**Output:**
A dashboard panel displaying **AD logon events** is created.

---

### Exercise 3: Analyzing AD Security Events

**Steps:**

1. Create a new search in Splunk.
2. Use a search query to filter critical security events (e.g., failed logon attempts, account lockouts):

```spl
sourcetype="WinEventLog:Security" (EventCode=4625 OR EventCode=4740)
```

3. Save the search and add it to a dashboard.
4. Configure the panel to display relevant security metrics.

**Output:**
Panels showing **critical AD security events** are added to the dashboard.

---

### Exercise 4: Setting Up Alerts for AD Anomalies

**Steps:**

1. Create a search for anomalies (e.g., high number of failed logon attempts):

```spl
sourcetype="WinEventLog:Security" EventCode=4625 | stats count by User
```

2. Save the search → Select **Alert**.
3. Configure alert conditions and notification channels (email, Slack, etc.).
4. Save the alert.

**Output:**
Alerts are triggered to notify administrators of **AD anomalies** in real time.

---

### Exercise 5: Generating Reports on AD Activity

**Steps:**

1. Create a search for desired AD activity reports (e.g., user logon activity):

```spl
sourcetype="WinEventLog:Security" EventCode=4624 | stats count by User
```

2. Save the search → Select **Report**.
3. Configure report schedule and format.
4. Save the report.

**Output:**
Scheduled **AD activity reports** are generated regularly, providing ongoing insights into logon activity.

---

## Final Outcome

By completing this project, I implemented a **robust Active Directory monitoring and analytics system using Splunk**, enabling:

* Collection and analysis of AD logs in real time.
* Detection of anomalies and suspicious activities.
* Creation of dashboards, alerts, and scheduled reports for SOC operations and AD administration.
