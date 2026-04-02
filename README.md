###🛡️ Blue Team Detection Lab


##📊 Project Highlights

- 🔍 SIEM Analysis with Splunk
- 🧠 Threat Detection & Investigation
- 📂 Log Analysis (Linux)
- 🧬 MITRE ATT&CK Mapping
- ⚔️ Attack Simulation (Red → Blue perspective)

##📌 Overview

This project is a hands-on Blue Team lab designed to simulate real-world cyber attacks and demonstrate detection and analysis using Splunk Enterprise.

Each attack scenario follows a structured workflow:

- ⚔️ Attack Execution  
- 📥 Log Collection  
- 🔍 Detection in Splunk  
- 🧬 MITRE ATT&CK Mapping  
- 🛡️ Mitigation & Defense

---

## 🧪 Lab Environment

| Component        | Description                |
|------------------|---------------------------|
| 🐉 Kali Linux    | Attacker machine          |
| 🐧 Ubuntu Server | Target system             |
| 📊 Splunk SIEM   | Log ingestion & analysis  |
| 🌐 Host-Only Network | Isolated attack simulation |


## ⚔️ Attack Scenarios

| Attack | Description | Status |
|--------|------------|--------|
| 🔐 SSH Brute Force | Credential attack using Hydra | ✅ Completed |
| 💉 SQL Injection | Web application exploitation | 🔄 In Progress |
| 🎯 Password Spraying | Low-and-slow authentication attack | ⏳ Planned |
| 🔁 Lateral Movement | Internal pivoting between systems | ⏳ Planned |
| 🧩 Persistence | Maintaining access | ⏳ Planned |
| 📡 Beaconing | Simulated command & control traffic | ⏳ Planned |

📂 Project Structure

```
blue-team-lab/
│
├── attacks/
│ ├── brute-force-ssh/
│ ├── sql-injection/
│ ├── password-spraying/
│ ├── lateral-movement/
│ ├── persistence/
│ └── beaconing/
│
└── README.md
```

##🎯 Objective

Build a practical understanding of how cyber attacks are executed and how defenders detect, analyze, and respond using SIEM tools.

##🧠 Key Concepts Demonstrated
Authentication attack detection
Log correlation and analysis
Identifying Indicators of Compromise (IOCs)
Post-compromise investigation
Real-world SOC workflows

##🚀 Roadmap

SSH Brute Force Detection

SQL Injection Detection

Password Spraying Detection

Lateral Movement Simulation

Persistence Techniques Detection

Beaconing / C2 Detection

##⚠️ Disclaimer

This project is for educational purposes only.
All attacks are performed in a controlled lab environment.
