# Get Folder Size from Windows Command Line
```
$fso = new-object -com Scripting.FileSystemObject
gci -Directory `
  | select @{l='Size'; e={$fso.GetFolder($_.FullName).Size}},FullName `
  | sort Size -Descending `
  | ft @{l='Size [MB]'; e={'{0:N2}    ' -f ($_.Size / 1MB)}},FullName
```


# check service is using which port
```
netsh http show servicestate | Select-String "1088"
```
more context:
```
netsh http show servicestate | Select-String "1088" -Context 2
```

# Kill pid
```
taskkill /PID 2356 /F
```

# get cpu starttime
Get-Process -Name chrome | Select-Object Id, ProcessName, StartTime, @{Name="CPU(s)";Expression={$_.CPU}}


#IIS 
# Remove IIS Sites ending with "_dev"
Get-IISSite | Where-Object { $_.Name -like "*_Development" } | ForEach-Object {
    Write-Host "Removing site: $($_.Name)"
    Remove-IISSite -Name $_.Name -Confirm:$false
}
