# SOC L1 Alert Triage

## About This Room

> *Learn more about SOC alerts and build a systematic approach to efficiently triaging them.*

**Learning Objectives:**
- Familiarise with the concept of SOC alerts
- Explore alert fields, statuses, and classifications
- Learn how to perform alert triage as an L1 analyst
- Practice with real alerts and SOC workflows

---

## Overview

This room simulated a real SOC alert triage. The scenario involved monitoring a SIEM dashboard, determining prioritisation logic, distinguishing True Positives from False Positive and assigning the status of alerts.

---

## Key Concepts Covered

### Event Flow
```
Event occurs (login, file download, process launch)
        ↓
System logs the event
        ↓
Logs shipped to SIEM or EDR
        ↓
Detection rule matches → Alert generated
        ↓
L1 analyst triages the alert     
```

### Alert Properties

- **Alert Time** - When the alert was created
- **Alert Name** - Summary of what happened based on the detection rule name 
- **Alert Severity** - Urgency level set by detection engineers 
- **Alert Status** - Whether the alert is being worked on 
- **Alert Verdict** - Whether the alert is a real threat or noise 
- **Alert Assignee** - The analyst who owns and is responsible for the alert 
- **Alert Description** - Rule logic, why it may indicate an attack, how to triage 
- **Alert Fields** - The specific values that triggered the rule

### Alert Prioritisation Rules

1. **Filter** - Take New/unassigned alerts not being worked on by another analyst
2. **Sort by severity** - Critical first, then High, Medium, Low
3. **Sort by time** - Within the same severity, take the oldest alert first

> The reasoning: a critical alert from 2 hours ago represents a threat actor who has had 2 hours of undetected access. The newer one has just started.

### Alert Triage Workflow

```
1. Assign the alert to yourself
2. Move status to In Progress
3. Familiarise with alert name, description and key fields
4. Investigate:
   - Who is affected (user, host, IP, cloud resource)?
   - What action occurred (login, file creation, process launch)?
   - Review surrounding events before and after the alert
   - Use threat intelligence to verify suspicious indicators
5. Determine verdict: True Positive or False Positive
6. Write a detailed analyst comment with your reasoning
7. Move status to Closed
```

---

## Scenario

The dashboard contained 5 alerts. I triaged the top 3 by priority:

<p align="center">
  <img src="alert-dashboard.png">
</p>

---

## Alert 1 - Potential Data Exfiltration

| Field | Value |
|---|---|
| **Severity** | Critical |
| **Description:** | This rule detects 5 or more gigabytes of data sent from a single device to a single destination within a day, which may indicate data exfiltration to untrusted location. |
| **Destination** | *.zoom.us |
| **Source IP** | 192.168.45.66 |
| **Source Network** | UK04/MEETINGROOM |
| **Sent Data** | 5.8 GB |
| **Received Data** | 5.2 GB |
| **Verdict** | False Positive |

**Analysis:** 

---

## Alert 2 - Double-Extension File Creation

| Field | Value |
|---|---|
| **Severity** | High |
| **Description** | This rule detects a creation of a double-extension file like '*.pdf.exe' or '*.gif.lnk', often used by hackers in phishing attacks to trick users into opening the malicious executable. |
| **Host** | LPT-HR-009 |
| **Process Name** | chrome.exe |
| **Process User** | S.Conway |
| **Target File** | C:\Users\S.Conway\Downloads\cats2025.mp4.exe |
| **Source URL** | https://freecatvideoshd[.]monster/cats2025[.]mp4[.]exe |
| **File MD5** | 14d8486f3f63875ef93cfd240c5dc10b |
| **VirusTotal** | 48/70 detections |
| **Verdict** | True Positive |

**Analysis:**  


<p align="center">
  <img src="virustotal-cats2025.png">
</p>

---

## Alert 3 - Download from GitHub Repository

| Field | Value |
|---|---|
| **Severity** | Low |
| **Description** | This rule detects any download from GitHub. While GitHub stores lots of great projects that our IT team uses, it also stores malicious scripts and exploits that must not be downloaded by the users. |
| **Accessed URL** | https://github.com/facebook/react |
| **Source User** | G.Chandler |
| **Source Host** | LPT-IT-063 |
| **Source Network** | VPN/DEVELOPERS |
| **Verdict** | False Positive |

**Analysis:**  

---

## Skills Demonstrated

- Alert prioritisation by severity and age
- True Positive vs False Positive determination
- IOC enrichment (VirusTotal hash lookup)
- Contextual analysis (network segment, user role, traffic ratios)
- Writing concise, structured analyst comments 

