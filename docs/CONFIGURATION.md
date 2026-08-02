# Wazuh SIEM Home Lab Configuration Guide

## Overview

This document describes the configuration performed to enable communication between the Wazuh Manager and the Windows Agent, as well as the configuration required for File Integrity Monitoring (FIM).

---

# Wazuh Manager Configuration

The Wazuh Manager was installed on an Ubuntu Server virtual machine using the official Wazuh installation script. After installation, the manager was configured to accept connections from Windows agents and process incoming security events.

Manager Responsibilities:

- Receive events from registered agents.
- Analyze logs using Wazuh detection rules.
- Generate security alerts.
- Store events in OpenSearch.
- Display alerts in the Wazuh Dashboard.

---

# Windows Agent Configuration

The Wazuh Agent was installed on a Windows 10 endpoint.

After installation, the following configuration was completed:

- Configured the Wazuh Manager IP address.
- Registered the Windows endpoint with the manager.
- Restarted the Wazuh Agent service.
- Verified that the agent appeared as **Active** in the Wazuh Dashboard.

---

# File Integrity Monitoring (FIM)

File Integrity Monitoring was enabled using the **Syscheck** module.

The following directory was added to the agent configuration file:

```xml
<directories realtime="yes">C:\Users\shree\Test</directories>
```

This configuration enables real-time monitoring of the specified directory.

The Wazuh Agent detects:

- File Creation
- File Modification
- File Deletion

---

# Agent Configuration File

Configuration File:

```text
C:\Program Files (x86)\ossec-agent\ossec.conf
```

The `ossec.conf` file is the primary configuration file for the Wazuh Agent.

It is used to configure:

- Manager IP Address
- Agent Registration
- File Integrity Monitoring (Syscheck)
- Windows Event Log Collection
- Communication Settings

---

# Network Configuration

The Ubuntu Server virtual machine was configured using **Bridged Adapter** networking to allow communication with the Windows endpoint.

Communication Details:

| Setting | Value |
|---------|-------|
| Protocol | TCP |
| Port | 1514 |
| Network Mode | Bridged Adapter |

---

# Configuration Verification

The following checks were performed after configuration:

- Wazuh Agent status was **Active**.
- Windows endpoint successfully connected to the Wazuh Manager.
- File Integrity Monitoring detected file creation events.
- File Integrity Monitoring detected file modification events.
- File Integrity Monitoring detected file deletion events.
- Alerts appeared successfully in the Wazuh Dashboard.

---

# Configuration Summary

The Wazuh SIEM Home Lab was successfully configured to:

- Collect Windows Event Logs.
- Monitor file integrity using Syscheck.
- Forward security events to the Wazuh Manager.
- Analyze events using Wazuh detection rules.
- Store events in OpenSearch.
- Display alerts through the Wazuh Dashboard.
