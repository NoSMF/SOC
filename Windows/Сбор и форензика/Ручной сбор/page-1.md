# Page 1



#### Network Information

```
Get-NetTCPConnection : List Active Network Connections
Get-NetIPAddress : Retrieve IP Address Information 
Get-SmbShare : List Active Network Shares 

Get-NetTCPConnection | Where-Object { $_.RemoteAddress -notlike "127.*" -and $_.RemoteAddress -notlike "::1" } : List Only Foreign (External) Network Connections

Get-NetTCPConnection | Where-Object { $_.RemotePort -eq 443 -or $_.RemoteAddress -match "^192\.168\." } : Filter Connections by Specific Port or IP Range

Get-NetTCPConnection -State Established : Find Established Network Connections 
```

#### Inspecting Loaded Modules and DLLs for Process Analysis

```
Get-Process | ForEach-Object { $_.Modules | Select-Object -Property ModuleName, FileName } : List Loaded Modules for Each Process
(Get-Process -Name "notepad").Modules | Select-Object ModuleName, FileName  :  Analyze DLLs Loaded by a Specific Process 
```

#### Event Log Analysis

```
Get-EventLog -LogName Security : Retrieve Security Event Logs
Get-WinEvent -LogName Security | Where-Object {$_.Id -eq 4624} : Filter Specific Event ID (e.g., Successful Logon)
Get-EventLog -LogName Security | Export-Csv -Path C:\Logs\SecurityLog.csv : Export Event Logs for Analysis 
Get-ChildItem -Path "C:\Logs" -Filter *.log | Select-String -Pattern "error|login failure" |
Out-File -FilePath "C:\Forensics\matching_logs.txt"  : Log Matching Results to a File
Get-WinEvent -FilterHashtable @{LogName='Security'; Id=4624} | Where-Object {$_.Message -match "Admin"}
```

#### History

```
Get-History 
Get-History | Format-Table -AutoSize
```

#### Browser and Internet Activity

```
Get-Item -Path "HKCU:\Software\Microsoft\Internet Explorer\TypedURLs": Retrieve Browser History for Edge/IE 
ipconfig /displaydns : Retrieve DNS Cache 
```

#### Collecting Evidence

```
Get-WmiObject -Class Win32_PhysicalMemory : Take a Snapshot of Memory Information 
Get-ChildItem Env :  Retrieve System Environment Variables
(Get-PSReadLineOption).HistorySavePath : Dump All Available PowerShell History
```

#### Malware Detection and Analysis

```
Get-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Run" : List Autoruns for Persistence Detection 
Get-ScheduledTask | Select-Object TaskName,TaskPath,State : List All Scheduled Tasks 
Get-WmiObject -Class Win32_Service | Where-Object { $_.StartMode -eq 'Auto' -and $_.State -ne 'Running' } : Check for Hidden Services or Processes
```

#### Using Hashing for File Integrity Verification

```
Get-FileHash -Algorithm SHA256 -Path "C:\path\to\file" : Compute File Hash 

$hash1 = Get-FileHash -Path "C:\path\to\original_file"
$hash2 = Get-FileHash -Path "C:\path\to\new_file"                               : Compare Hashes Across Files for Tampering Detection
if ($hash1.Hash -ne $hash2.Hash) { Write-Output "Files differ!" }
```
