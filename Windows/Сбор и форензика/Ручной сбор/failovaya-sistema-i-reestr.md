# Файловая система и реестр

```powershell
Get-PSDrive : Enumerate All Drives
Get-ChildItem -Path C:\path\to\directory -Recurse : Retrieve Files in a Specific Directory 
Get-ItemProperty -Path "HKCU:\Software\Microsoft\Windows\CurrentVersion\Run" : Query Registry Key for Persistence Mechanisms
Get-ItemProperty -Path "HKCU:\Software\Microsoft\Windows\Shell\BagMRU": Retrieve ShellBag Information (User File and Folder History)
Get-ChildItem -Path "C:\Logs\" -Filter *.log | Select-String -Pattern "error|fail|attack"  : Search Across Log Files for Keywords

Get-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Run" |
Where-Object { $_.Property -match "cmd|powershell|vbs" }  : Searching within the Registry for Suspicious Keys 

Get-ChildItem -Path HKLM:\ -Recurse | Get-ItemProperty -ErrorAction SilentlyContinue |
Where-Object { $_.PSChildName -match "suspicious_keyword" } : Search for Specific String Across Registry Keys

Get-Item "C:\path\to\file.txt" | Select-Object -Property Name, CreationTime, LastAccessTime, LastWriteTime  : Extracting Artifact Metadata from Files

```
