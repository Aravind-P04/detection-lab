# MITRE ATT&CK Mapping

| File | Technique ID | Technique Name | Tactic | Data Source |
|---|---|---|---|---|
| rules/splunk/T1078-valid-accounts.spl | T1078 | Valid Accounts | Initial Access, Persistence | Authentication logs |
| rules/sentinel/T1110-brute-force.kql | T1110 | Brute Force | Credential Access | Azure AD Sign-in Logs |
| rules/splunk/T1562-defense-evasion.spl | T1562 | Impair Defenses | Defense Evasion | Windows Event Logs |
| rules/splunk/T1021-lateral-movement.spl | T1021 | Remote Services | Lateral Movement | Network, Auth logs |
| rules/sentinel/T1059-powershell.kql | T1059 | Command Interpreter | Execution | Endpoint logs |

## References
- [MITRE ATT&CK Framework](https://attack.mitre.org/)
- [Splunk Security Essentials](https://splunkbase.splunk.com/app/3435)
- [Microsoft Sentinel Analytics Rules](https://learn.microsoft.com/en-us/azure/sentinel/detect-threats-built-in)
