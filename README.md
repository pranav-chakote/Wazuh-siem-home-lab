# 🛡️ Wazuh SIEM Home Lab with File Integrity Monitoring (FIM)
## 📐 Architecture Diagram

![Wazuh SIEM Home Lab Architecture](images/wazuh_siem_architecture%20(1).svg)
## 📌 Project Overview

This project demonstrates the deployment of a Wazuh SIEM environment using an Ubuntu Server as the Wazuh Manager and a Windows 10 endpoint as the Wazuh Agent.

The lab demonstrates centralized log collection, endpoint monitoring, and File Integrity Monitoring (FIM). Wazuh detects file creation, modification, and deletion events in real time and displays them on the Wazuh Dashboard for security monitoring.

---
## 🛠️ Technologies Used

| Component | Technology |
|-----------|------------|
| SIEM Platform | Wazuh 4.12 |
| Operating System | Ubuntu Server 24.04 LTS |
| Endpoint | Windows 10 Pro |
| Virtualization | Oracle VirtualBox |
| Log Collection | Wazuh Agent |
| File Integrity Monitoring | Syscheck |
| Search Engine | OpenSearch |
| Dashboard | Wazuh Dashboard |
| Network | Bridged Adapter |
| Protocol | TCP (Port 1514) |

---

## 🎯 Objectives

- Deploy Wazuh Manager on Ubuntu Server
- Install and configure the Wazuh Agent on Windows
- Register the Windows Agent with the Wazuh Manager
- Configure File Integrity Monitoring (Syscheck)
- Monitor file creation, modification, and deletion events
- Visualize security alerts in the Wazuh Dashboard
- Understand the architecture and workflow of a SIEM solution

  ---

## 🚀 Project Features

- ✅ Centralized log collection from Windows endpoint
- ✅ Windows Event Log monitoring
- ✅ File Integrity Monitoring (FIM) using Syscheck
- ✅ Real-time detection of file creation, modification, and deletion
- ✅ Security alerts displayed in the Wazuh Dashboard
- ✅ Endpoint registration and management
- ✅ SIEM architecture using Ubuntu Server and Windows Agent
- ✅ Real-time security monitoring through a web dashboard

---



# 🏗️ Project Architecture

This project consists of one Ubuntu Server acting as the Wazuh Manager and one Windows 10 endpoint running the Wazuh Agent.

The Windows endpoint sends logs and file integrity events to the Wazuh Manager over the local network. The manager analyzes the events, stores them in OpenSearch, and displays them through the Wazuh Dashboard.



### Architecture Overview

The Wazuh SIEM Home Lab consists of an Ubuntu Server running the Wazuh Manager and a Windows 10 endpoint running the Wazuh Agent. The Wazuh Agent continuously collects Windows Event Logs and File Integrity Monitoring (FIM) events using the Syscheck module. These events are securely transmitted to the Wazuh Manager over TCP port 1514, where they are analyzed using built-in detection rules. The processed events are stored in OpenSearch and visualized through the Wazuh Dashboard, allowing a SOC analyst to monitor and investigate security events in real time.

                

### Architecture Explanation

- **Windows 10 Endpoint** – Runs the Wazuh Agent and collects Windows Event Logs and File Integrity Monitoring (Syscheck) events.
- **TCP Port 1514** – Secure communication channel between the Wazuh Agent and Wazuh Manager.
- **Wazuh Manager (Ubuntu VM)** – Receives logs, analyzes events, applies detection rules, and generates alerts.
- **OpenSearch** – Stores indexed security events for fast searching.
- **Wazuh Dashboard** – Displays alerts, dashboards, and agent status.
- **SOC Analyst** – Monitors alerts and investigates security events.

  ---

# 🔄 Project Workflow

The following workflow illustrates how Wazuh detects and processes file integrity monitoring events in this home lab.

## Workflow

1. A user creates, modifies, or deletes a file inside the monitored folder (`C:\Users\shree\Test`).
2. The **Syscheck** module running on the Wazuh Agent detects the file system event in real time.
3. The Wazuh Agent securely forwards the event to the Wazuh Manager using **TCP Port 1514**.
4. The Wazuh Manager analyzes the received event using built-in detection rules.
5. The analyzed event is indexed and stored in **OpenSearch**.
6. The **Wazuh Dashboard** retrieves the indexed data and displays a security alert.
7. The **SOC Analyst** reviews the alert and investigates the detected activity.

### Workflow Summary

```text
User Action
      │
      ▼
Monitored Folder
      │
      ▼
Syscheck (FIM)
      │
      ▼
Wazuh Agent
      │
 TCP Port 1514
      │
      ▼
Wazuh Manager
      │
      ▼
Rule Engine
      │
      ▼
OpenSearch
      │
      ▼
Wazuh Dashboard
      │
      ▼
SOC Analyst
```
   ---

# 📂 Repository Structure

```text
Wazuh-siem-home-lab/
│
├── README.md
├── LICENSE
│
├── configuration/
│   └── Configuration files and documentation
│
├── docs/
│   └── Project documentation
│
├── images/
│   ├── architecture.svg
│   └── Project screenshots
│
├── installation/
│   └── Installation guides
│
└── scripts/
    └── Helper scripts (future improvements)
```

## Folder Description

| Folder | Description |
|---------|-------------|
| **configuration/** | Contains configuration-related documentation and important configuration files used in the project. |
| **docs/** | Contains detailed project documentation and supporting guides. |
| **images/** | Stores architecture diagrams, screenshots, and other visual assets used in the README. |
| **installation/** | Contains step-by-step installation documentation for setting up the Wazuh SIEM Home Lab. |
| **scripts/** | Reserved for automation scripts and helper utilities for future enhancements. |               

---

# 🖥️ Lab Environment

This project was implemented using an Ubuntu Server virtual machine running the Wazuh Manager and a Windows 10 host machine running the Wazuh Agent. The environment was configured to demonstrate centralized log collection, File Integrity Monitoring (FIM), and real-time security event visualization.

## Host Machine

| Component | Details |
|-----------|---------|
| Operating System | Windows 10 |
| Role | Wazuh Agent (Endpoint) |
| Monitored Folder | `C:\Users\shree\Test` |

---

## Virtual Machine

| Component | Details |
|-----------|---------|
| Virtualization Software | Oracle VirtualBox |
| Guest Operating System | Ubuntu Server 24.04 LTS |
| Role | Wazuh Manager |

---

## Wazuh Components

| Component | Purpose |
|-----------|---------|
| Wazuh Agent | Collects Windows Event Logs and File Integrity Monitoring (FIM) events |
| Wazuh Manager | Receives, analyzes, and correlates security events |
| OpenSearch | Stores indexed security events |
| Wazuh Dashboard | Visualizes alerts and agent information |

---

## Network Configuration

| Setting | Value |
|---------|-------|
| Network Mode | Bridged Adapter |
| Communication Protocol | TCP |
| Agent Communication Port | 1514 |
| Dashboard Access | HTTPS (Port 443) |

---

## File Integrity Monitoring Configuration

| Setting | Value |
|---------|-------|
| Monitoring Module | Syscheck |
| Monitoring Mode | Real-Time |
| Monitored Directory | `C:\Users\shree\Test` |
| Events Detected | File Creation, Modification, and Deletion |
