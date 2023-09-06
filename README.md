# win-ps-commands
Windows Powershell Commands

## Disclaimer

Use this commands responsibly and ensure you have a backup of your important data before running any commands listed below


## Find Large Files 
This PowerShell script helps you find large files on your C drive and displays their details such as full path and size in gigabytes (GB).

Find Large Files > `300MB`  This command will search for files on the C drive that are larger than `300MB`. You can adjust the file size limit by modifying the `300MB` value.

```
Get-ChildItem -Path "C:\" -File -Recurse -ErrorAction SilentlyContinue | Where-Object { $_.Length -gt 300MB } | Select-Object FullName, @{Name="SizeGB"; Expression={"{0:N2}" -f ($_.Length / 1GB)}} | Sort-Object -Property SizeGB -Descending

```

## Sample Output

```
FullName SizeGB

C:\Path\To\LargeFile1.txt 4.56
C:\Another\Path\LargeFile2.exe 2.34

```

## Command to list top 10 process consuming high CPU
```
Get-Process | Sort-Object -Property CPU -Descending | Select-Object -First 10
```
