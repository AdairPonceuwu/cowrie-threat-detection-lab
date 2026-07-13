# 🐝 Cowrie Threat Detection Lab

> A Detection Engineering lab that integrates the Cowrie SSH/Telnet Honeypot with Wazuh SIEM to detect, analyze, and visualize real-world attacks using custom detection rules, Sigma rules, and MITRE ATT&CK mapping.

![Status](https://img.shields.io/badge/status-In%20Progress-yellow)
![Platform](https://img.shields.io/badge/platform-Ubuntu%20Server-E95420)
![SIEM](https://img.shields.io/badge/SIEM-Wazuh-blue)
![Language](https://img.shields.io/badge/Python-3.x-blue)
![License](https://img.shields.io/badge/license-MIT-green)

---

# 📖 Overview

This project demonstrates the implementation of a **Detection Engineering Lab** using the Cowrie SSH/Telnet Honeypot integrated with **Wazuh SIEM**.

The objective is to simulate real-world attacks against a honeypot, collect telemetry, generate alerts, develop custom detection rules, write Sigma rules, and map detections to the MITRE ATT&CK Framework.

Rather than focusing only on deploying a honeypot, this project emphasizes the complete detection lifecycle:

- Attack Simulation
- Log Collection
- Detection Engineering
- Alerting
- Threat Analysis
- Dashboard Visualization
- MITRE ATT&CK Mapping

---

# 🎯 Objectives

- Deploy a Cowrie SSH/Telnet Honeypot
- Integrate Cowrie logs with Wazuh SIEM
- Develop custom Wazuh decoders
- Create custom Wazuh detection rules
- Develop Sigma detection rules
- Map detections to MITRE ATT&CK
- Build dashboards for attack visualization
- Document attack scenarios and detections

---

# 🏗️ Architecture

```
                    Internet
                        │
                 SSH Attackers
                        │
                Cowrie Honeypot
                        │
             JSON / Event Logs
                        │
                 Wazuh Agent
                        │
                 Wazuh Manager
                        │
             Wazuh Dashboard
                        │
      Dashboards • Alerts • Sigma Rules
```

---

# 🧰 Technologies

| Technology | Purpose |
|------------|---------|
| Wazuh | SIEM Platform |
| Cowrie | SSH/Telnet Honeypot |
| Ubuntu Server | Honeypot Host |
| Python | Cowrie Runtime |
| Sigma | Detection Rules |
| MITRE ATT&CK | Threat Mapping |
| Linux | Operating System |

---

# 📂 Repository Structure

```
cowrie-threat-detection-lab/
│
├── architecture/
│   └── diagrams
│
├── attack-scenarios/
│   ├── brute-force.md
│   ├── reconnaissance.md
│   ├── malware-download.md
│   └── persistence.md
│
├── dashboards/
│
├── decoders/
│
├── docs/
│
├── images/
│
├── rules/
│
├── scripts/
│
├── sigma/
│
└── README.md
```

---

# 🚀 Project Roadmap

- [x] Deploy Wazuh SIEM
- [x] Configure Ubuntu Server
- [x] Register Ubuntu as Wazuh Agent
- [ ] Install Cowrie
- [ ] Configure Cowrie
- [ ] Integrate Cowrie with Wazuh
- [ ] Create custom Wazuh decoders
- [ ] Develop Wazuh detection rules
- [ ] Create Sigma detection rules
- [ ] Build security dashboards
- [ ] Map detections to MITRE ATT&CK
- [ ] Document attack scenarios

---

# 📊 Planned Dashboards

- Top Attacking IPs
- Countries of Origin
- Failed Login Attempts
- Successful Logins
- Most Executed Commands
- Downloaded Files
- MITRE ATT&CK Techniques
- Attack Timeline

---

# 🔍 Detection Scenarios

This lab will include detections for:

- SSH Brute Force
- Successful SSH Login
- System Reconnaissance
- Credential Enumeration
- Malware Download
- Persistence Attempts
- Reverse Shell Activity
- File Downloads
- Suspicious Command Execution

---

# 🎯 MITRE ATT&CK Coverage

| Technique | Description |
|-----------|-------------|
| T1110 | Brute Force |
| T1059 | Command and Scripting Interpreter |
| T1082 | System Information Discovery |
| T1083 | File and Directory Discovery |
| T1005 | Data from Local System |
| T1105 | Ingress Tool Transfer |
| T1070 | Indicator Removal on Host |

---

# 📸 Screenshots

*Coming soon...*

---

# 📚 References

- Cowrie Documentation
- Wazuh Documentation
- Sigma Project
- MITRE ATT&CK Framework

---

# 👨‍💻 Author

**Adair Ponce Luna**

Cybersecurity | SOC | Detection Engineering | Blue Team

---

# ⭐ Future Improvements

- Integrate Suricata
- Add Sysmon endpoint telemetry
- Deploy Windows endpoint
- Create automated attack simulations
- Implement Threat Hunting use cases
- Expand Sigma detection coverage
