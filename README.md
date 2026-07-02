# SOC-Lab-03-PowerShell-Download-Investigation
### Objective

Investigate a PowerShell execution that used suspicious command-line arguments to download remote content and determine whether the activity was malicious or benign.

### Skills Demonstrated

- Splunk investigations

- Sysmon Event ID 1 analysis

- Sysmon Event ID 11 (File Create)

- Process tree analysis

- Command-line analysis

- Network activity identification

- Evidence-based triage

- MITRE ATT&CK mapping

- Incident documentation

### Environment

| Component        | Technology                 |
| ---------------- | -------------------------- |
| SIEM             | Splunk Enterprise          |
| Endpoint Logs    | Sysmon                     |
| Operating System | Windows 11                 |
| Log Forwarding   | Splunk Universal Forwarder |

### Detection
Suspicious PowerShell Execution

## PowerShell executed with the following suspicious parameters:

- -ExecutionPolicy Bypass

- -WindowStyle Hidden

Invoke-WebRequest

- -OutFile

## These arguments in the path are frequently associated with attackers and therefore warranted an investigation.
