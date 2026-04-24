# SOC L1 Alert Reporting

## About This Room

> *Learn how to properly report, escalate, and communicate about high-risk SOC alerts.*

**Learning Objectives:**

- Understand the need for SOC alert reporting and escalation
- Learn how to write alert comments and case reports properly
- Explore escalation methods and communication best practices
- Apply the knowledge to triage alerts in a simulated environment

---

## Overview

---

## Key Concepts Covered

### Alert Flow

```
L1 receives alert (SIEM / EDR / Ticket platform)
        ↓
Triage: most closed as False Positive or handled at L1 level
        ↓
True Positives requiring action → Escalated to L2
        ↓
L2 remediates most breaches
        ↓
Critical incidents → DFIR / CIRT called in
```

### The Five Ws Report Format

Every alert comment or report should answer:

| W | Question | Example |
|---|---|---|
| **Who** | Which user, host, or system is involved? | `S.Conway` on `LPT-HR-009` |
| **What** | What action or event occurred? | Downloaded a double-extension `.mp4.exe` file via Chrome |
| **When** | When did the suspicious activity start? | 14:32 UTC on April 12 |
| **Where** | Which device, IP, or website was involved? | Source: `192.168.45.22`, Destination: `freecatvideoshd[.]monster` |
| **Why** | What is the reasoning for the verdict? | 48/70 VirusTotal detections, suspicious TLD, double extension |

### When to Escalate

- The alert indicates a major cyberattack requiring deeper investigation or DFIR
- Remediation actions are needed (malware removal, host isolation, password reset)
- Communication with external parties is required (customers, partners, law enforcement)
- You don't fully understand the alert and need senior support

### Escalation Steps

```
1. Move alert to **In Progress**
2. Conduct investigation and write your report
3. Set verdict (True Positive)
4. Reassign the alert to the L2 analyst on shift
5. Ping them in the corporate chat or in person
6. L2 will investigate further and initiate a formal Incident Response if needed.
```

### Edge Case Situations

| Situation | Correct Action |
|---|---|
| Critical alert but L2 is unavailable for 30+ minutes | Try calling L2 → then L3 → then the manager |
| Account compromise via Slack/Teams | Use phone or alternative method |
| Sudden flood of critical alerts | Prioritise accordingly, but inform L2 on shift immediately |
| You realise days later that you misclassified an alert | Immediately inform L2 - threat actors can be dormant for weeks before impact |
| Logs not parsed correctly | Investigate what you can and report the technical issue to L2 or an engineer |


---

## Scenario

---

## Skills Demonstrated
