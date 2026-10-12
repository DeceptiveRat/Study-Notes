Nice — let’s dig into a SOC analyst’s day-to-day, step-by-step, and show exactly *how* MITRE ATT\&CK becomes a working tool for triage, investigation, hunting, and reporting. I’ll give practical templates you can copy into a SIEM ticket or playbook, a triage checklist, examples of mapping alerts to ATT\&CK techniques, and recommended metrics and behaviors.

# 1) Mental model — what ATT\&CK gives the analyst

* **Common language**: when you say “T1059.001 (PowerShell)” everyone knows what behavior you mean.
* **Context for intent**: ATT\&CK’s tactics (Initial Access → Execution → Persistence → etc.) help you understand *why* the adversary did X, not just *what* happened.
* **Investigation roadmap**: techniques suggest likely follow-ups (if you see PowerShell execution, check process parents, network callbacks, modules loaded, credential access attempts).

# 2) Day-in-the-life flow (high level)

1. **Alert ingestion** — SIEM/EDR surfaces an alert.
2. **Initial triage** — use a checklist to decide escalate/contain/close. Tag the alert with an ATT\&CK technique ID (or multiple IDs).
3. **Enrichment** — pull host/identity/geo/network/contextual data. Add it to the case.
4. **Investigation** — pivot from evidence: processes, command lines, file system artifacts, network connections, logs. Map findings to ATT\&CK tactics to infer next steps.
5. **Containment & remediation** — follow playbook mapped to technique(s). Document actions with ATT\&CK IDs.
6. **Hunt & follow-up** — hunt for similar indicators across estate; update detections and rules.
7. **Reporting** — produce a concise report that references ATT\&CK techniques and coverage gaps.

# 3) Practical triage checklist (use this on every alert)

Put this at the top of your case/ticket and answer quickly:

1. **Alert summary** — one-line (what, where, when).
2. **Severity** — Low / Medium / High (use org criteria).
3. **ATT\&CK mapping** — technique(s) and tactic(s) (e.g., T1059.001 — Execution: PowerShell).
4. **Observable evidence present** — process, cmdline, file hash, IP, user.
5. **Is it known/expected?** — legitimate admin activity, patching, scheduled task? (Y/N + proof)
6. **Scope** — single host / user / multiple?
7. **Initial action** — contain (isolate host), credential reset, block IP, monitor only.
8. **Escalate?** — Yes if: domain admin affected, exfiltration suspected, persistent access.
9. **Owner & SLA** — assigned analyst, expected due times.

# 4) What to collect during enrichment (fields you must fetch)

* Host: hostname, OS, IP, MAC, EDR sensor version, last user, uptime.
* Process: parent PID/name, full command line, start/stop timestamps, file path, signature.
* Network: remote IP/port, domain, TLS cert validation, DNS queries, proxy logs.
* Identity: logged-on user, kerberos/NTLM events, recent privileged escalations.
* Artifacts: file hashes, created/mutated files, scheduled tasks, services, registry keys.
* Context: business owner, asset criticality, patch level, known maintenance windows.

# 5) Investigation pivots mapped to ATT\&CK (how ATT\&CK informs what you look for)

Example 1 — **Alert**: EDR flags suspicious PowerShell execution. Tag: **T1059.001 (PowerShell)**.

* Pivot checklist:

  * Parent process: what launched PowerShell? (explore for signed scripts run by explorer.exe vs svchost.exe)
  * Command line: encodedCommand, -nop, -w hidden, downloadstring, IEX.
  * Network: did PS spawn an outbound HTTP/HTTPS callback? check proxy and EDR network flows.
  * Persistence: scheduled tasks, services, startup registry keys.
  * Lateral movement: are creds being used from this host? check event logs for lateral logons (T1021).
  * Artifact collection: extract PowerShell command, save to evidence storage, compute hash.

Example 2 — **Alert**: Unusual lsass.exe handle access flagged. Tag: **T1003 (Credential Dumping)**.

* Pivot checklist:

  * Process accessing lsass: which PID and user?
  * Dump write artifacts: .dmp files, procdump, mimikatz execution.
  * Elevated privileges: check for DCSync (T1003.003) events (DirSvc replication attempts).
  * Network: outbound connections around the same time.
  * Scope: search for similar events across domain controllers.

# 6) Investigation playbook skeleton (copy/paste into your case tool)

Title: Investigate \[Technique: TXXXX] — Short description

Steps:

1. **Initial validation** — confirm alert via EDR process evidence + SIEM logs. Save screenshot/packet capture.
2. **Identify scope** — list related hosts, users, IPs.
3. **Containment decision** — if host is critical or domain admin used → isolate now; otherwise increase monitoring.
4. **Forensics** — collect volatile data: running processes, network connections, relevant log slices, memory image if approved.
5. **Hunt for lateral activity** — check for same user logging into other hosts, suspicious RPC/SMB activity.
6. **Credential check** — force password change for compromised accounts if confirmed.
7. **Eradication** — remove persistence, patch/vuln fix, rotate creds.
8. **Recovery** — validate host clean, reimage if needed, restore services.
9. **Post-mortem** — map entire chain to ATT\&CK techniques, update detections, and add to knowledge base.

