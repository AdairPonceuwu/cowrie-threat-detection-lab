# MITRE ATT&CK Mapping

## Overview

This document maps the custom Cowrie detection rules to the MITRE ATT&CK framework.

The purpose of this mapping is to demonstrate how attacker behavior observed inside the Cowrie honeypot aligns with known adversary techniques.

---

# ATT&CK Coverage

| Rule ID | Cowrie Event | ATT&CK Tactic | ATT&CK Technique |
|----------|--------------|---------------|------------------|
|100104|cowrie.login.failed|Credential Access|T1110 - Brute Force|
|100105|cowrie.login.success|Initial Access|T1078 - Valid Accounts|
|100106|cowrie.command.input|Execution|T1059 - Command and Scripting Interpreter|
|100108|cowrie.session.file_download|Command and Control|T1105 - Ingress Tool Transfer|
|100109|cowrie.session.file_upload|Command and Control|T1105 - Ingress Tool Transfer|

---

# Detection Matrix

| Tactic | Coverage |
|---------|----------|
|Initial Access|✔|
|Execution|✔|
|Persistence|Planned|
|Privilege Escalation|Planned|
|Defense Evasion|Planned|
|Credential Access|✔|
|Discovery|Future Enhancement|
|Lateral Movement|Future Enhancement|
|Collection|Future Enhancement|
|Command and Control|✔|
|Exfiltration|Future Enhancement|
|Impact|Future Enhancement|

---

# Current Detection Scope

The current implementation focuses on SSH-based attacks captured by the Cowrie honeypot.

The following attacker actions are detected:

- SSH connection attempts
- Failed authentication
- Successful authentication
- Command execution
- File downloads
- File uploads
- Session lifecycle events

---

# Planned Improvements

Future versions of this project will include:

- Detection of reconnaissance commands
- Malware hash reputation checks
- Threat Intelligence enrichment
- GeoIP enrichment
- Sigma rule integration
- Multi-stage attack correlation
- Detection of persistence techniques
- Detection of privilege escalation attempts

---

# ATT&CK Navigator

The techniques implemented in this project can be imported into MITRE ATT&CK Navigator for visualization.

Current techniques:

- T1078
- T1110
- T1059
- T1105
