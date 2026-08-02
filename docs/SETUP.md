# Wazuh SIEM Home Lab Setup Guide

## Overview

This document explains how the Wazuh SIEM Home Lab was deployed using an Ubuntu Server virtual machine as the Wazuh Manager and a Windows 10 endpoint as the Wazuh Agent.

---

# Lab Environment

| Component | Details |
|----------|---------|
| SIEM Platform | Wazuh 4.12 |
| Manager OS | Ubuntu Server 24.04 LTS |
| Endpoint OS | Windows 10 |
| Virtualization | Oracle VirtualBox |
| Search Engine | OpenSearch |
| Dashboard | Wazuh Dashboard |
| Monitoring | File Integrity Monitoring (Syscheck) |

---

# Installation Steps

## Step 1 – Install Ubuntu Server

- Install Ubuntu Server 24.04 LTS in Oracle VirtualBox.
- Configure the network adapter in **Bridged Mode**.
- Update the operating system.

---

## Step 2 – Install Wazuh Manager

Run the official Wazuh installation script.

The installation automatically installs:

- Wazuh Manager
- OpenSearch
- Wazuh Dashboard

---

## Step 3 – Access the Dashboard

After installation, access the dashboard using:

```text
https://<Ubuntu-IP>
```

Accept the browser certificate warning and log in using the credentials generated during installation.

---

## Step 4 – Install the Windows Agent

Download and install the Wazuh Agent on the Windows 10 endpoint using the default installation options.

---

## Step 5 – Register the Agent

- Generate the agent key on the Wazuh Manager.
- Import the key into the Windows Agent.
- Configure the Manager IP address.
- Restart the Wazuh Agent service.

---

## Step 6 – Configure File Integrity Monitoring

Edit the agent configuration file:

```text
C:\Program Files (x86)\ossec-agent\ossec.conf
```

Add the monitored directory:

```xml
<directories realtime="yes">C:\Users\shree\Test</directories>
```

Restart the Wazuh Agent service.

---

## Step 7 – Verify the Deployment

Verify the following:

- Agent status is **Active**
- File Integrity Monitoring is enabled
- File creation events appear
- File modification events appear
- File deletion events appear

---

# Deployment Complete

The Wazuh SIEM Home Lab is now ready to monitor file integrity events and generate security alerts in real time.
