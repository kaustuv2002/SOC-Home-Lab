[06:14:2026] Security Incident: Unauthorized SMB Authentication Attempt

Date: June 14, 2026
Status: Remediated
Detection Source: Wazuh SIEM / Windows Security Event Log
MITRE ATT&CK Mapping: T1110.001 - Brute Force: Password Guessing


Observation:
SIEM Rule Triggered: Rule 92652 (Possible NTLM abuse / pass-the-hash indicator)
Event Type: Windows Security Event ID 4625 (Failed Logon Attempts)
Pattern Observed: High-frequency authentication failures within seconds
Protocol Targeted: SMB (NTLM Authentication)
Target Account: Administrator
At 18:04:15, the SIEM correlation engine flagged a spike in anomalous authentication activity consistent with brute-force behavior patterns. Within 15 seconds, supporting Windows security logs confirmed repeated authentication failures aligned with automated credential spraying or dictionary-based guessing attempts.

![Attack1](https://github.com/kaustuv2002/SOC-Home-Lab/blob/cff54af61fdbb28b955fd15b5b8967b4c0f79cb5/image/bruteforce.png)
![Data](https://github.com/kaustuv2002/SOC-Home-Lab/blob/a66c37f9b132d798a26e7e25c2f7073ccc338460/image/authfail.png)

Investigation: Filtered logs verified the source IP 192.168.56.105 (Kali Linux) was performing a dictionary-based attack against the Administrator account using the NTLM authentication protocol.
![foundattacker](https://github.com/kaustuv2002/SOC-Home-Lab/blob/73da961b86d3124ac1cd9396695179842989181e/image/found%20the%20attacker.png)

Impact Assessment
Confidentiality: No evidence of successful authentication
Integrity: No system modification detected
Availability: No service disruption observed
Overall Impact: Low (attempt only, no compromise achieved)


Response Actions
To mitigate the threat and prevent further brute-force attempts, I implemented a SOAR (Security Orchestration, Automation, and Response) workflow using Wazuh Active Response.

Response Strategy: Configured the Wazuh Manager to automatically trigger firewall-drop via Rule ID 92652.
![firewall](https://github.com/kaustuv2002/SOC-Home-Lab/blob/ab13beb6647c0d8410383d9597310cf337b399f3/image/fi.png)


Implementation:

