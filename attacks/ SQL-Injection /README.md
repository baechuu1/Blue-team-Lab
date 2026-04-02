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
| 🌐 Apache | Reverse proxy and web log source |
| 📊 Splunk Enterprise | Log ingestion and analysis |
| 🌐 Host-Only Network | Isolated attack simulation |

### Logs Monitored
- `/var/log/apache2/juice_access.log`
- `/var/log/apache2/juice_error.log`

### Network Setup
- Host-only adapter (isolated lab environment)

---

⚔️ Attack Execution

The SQL injection attempt was simulated by sending malicious input through the Juice Shop search endpoint using a URL parameter.

Example request:

/rest/products/search?q=test' OR 1=1--

Because the payload was placed in a GET parameter instead of a POST body, the injected SQL pattern was visible in Apache access logs and searchable in Splunk.

📸 Attack Simulation

🔎 Key Observations
- A suspicious SQL-like pattern was observed in the q parameter of the search endpoint
- The request targeted /rest/products/search
- The request returned an HTTP 500 response, indicating backend processing was disrupted
- Apache access logs captured the request, source IP, method, URI, and response code
- Splunk successfully parsed the request fields, including clientip, uri, uri_query, and status
🔍 Detection in Splunk
🔐 Detect Requests to the Search Endpoint
spl```
index=lab "/rest/products/search"
| table _time clientip method uri status
```
🚨 Detect SQL Injection Patterns
spl```
index=lab "/rest/products/search"
| eval raw=lower(_raw)
| where like(raw,"%or 1=1%") OR like(raw,"%--%") OR like(raw,"%union%")
| table _time clientip method uri status
```
🔍 Decode the Query String for Visibility
spl```
index=lab "/rest/products/search"
| eval decoded=urldecode(uri_query)
| table _time clientip decoded status
```
📊 Identify Error Responses from Suspicious Requests
spl```
index=lab "/rest/products/search"
| eval raw=lower(_raw)
| where like(raw,"%or 1=1%") OR like(raw,"%--%")
| stats count by clientip, status, uri
```
📸 Splunk Detection

🧬 MITRE ATT&CK Mapping
- T1190 – Exploit Public-Facing Application
🛡️ Mitigation & Defense
- Use parameterized queries / prepared statements
- Validate and sanitize user input
- Restrict detailed database error messages returned to users
- Deploy a Web Application Firewall (WAF)
- Continuously monitor HTTP logs for suspicious query strings and abnormal response codes
- Apply least privilege to backend database accounts
💻 Detection Outcome

The SQL injection attempt generated a suspicious request pattern containing SQL keywords in a user-controlled parameter. The request triggered an HTTP 500 response, suggesting that malicious input reached backend application logic and caused abnormal processing.

By ingesting Apache access logs into Splunk, the attack was detectable through request pattern analysis, suspicious query parameters, and anomalous response codes.


⚠️ Disclaimer

This project is for educational purposes only. All activity was performed in a controlled lab environment using intentionally vulnerable systems owned by the researcher.

