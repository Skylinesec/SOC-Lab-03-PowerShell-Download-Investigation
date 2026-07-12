## Investigation
### Step 1 – Identify PowerShell Execution
<img width="985" height="716" alt="Screenshot 2026-07-02 at 19 01 16" src="https://github.com/user-attachments/assets/b107394d-c10a-4ce9-8a63-a8421bca2f50" />

### Step 2 – Review Process Details
| Field            | Value                      |
| ---------------- | -------------------------- |
| User             | Jetros-Laptop\jetro        |
| Process          | powershell.exe             |
| Parent Process   | powershell.exe             |

### Step 3 – Analyze the Command Line
<img width="1382" height="747" alt="Screenshot 2026-07-02 at 19 08 35" src="https://github.com/user-attachments/assets/d278bb64-caf7-4612-b267-87d69c497c1e" />

### Step 4 – Investigate File Creation
<img width="697" height="476" alt="Screenshot 2026-07-02 at 19 21 37" src="https://github.com/user-attachments/assets/d52c560f-44a1-48e9-81e0-f30bd1d0adfc" />

### Findings:
- PowerShell created a temporary __PSScriptPolicyTest file (this is normal PowerShell behavior).
- However the file example.html was confirmed to exist in the user's (Jetro) Temp directory.

### Step 5 – Child Process Analysis
- **Result:** No child processes were observed originating from the PowerShell process.

## Findings

| Finding                | Result                           |
| ---------------------- | -------------------------------- |
| PowerShell Executed    | Yes                              |
| ExecutionPolicy Bypass | Yes                              |
| Hidden Window          | Yes                              |
| Outbound Web Request   | Yes                              |
| Remote URL             | https://example.html             |
| File Written to Disk   | Yes (Example.html in Temp folder)|
| Child Processes        | None Observed                    |
| Persistence Activity   | None Observed                    |
| Registry Modifications | None Observed                    |
| Malicious Payload      | None Observed                    |


PowerShell executed using the **-ExecutionPolicy Bypass** and **-WindowStyle Hidden** parameters, then initiated an outbound web request to https://example.com using Invoke-WebRequest. 
The response was successfully written to example.html in the user's temporary directory.  
Review of Sysmon telemetry identified no child processes, persistence mechanisms, registry modifications, or additional suspicious activity following execution. 
Although the command-line arguments resemble techniques commonly used by threat actors, the destination domain was benign and no indicators of malicious behavior were identified during the investigation.

| Severity               | Medium                                   |
| ---------------------- | --------------------------------         |
| Disposition            | Benign Activity – No Escalation Required |

## MITRE ATT&CK

| Technique               | Description                      |
| ----------------------  | -------------------------------- |
| T1059.001               | PowerShell                       |
| T1105                   | Ingress tool transfer            |

