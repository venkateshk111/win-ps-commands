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

### Sample Output

```
FullName SizeGB

C:\Path\To\LargeFile1.txt 4.56
C:\Another\Path\LargeFile2.exe 2.34

```

## Command to list top 10 process consuming high CPU
```
Get-Process | Sort-Object -Property CPU -Descending | Select-Object -First 10
```

### Sample Output

```
Handles  NPM(K)    PM(K)      WS(K)     CPU(s)   Id  SI ProcessName
-------  ------    -----      -----     -------   --  -- -----------
  13394     276   176996     209328    8540.78 1232   0 chrome
   3627     123    65544      66752    1323.70 2672   0 explorer
   4227      92    40980      60684     640.69 4832   0 slack
   3514      84    39540      61824     418.83 6824   0 powershell
   5851     105    34956      58300     415.78 7344   0 Code
   2961      77    23364      42784     327.50 2620   0 Microsoft.Teams
   1662      72    22260      28116     245.25 6044   0 OneDrive
   4441     105    49840      59240     231.84 4504   0 Discord
   1644      70    23668      30776     216.06 6964   0 Spotify
   3705      98    20492      29820     197.75 5292   0 WindowsTerminal

```
