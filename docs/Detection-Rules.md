# Custom Detection Rules

## Overview

This document describes the custom Wazuh rules created to detect attacker activity captured by the Cowrie SSH honeypot.

The rules are designed to identify common attack techniques such as brute-force attempts, successful logins, command execution, and malware delivery.

---

# Detection Flow

```
Attacker
    │
    ▼
Cowrie Honeypot
    │
    ▼
JSON Event
    │
    ▼
Wazuh Agent
    │
    ▼
JSON Decoder
    │
    ▼
Custom Rule
    │
    ▼
Alert
```

---

# Rule Summary

| Rule ID | Event | Severity | MITRE ATT&CK | Description |
|----------|-------|---------:|--------------|-------------|
|100100|Base Event|0|-|Parent rule for all Cowrie events|
|100101|Session Connect|3|-|New SSH connection detected|
|100102|Client Version|2|-|SSH client version identified|
|100103|Client Fingerprint|2|-|SSH key exchange fingerprint captured|
|100104|Login Failed|6|T1110|Failed authentication attempt|
|100105|Login Success|10|T1078|Successful authentication to the honeypot|
|100106|Command Input|8|T1059|Command executed by the attacker|
|100107|Command Failed|5|-|Invalid command executed|
|100108|File Download|12|T1105|File downloaded from a remote source|
|100109|File Upload|12|T1105|File uploaded to the honeypot|
|100110|Session Closed|2|-|SSH session closed|
|100111|TTY Log Saved|3|-|Session recording stored successfully|

---

# Rule Details

## Rule 100100

**Purpose**

Acts as the parent rule for every Cowrie event.

This rule does not generate alerts and is only used to simplify rule inheritance.

---

## Rule 100101

**Event**

```
cowrie.session.connect
```

**Description**

Detects every new SSH connection received by the honeypot.

**Severity**

Low

---

## Rule 100102

**Event**

```
cowrie.client.version
```

**Description**

Captures the SSH client version used by the attacker.

---

## Rule 100103

**Event**

```
cowrie.client.kex
```

**Description**

Stores the SSH client fingerprint and supported cryptographic algorithms.

---

## Rule 100104

**Event**

```
cowrie.login.failed
```

**Description**

Detects failed SSH authentication attempts.

**MITRE ATT&CK**

T1110 – Brute Force

---

## Rule 100105

**Event**

```
cowrie.login.success
```

**Description**

Detects successful authentication into the honeypot.

**MITRE ATT&CK**

T1078 – Valid Accounts

---

## Rule 100106

**Event**

```
cowrie.command.input
```

**Description**

Detects commands executed by the attacker after authentication.

**MITRE ATT&CK**

T1059 – Command and Scripting Interpreter

---

## Rule 100107

**Event**

```
cowrie.command.failed
```

**Description**

Detects invalid or unsupported commands.

---

## Rule 100108

**Event**

```
cowrie.session.file_download
```

**Description**

Detects files downloaded from external sources.

**MITRE ATT&CK**

T1105 – Ingress Tool Transfer

---

## Rule 100109

**Event**

```
cowrie.session.file_upload
```

**Description**

Detects files uploaded by the attacker.

**MITRE ATT&CK**

T1105 – Ingress Tool Transfer

---

## Rule 100110

**Event**

```
cowrie.session.closed
```

**Description**

Indicates that the SSH session has ended.

---

## Rule 100111

**Event**

```
cowrie.log.closed
```

**Description**

Indicates that Cowrie successfully stored the complete TTY recording of the session.

---

# Future Rules

Additional detections may be implemented for:

- HTTP honeypot events
- Malware hash reputation
- IOC enrichment
- GeoIP enrichment
- Threat intelligence correlation
- Sigma rule conversion
