# SOC Lab Architecture

## Overview

This project demonstrates a Security Operations Center (SOC) lab built using Wazuh SIEM and the Cowrie SSH honeypot.

The objective is to simulate real-world attacker activity, collect telemetry, detect malicious behavior using custom detection rules, and visualize alerts within the Wazuh Dashboard.

---

## Components

### Wazuh Server

Responsible for:

- Event analysis
- Rule matching
- Alert generation
- Dashboard visualization

---

### Wazuh Agent

Installed on the Ubuntu server hosting Cowrie.

Responsibilities:

- Collect Cowrie JSON logs
- Forward events to the Wazuh Manager
- Monitor local system events

---

### Cowrie Honeypot

Cowrie emulates an SSH server that records attacker activity.

Captured events include:

- SSH connections
- Login attempts
- Executed commands
- File downloads
- File uploads
- Session metadata

---

## Event Flow

Windows Attacker
        │
        ▼
SSH Connection
        │
        ▼
Cowrie Honeypot
        │
JSON Event
        │
        ▼
Wazuh Agent
        │
        ▼
Wazuh Manager
        │
Decoder
        │
Custom Rules
        │
        ▼
Alert
        │
        ▼
Dashboard

---

## Technologies

- Wazuh 4.14.6
- Cowrie Honeypot
- Ubuntu Server 26.04 LTS
- Windows 11
- VirtualBox
- JSON
- SSH
- MITRE ATT&CK

---

## Detection Workflow

1. Attacker connects through SSH.
2. Cowrie generates a JSON event.
3. Wazuh Agent monitors the log file.
4. Event is sent to the Wazuh Manager.
5. JSON decoder parses the event.
6. Custom detection rules evaluate the event.
7. Alert appears in the Wazuh Dashboard.
