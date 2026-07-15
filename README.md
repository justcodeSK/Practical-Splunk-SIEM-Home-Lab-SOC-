# Enterprise SOC Home Lab with Splunk

## Detection Engineering and Incident Investigation Lab

This project is an enterprise-style SOC home lab built to practice real-world Security Operations Center workflows. The lab uses a lightweight 3-VM architecture designed for systems with limited resources, while still covering core SOC Analyst L1/L2 skills such as log collection, SIEM monitoring, endpoint visibility, attack simulation, alerting, incident investigation, and MITRE ATT&CK mapping.

The goal of this project is not only to install security tools, but to simulate how a real SOC collects telemetry, detects suspicious activity, investigates alerts, and documents incidents.

---

## Lab Overview

The lab is built using VirtualBox and consists of three virtual machines:

| Machine | Role | Purpose |
|---|---|---|
| Ubuntu Server | Splunk Enterprise SIEM + Linux log source | Collects, indexes, and analyzes logs |
| Windows 11 Endpoint | Monitored enterprise workstation | Generates Windows Event Logs and Sysmon telemetry |
| Kali Linux | Attacker simulation machine | Generates controlled attack activity for detection testing |

---

## Lab Architecture

```text
+-----------------------------+
| Kali Linux                  |
| Attacker / Test Machine     |
| Simulated Attack Activity   |
+-------------+---------------+
              |
              | Network scans, login attempts,
              | suspicious commands
              v
+-----------------------------+
| Windows 11 Endpoint         |
| Sysmon                      |
| Windows Event Logs          |
| Splunk Universal Forwarder  |
+-------------+---------------+
              |
              | Forwarded endpoint logs
              v
+-----------------------------+
| Ubuntu Server               |
| Splunk Enterprise           |
| Linux Syslog Source         |
| Detection & Investigation   |
+-----------------------------+
