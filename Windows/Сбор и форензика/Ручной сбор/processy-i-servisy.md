# Процессы и сервисы

```powershell
Get-Process : List Running Processes 
Get-Process | Where-Object {$_.ProcessName -match "powershell|notepad"} : Filter Output from Commands
Get-Process | Select-Object -Property Path, Name, Id 
Get-Service  :  List Installed Services 
Get-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Run" : Query Startup Applications 
Get-Service | Export-Csv -Path services.csv : print all the info into csv file
Get-Process | Out-File -FilePath processes.txt -Append :
Get-Process | ForEach-Object {
    if ($_.CPU -gt 100) {
        Write-Output "$($_.ProcessName) is using high CPU!"  
    }
}
 
Get-Service | Where-Object { $_.Status -eq 'Running' } | ForEach-Object { $_.DisplayName } : Extract Information from Command Output (Pipeline Parsing)
```
