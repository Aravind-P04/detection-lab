# Detection Engineering Lab

Detection rules I use or have used in SOC work at Northern Trust. Splunk rules are SPL against the CIM Authentication datamodel. Sentinel rules are KQL against Azure AD SigninLogs. FP notes are from actual tuning. Not every rule is production-ready as-is — thresholds and field names 
will need adjusting for your environment.

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
Windows Event Logs · Azure AD Sign-in Logs · Palo Alto firewall logs
