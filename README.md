# Wazuh SOC Home Lab

A collaborative SOC lab project — building hands-on SIEM and detection 
engineering skills using Wazuh.

## About

This lab simulates a real-world SOC workflow. We built a Wazuh SIEM 
setup on cloud infrastructure and work together on simulating attacks, 
analyzing the resulting alerts, and refining detection logic.

**Team:**
- [thisismycv](https://github.com/thisismycv)
- Hira ([@albatross-280](https://github.com/albatross-280))

## Lab Overview

![wazuh-overview](./wazuh-overview.png)

## Tech Stack

- Wazuh (Manager + Indexer + Dashboard)
- Cloud-hosted environment
- Kali Linux (attack simulation)

## Use Cases

| Use Case | Status |
|---|---|
| [Content Discovery Scan Detection](./content-discovery-scan/content-discovery-scan.md) | ✅ Complete |
| [Vulnerability Assessment](./vulnerability-assessment/vulnerability-assessment.md) | ✅ Complete |
| [MITRE ATT&CK Correlation Analysis](./mitre-attack-mapping/mitre-attack-mapping.md) |✅ Complete|
| [Malicious File Detection (EICAR)](./malicious-file-detection/malicious-file-detection.md) | ✅ Complete |
| [File Integrity Monitoring — Activity Overview](./fim-activity-overview/fim-activity-overview.md) | ✅ Complete |
| [Webshell Access Attempt Detection](./webshell-access-attempt/webshell-access-attempt.md) | ✅ Complete |
## Goal

Building practical SOC analyst skills — detection logic, log analysis, 
and understanding attacker behavior from a defender's perspective.


# Wazuh Installation

## Connection to Wazuh Machine

Connect via SSH tunnel:

```bash
ssh -L 8443:<manager-internal-ip>:443 <username>@<manager-public-ip>
```

## Download Wazuh and Install

```bash
curl -sO https://packages.wazuh.com/4.9/wazuh-install.sh
sudo bash wazuh-install.sh -a
```

## Connect to Dashboard

```
https://localhost:8443
```

---

# VM-Web Agent Installation

## vm-web

```bash
wget https://packages.wazuh.com/4.x/apt/pool/main/w/wazuh-agent/wazuh-agent_4.9.2-1_amd64.deb && sudo WAZUH_MANAGER='10.0.2.4' WAZUH_AGENT_NAME='vm-web' dpkg -i ./wazuh-agent_4.9.2-1_amd64.deb
sudo systemctl daemon-reload
sudo systemctl enable wazuh-agent
sudo systemctl start wazuh-agent
`

