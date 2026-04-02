# 💉 SQL Injection Detection Lab

## 📌 Overview
A SQL Injection attack targets web applications by submitting malicious or abnormal input into user-controlled fields, such as login forms or search boxes, in an attempt to manipulate backend SQL queries.

This technique can be used to bypass authentication, retrieve unauthorized data, or interfere with application behavior. In this lab, a vulnerable web application was deployed and monitored through Apache access logs, which were then ingested into Splunk for detection and analysis.

---

## 🧪 Lab Environment

| Component | Description |
|----------|-------------|
| 🐉 Kali Linux | Attacker machine |
| 🐧 Ubuntu Server | Target system |
| 🌐 OWASP Juice Shop | Vulnerable web application |
| 📊 Splunk Enterprise | Log ingestion and analysis |
| 🌐 Host-Only Network | Isolated attack simulation |

### Logs Monitored
- `/var/log/apache2/juice_access.log`
- `/var/log/apache2/juice_error.log`

### Network Setup
- Host-only adapter (isolated lab environment)

---

## ⚙️ Lab Setup

### 1. Run OWASP Juice Shop in Docker
```bash
docker run -d --name juice-shop -p 3000:3000 bkimminich/juice-shop
