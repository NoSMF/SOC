# Информация о системе

```powershell
get-computerinfo
echo %DATE% %TIME%
date /t
time /t
reg query "HKLM\System\CurrentControlSet\Control\TimeZoneInformation"
systeminfo
wmic computersystem list full
wmic /node:localhost product list full /format:csv
wmic softwarefeature get name,version /format:csv
wmic softwareelement get name,version /format:csv
reg query "HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion" /s
echo %PATH%
(gci env:path|Select -exp Value).split(';')
SET
wmic bootconfig get /all /format:List
wmic computersystem get name, domain, manufacturer, model, numberofprocessors,primaryownername,username,roles,totalphysicalmemory /format:list
wmic timezone get Caption, Bias, DaylightBias, DaylightName, StandardName
wmic recoveros get /all /format:List
wmic os get /all /format:list
wmic partition get /all /format:list
wmic logicaldisk get /all /format:list
wmic diskdrive get /all /format:list
fsutil fsinfo drives
$env
Get-Variable
Get-SystemInfo: Retrieves detailed system information.
Get-ComputerInfo : 
Get-WmiObject -Class Win32_OperatingSystem : Gather information about the Operating System
Get-ItemProperty HKLM:\Software\Microsoft\Windows\CurrentVersion\Uninstall\* : Retrieve Installed Software
(Get-WmiObject -Class Win32_OperatingSystem).LastBootUpTime : Check System Boot Time
Get-ChildItem env:\  : to get all Environment Variables
dir env:\
```
