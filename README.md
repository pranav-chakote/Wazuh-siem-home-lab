# 🛡️ Wazuh SIEM Home Lab with File Integrity Monitoring (FIM)

## 📌 Project Overview

This project demonstrates the deployment of a Wazuh SIEM environment using an Ubuntu Server as the Wazuh Manager and a Windows 10 endpoint as the Wazuh Agent.

The lab demonstrates centralized log collection, endpoint monitoring, and File Integrity Monitoring (FIM). Wazuh detects file creation, modification, and deletion events in real time and displays them on the Wazuh Dashboard for security monitoring.

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
