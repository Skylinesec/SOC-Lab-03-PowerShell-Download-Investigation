## PowerShell Events
SPL: index=main EventCode=1 Image="*powershell.exe"

## File Creation Events
SPL: index=main EventCode=11 TargetFilename="example"

## Child Process Investigation
SPL: index=main EventCode=1 ParentProcessGuid

## Timeline
index=main EventCode IN (1,11) | table _time EventCode Image TargetFilename CommandLine | sort _time
