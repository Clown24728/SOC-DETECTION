# IOC table for the supposed project and MITTRE ATT&CKS.
# Indicators of Compromise (IOC) Table

| # | IOC Type | Value / Indicator | Description / Context | Source / Evidence | MITRE ATT&CK Technique | Confidence / Notes |
|---|----------|-------------------|-----------------------|-------------------|------------------------|--------------------|
| 1 | Email Address | `Hendrikluca@gmail.com` | Sender of initial phishing email | Email gateway / M365 Message Trace | T1566.001 Phishing: Spearphishing Attachment | High – initial vector |
| 2 | Email Subject | Pluracode Admin Dept | Subject line used in phishing campaign | M365 Message Trace / Outlook logs | T1566.001 | High |
| 3 | File Hash (SHA-256) | `a1b2c3d4e5f678901234567890abcdef1234567890abcdef1234567890abcdef` | Malicious Word document / payload dropper | Sysmon Event ID 1 / File creation logs | T1204.002 User Execution: Malicious File | High |
| 4 | File Name | `portal update` | Ransomeware attacks of information | Endpoint / Sysmon | T1204.002 | High |
| 7 | Domain / URL | `hxxps://cdn-update[.]secure-updates[.]net/payload.bin` | C2 / payload download URL | Network logs / Proxy / Sysmon | T1071.001 Web Protocols | High |
| 8 | IP Address | `185.234.72.45` | Command-and-Control (C2) server | Firewall / Proxy / DNS logs | T1071 | High |
| 9 | User Account | `Hendrik` (newly created) | Local / domain account created for persistence | Windows Security Event 4720 | T1136.001 Create Account: Local Account | Medium-High |
| 11 | Registry Key | `HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Run\WinUpdate` | Persistence via Run key | Sysmon Event ID 13 | T1547.001 Registry Run Keys | High |
| 13 | File Extension | `.locked` / `.encrypted` / `.crimson` | Ransomware encrypted file extension | File system / Endpoint detection | T1486 Data Encrypted for Impact | High |
| 14 | Ransom Note | `README_RESTORE_FILES.txt` | Ransom note dropped on file servers | File system artifacts | T1486 | High |
