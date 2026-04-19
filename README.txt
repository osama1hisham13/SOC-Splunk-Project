# SOC Monitoring Project using Splunk

## Project Objective
This project simulates a real Security Operations Center (SOC) environment using Splunk SIEM.  
It focuses on detecting and analyzing common cyber attacks across multiple log sources.

---

## Key Goals
- Detect brute force attacks (T1110)
- Identify account compromise attempts (T1078)
- Detect web attacks such as SQL Injection (T1190)
- Detect data exfiltration patterns (T1041)
- Build security dashboards for real-time monitoring

---

## Tools & Data Sources
- Splunk Enterprise (SIEM)
- Windows Event Logs
- Linux Authentication Logs (Kali)
- Apache Web Server Logs

---

## System Architecture

This project simulates a centralized SIEM architecture using Splunk.

### Data Flow
1. Logs are generated from:
   - Linux systems (authentication logs)
   - Windows systems (Event Logs)
   - Apache Web Server (access logs)

2. Logs are collected using Splunk Forwarder and indexed in:
   - `index=project`

3. Data is processed in Splunk:
   - Field extraction (src_ip, user, url, status, bytes)
   - Normalization across multiple log sources

4. Detection layer:
   - SPL-based correlation searches
   - MITRE ATT&CK mapped detections

5. Visualization layer:
   - Security dashboards for monitoring and analysis

---

## Detection Rules (SPL Use Cases)

### Brute Force Detection
Multiple failed login attempts from the same IP.  
MITRE: T1110 (Brute Force)

### Account Compromise
Failed logins followed by successful login.  
MITRE: T1078 (Valid Accounts)

### Web Scanning
High number of unique URLs accessed by a single IP.  
MITRE: T1595 (Active Scanning)

### SQL Injection Detection
Detection of payloads such as OR 1=1, UNION SELECT.  
MITRE: T1190 (Exploit Public-Facing Application)

### Data Exfiltration
Unusually high outbound data volume from a single IP.  
MITRE: T1041 (Exfiltration Over Web Service)

---

## Dashboards

### Security Overview Dashboard
- Top Attackers
- Attack Distribution
- Activity Timeline

### Web Attack Monitoring Dashboard
- SQL Injection Attempts
- Web Scanning Detection
- Top Requested URLs
- Data Exfiltration Activity

### Failed Authentication Dashboard
- Failed Logins per IP
- Account Compromise Detection
- Failed Login Timeline
- Targeted Users

---

## Screenshots

### Security Overview
![Security Overview](dashboards/security_overview.png)

### Web Attacks
![Web Attacks](dashboards/web_attacks.png)

### Failed Authentication
![Failed Auth](dashboards/failed_auth.png)

---

## MITRE ATT&CK Mapping

| Detection Rule        | Tactic             | Technique |
|----------------------|--------------------|----------|
| Brute Force          | Credential Access  | T1110    |
| Account Compromise   | Initial Access     | T1078    |
| Web Scanning         | Reconnaissance     | T1595    |
| SQL Injection        | Initial Access     | T1190    |
| Data Exfiltration    | Exfiltration       | T1041    |

---

## Log Sources
- Windows Event Logs
- Linux Authentication Logs
- Apache Web Server Logs

Logs are ingested in real-time using Splunk Forwarder into `index=project`.

---

## Conclusion
This project demonstrates hands-on SOC analyst skills including:
log analysis, threat detection, correlation searches, dashboard creation, and MITRE ATT&CK mapping.

It simulates how a SOC team monitors, detects, and responds to cyber threats using Splunk SIEM.