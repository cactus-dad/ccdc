
```powershell
Get-NetTCPConnection |
 Where-Object {$_.State -eq "Listen"} |
 Select-Object @{Name="LocalPort";Expression={$_.LocalPort}},
               @{Name="RemotePort";Expression={$_.RemotePort}},
               @{Name="OwningProcess";Expression={
                   if ($_.OwningProcess) {
                       (Get-Process -Id $_.OwningProcess).Name
                  }
                  else {
                       "Unknown"
                  }
               }}
```