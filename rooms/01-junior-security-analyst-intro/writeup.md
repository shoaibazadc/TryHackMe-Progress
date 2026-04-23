# Junior Security Analyst Intro

## Overview

This room simulated one of the day-to-day responsibilities of a Tier 1 SOC Analyst. The scenario involved monitoring a SIEM dashboard, identifying suspicious alerts, performing OSINT on malicious IPs and escalating alerts to a senior analyst.

---

## Key Concepts Covered

### Daily Duties of a Junior Security Analyst

- Monitoring and investigating security alerts
- Participating in brainstorms and workshops
- Cooperating with other teams to keep the company safe
- Continuously learning about new attacks and defences

---

## Scenario

### Alert Triage

Opened the alert dashboard. Two critical alerts, both originating from the same external IP:

| Alert | Detail |
|---|---|
| Alert 1 | Unauthorized login attempts from IP address `221.181.185.159` to port 22 |
| Alert 2 | Successful SSH login from the suspicious IP address `221.181.185.159` |

> **Suspicious IP:** `221.181.185.159`

### OSINT - IP Lookup

Searched the IP in the threat intelligence platform available in the lab to confirm its reputation.

<p align="center">
  <img src="ip-hunter-results.png">
</p>

### Actions Taken

1. Identified the IP as **malicious** based on threat intel
2. Escalated to SOC Team Lead **Will Griffin** with the IP and context
3. Blocked the IP at the firewall level
4. Documented verdict: *Brute-forced SSH*

---

## Skills Demonstrated

- Alert monitoring from a SOC dashboard
- IP reputation lookup using threat intelligence tools
- Escalation procedure to senior analyst
- Documenting findings and applying defensive action

