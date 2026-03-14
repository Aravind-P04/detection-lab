# Detection Engineering Lab

Splunk and Microsoft Sentinel detection rules mapped to the MITRE ATT&CK framework.
Built from real SOC experience — each rule includes detection logic, the attack
technique it covers, and tuning notes to reduce false positives.

## Rules covered

| Rule | MITRE Technique | Tactic | Platform |
|---|---|---|---|
| Impossible travel login | T1078 — Valid Accounts | Initial Access | Splunk, Sentinel |
| Brute force threshold | T1110 — Brute Force | Credential Access | Splunk, Sentinel |
| Security tool disabled | T1562 — Impair Defenses | Defense Evasion | Splunk |
| Lateral movement via SMB | T1021 — Remote Services | Lateral Movement | Splunk |
| Suspicious PowerShell | T1059 — Command Interpreter | Execution | Sentinel |

## Structure
- `/rules/splunk/` — Splunk SPL queries
- `/rules/sentinel/` — KQL queries for Microsoft Sentinel
- `mitre-mapping.md` — full technique to tactic mapping
- `false-positive-notes.md` — tuning guidance per rule

## Environment
Tested against: Windows Event Logs, Azure AD Sign-in Logs, Palo Alto firewall logs
