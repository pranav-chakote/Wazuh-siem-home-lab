# Wazuh SIEM Home Lab Troubleshooting Guide

## Overview

This document summarizes the issues encountered during the deployment of the Wazuh SIEM Home Lab and the solutions used to resolve them.

---

# Issue 1 – Unable to Access the Wazuh Dashboard

## Problem

The Wazuh Dashboard could not be accessed from the Windows host. The browser displayed:

```
ERR_CONNECTION_TIMED_OUT
```

## Cause

The Ubuntu virtual machine was not reachable from the Windows host due to network configuration issues.

## Solution

- Verified that the Ubuntu virtual machine was running.
- Checked the IP address using:

```bash
ip addr
```

- Confirmed that the VirtualBox network adapter was configured in **Bridged Adapter** mode.
- Verified connectivity using the `ping` command from the Windows host.

---

# Issue 2 – Windows Agent Not Appearing in the Dashboard

## Problem

The Windows Agent did not appear under **Agents** in the Wazuh Dashboard.

## Cause

The agent was not properly registered with the Wazuh Manager or the manager IP address was incorrect.

## Solution

- Generated a new agent key using the `manage_agents` utility.
- Imported the key into the Windows Agent.
- Verified the manager IP address in the agent configuration.
- Restarted the Wazuh Agent service.

---

# Issue 3 – File Integrity Monitoring Not Detecting Changes

## Problem

Creating or modifying files did not generate alerts.

## Cause

The monitored directory was not configured in the `ossec.conf` file.

## Solution

Added the following configuration:

```xml
<directories realtime="yes">C:\Users\shree\Test</directories>
```

Saved the configuration and restarted the Wazuh Agent service.

---

# Issue 4 – Unable to Locate ossec.conf

## Problem

The expected configuration file could not be found.

## Cause

The file location differed from the expected path.

## Solution

Located the configuration file at:

```text
C:\Program Files (x86)\ossec-agent\ossec.conf
```

Edited the configuration and restarted the agent.

---

# Issue 5 – Agent Connection Failed

## Problem

The Windows Agent failed to communicate with the Wazuh Manager.

## Cause

Incorrect manager IP address or network connectivity issues.

## Solution

- Verified both systems were connected to the same Wi-Fi network.
- Confirmed communication using `ping`.
- Corrected the manager IP address.
- Restarted the Wazuh Agent.

---

# Issue 6 – Dashboard Accessible but No Alerts Displayed

## Problem

The dashboard opened successfully, but no File Integrity Monitoring alerts were visible.

## Cause

No monitored file events had occurred or the agent had not yet synchronized.

## Solution

- Created, modified, and deleted files in the monitored directory.
- Refreshed the dashboard.
- Confirmed alerts appeared after the agent processed the events.

---

# Lessons Learned

Throughout the project, several practical challenges were encountered and resolved. Troubleshooting these issues improved understanding of:

- Wazuh Agent registration
- VirtualBox networking
- Windows and Linux connectivity
- File Integrity Monitoring (Syscheck)
- Agent configuration using `ossec.conf`
- SIEM deployment and validation

---

# Conclusion

Successfully resolving these issues resulted in a fully operational Wazuh SIEM Home Lab capable of collecting Windows events, monitoring file integrity, generating security alerts, and displaying them through the Wazuh Dashboard.