# 7) Example SIEM alert template (make every alert include this)

* Title: \[Technique] Short summary (e.g., T1059.001 — Suspicious encoded PowerShell on HOST123)
* ATT\&CK ID: T1059.001
* Evidence: EDR event IDs, timestamp, command line (redact secrets), file hash, remote IP.
* Initial hypothesis: suspected execution for C2 beaconing.
* Recommended action: Isolate host / Capture memory / Begin forensic capture.
* Assigned to: Analyst Name.
* SLA: X hrs.

# 8) Hunting recipes using ATT\&CK (small, repeatable)

* Hunt: **T1078 (Valid Accounts)** — query authentication logs for uncommon logon hours + new source IPs + multiple failed then successful logins.
* Hunt: **T1021.002 (SMB Lateral Movement)** — search for suspicious SMB session creation from non-admin endpoints or patterns of service creation via SMB.
* Hunt: **T1059 (Cmd/PowerShell)** — aggregate command-line telemetry: look for base64/encoded flags, one-liners that call IEX or download from uncommon domains.

# 9) When to escalate and what to notify

Escalate immediately if any of:

* Domain admin credentials exposed (T1003 + DCSync).
* Sensitive data exfiltration suspected (large outbound file transfers, cloud storage writes).
* Ransomware detected or signs of encryption activity.
* Multiple critical hosts affected or attacker has persistent foothold.

Notification should include: ATT\&CK techniques observed, evidence summary, containment actions taken, recommended next actions.

# 10) Creating ATT\&CK-based labels in the workflow

* Add tags to every case: `attack_tactic: Credential_Access`, `attack_technique: T1003`.
* Use these tags to build dashboards: coverage by technique, speed-to-detection by technique, volume of alerts per technique.
* This makes trend analysis and reporting trivial.

# 11) Metrics and KPIs for a SOC analyst team (what to measure)

* **MTTD** (Mean Time To Detect) per ATT\&CK technique.
* **MTTR** (Mean Time To Respond) per technique.
* **Coverage %** — percent of common techniques with at least one reliable detection.
* **False positive rate** by detection rule/technique.
* **Hunt success rate** — % hunts that produce meaningful detections.
* **Escalation frequency** — how often incidents require tier-2/IR involvement.

# 12) Documentation & knowledge base

* Keep a living doc that maps: ATT\&CK technique → data sources needed → typical fields to collect → investigation steps → playbook link.
* Store sample query snippets (Sigma or SIEM syntax) and sample command-lines that were malicious (avoid full payloads; redact secrets).

# 13) Communication templates (to stakeholders)

* Short executive summary: “On \[date], we observed behavior mapped to ATT\&CK T1059.001 (PowerShell execution). We contained the host, rotated affected credentials, and found no evidence of exfiltration. Action items: deploy enhanced logging to 200 servers.”
* For technical handoff: include timeline of events with ATT\&CK technique IDs, evidence artifacts, hashes/IOCs, and links to playbooks.

# 14) Training & continuous improvement

* Regularly review recent alerts and label them with ATT\&CK techniques — run a weekly “tagging” session to calibrate.
* Run purple-team exercises focused on 2–3 techniques and measure detection improvements (MTTD reduction).
* Keep a “playbook review” after any incident and update the technique mapping and automation.

# 15) Example mini-case walkthrough (compact)

Alert: SIEM shows `powershell.exe -encodedCommand ...` launched by `schtasks.exe` on HOST-A at 03:12 UTC.

1. Triage: map to **T1059.001 (PowerShell)**. Severity = Medium → investigate host.
2. Enrich: fetch parent process (schtasks), get scheduled task name, user account that scheduled task, network connections within ±5 min.
3. Investigate: command line decodes to a script that fetches from `evil.example.com`. EDR shows an outbound HTTPS connection to that domain.
4. Contain: isolate HOST-A, block `evil.example.com` at proxy, remove scheduled task, reset account used to create task.
5. Hunt: search for any other scheduled tasks created outside maintenance windows and similar command patterns.
6. Post-mortem: label entire event as Execution (T1059.001) → Command and Scripting Interpreter and add detection rule for scheduled tasks launching encoded PowerShell.

# 16) Tools & quick tips for analysts

* Use Navigator-style heatmaps internally to see which techniques trigger the most alerts.
* Always include ATT\&CK IDs in Jira/incident titles for easy aggregation.
* When writing detections, include a short “why this maps to ATT\&CK” line so future analysts understand intent.
* Don’t ignore low-severity alerts of certain techniques (e.g., repeated T1059 alerts can indicate reconnaissance).

---

If you want, I can:

* provide a ready-to-copy triage checklist in plain text you can paste into your ticketing system, or
* give 3 sample Sigma rules (high-level, non-abusive) for common techniques your environment has logs for (tell me which logs you have), or
* build a one-page playbook for investigating T1003 (credential dumping).

Which of those would help you most right now?
