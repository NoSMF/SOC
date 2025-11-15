# Информация о пользователях

```powershell
whoami
whoami /user
net users
net localgroup administrators
net group /domain [groupname]
net user /domain [username]
wmic sysaccount
wmic useraccount get name,SID
wmic useraccount list
Get-LocalUser
Get-LocalGroup
Get-LocalGroupMember Administrators
Get-LocalUser : Retrieve Local User Accounts
Get-EventLog -LogName Security | Where-Object {$_.EventID -eq 4624}
```

Информация об активных сессиях:\


```powershell
wmic netlogin list /format:List
Get-WmiObject Win32_LoggedOnUser
Get-WmiObject win32_logonsession
query user
quser : List Active User Sessions 
qwinsta
klist sessions
klist -li
```
