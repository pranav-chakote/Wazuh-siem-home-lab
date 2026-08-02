# Wazuh SIEM Home Lab Testing Guide

## Overview

This document describes the testing process used to validate the Wazuh SIEM Home Lab. The objective was to verify that the Wazuh Agent correctly detects file system changes, forwards events to the Wazuh Manager, and generates alerts in the Wazuh Dashboard.

---

# Test Environment

| Component | Details |
|-----------|---------|
| Manager | Ubuntu Server 24.04 LTS |
| Agent | Windows 10 |
| SIEM Platform | Wazuh 4.12 |
| Monitoring Module | Syscheck (File Integrity Monitoring) |
| Monitored Folder | `C:\Users\shree\Test` |

---

# Test Case 1 – Agent Registration

### Objective

Verify that the Windows Agent successfully connects to the Wazuh Manager.

### Steps

1. Start the Wazuh Agent service.
2. Open the Wazuh Dashboard.
3. Navigate to **Agents**.
4. Verify that the Windows Agent appears with the status **Active**.

### Expected Result

The Windows Agent should be connected and displayed as **Active**.

### Actual Result

The Windows Agent successfully connected to the Wazuh Manager and appeared as **Active** in the dashboard.

📷 Screenshot:
`images/agent-active.png`

---

# Test Case 2 – File Creation Detection

### Objective

Verify that Wazuh detects the creation of a new file.

### Steps

1. Open the monitored folder (`C:\Users\shree\Test`).
2. Create a new text file.
3. Wait a few seconds.
4. Refresh the Wazuh Dashboard.

### Expected Result

A File Integrity Monitoring alert should be generated.

### Actual Result

The Wazuh Agent detected the new file and generated a File Integrity Monitoring alert.

📷 Screenshot:
`images/file-created.png`

---

# Test Case 3 – File Modification Detection

### Objective

Verify that Wazuh detects modifications to an existing file.

### Steps

1. Open an existing file in the monitored folder.
2. Modify the file contents.
3. Save the file.
4. Refresh the Wazuh Dashboard.

### Expected Result

A File Integrity Monitoring alert should be generated for the modified file.

### Actual Result

The modification was successfully detected, and an alert was displayed in the dashboard.

📷 Screenshot:
`images/file-modified.png`

---

# Test Case 4 – File Deletion Detection

### Objective

Verify that Wazuh detects deletion of monitored files.

### Steps

1. Delete a file from the monitored folder.
2. Wait a few seconds.
3. Refresh the Wazuh Dashboard.

### Expected Result

A File Integrity Monitoring alert should be generated for the deleted file.

### Actual Result

The file deletion was successfully detected and reported by the Wazuh Manager.

📷 Screenshot:
`images/file-deleted.png`

---

# Test Summary

| Test Case | Status |
|-----------|--------|
| Agent Registration | ✅ Passed |
| File Creation Detection | ✅ Passed |
| File Modification Detection | ✅ Passed |
| File Deletion Detection | ✅ Passed |

---

# Conclusion

The Wazuh SIEM Home Lab was successfully tested. All File Integrity Monitoring (FIM) events were detected by the Wazuh Agent, transmitted to the Wazuh Manager, analyzed, and displayed in the Wazuh Dashboard. The successful execution of these tests confirms that the SIEM environment is functioning as expected.
