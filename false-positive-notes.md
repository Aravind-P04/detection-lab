# False Positive Tuning Notes

## T1078 — Valid Accounts (impossible travel / multi-IP login)

**Common triggers:**
- Users on split-tunnel VPN appear with both corporate and home IP simultaneously
- Mobile hotspot users switching networks mid-session
- Shared service accounts accessed from multiple hosts

**Tuning:**
- Whitelist known VPN egress IPs from the detection
- Add exclusion for service account naming conventions (svc_*, sa_*)
- Raise mvcount threshold to 3+ in noisy environments
- Scope to high-value accounts first (admins, finance, executives)

---

## T1110 — Brute Force (failed authentication threshold)

**Common triggers:**
- Legacy applications using basic auth with expired or cached credentials
- Automated monitoring tools with misconfigured service account passwords
- Password sync failures during Active Directory migrations

**Tuning:**
- Exclude known monitoring and automation tool IPs
- Focus on ResultType codes 50126, 50053, 50055 (invalid credentials)
- Build separate alert for internal vs external source IPs — different risk levels
- Combine with successful login after failures for higher-confidence alert

---

## T1562 — Impair Defenses (security tool disabled)

**Common triggers:**
- Legitimate IT admin disabling AV temporarily for software installs
- Patch management systems stopping services during updates
- Security tool upgrades causing momentary service stops

**Tuning:**
- Correlate with change management window schedule
- Whitelist known admin accounts performing routine maintenance
- Alert only when combined with other suspicious activity in same timeframe

---

## T1021 — Remote Services (lateral movement via SMB)

**Common triggers:**
- IT helpdesk remote access to endpoints
- Legitimate file share access between workstations
- Domain controller replication traffic

**Tuning:**
- Baseline normal SMB traffic patterns per user and host
- Focus on first-time connections between hosts with no prior history
- Alert on admin share access (C$, ADMIN$) from non-admin accounts

---

## T1059 — Command Interpreter (suspicious PowerShell)

**Common triggers:**
- IT automation scripts running on schedule
- Software deployment tools (SCCM, Intune) executing PowerShell
- Developer workstations running legitimate scripts

**Tuning:**
- Whitelist known script paths and signed scripts
- Focus on encoded commands (-EncodedCommand flag)
- Alert on PowerShell spawned by Office applications or browsers
- Use parent process context — powershell.exe spawned by winword.exe is high confidence
