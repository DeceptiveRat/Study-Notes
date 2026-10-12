1. Get-WinEvent
- tool for analyzing logs en masse
- can retrieve different types of event logs

2. example uses
2.1. retrieving events from the system log

```powershell
Get-WinEvent -LogName 'System' -MaxEvents 50 | Select-Object TimeCreated, ID, ProviderName, LevelDisplayName, Message | Format-Table -AutoSize
```

![unnamed_7383bb4cb36c4aecb89e8d61db6f591f](unnamed_7383bb4cb36c4aecb89e8d61db6f591f.png)

2.2. retrieving events from Microsoft-Windows-WinRM/Operational


```powershell
Get-WinEvent -LogName 'Microsoft-Windows-WinRM/Operational' -Oldest -MaxEvents 30 | Select-Object TimeCreated, ID, ProviderName, LevelDisplayName, Message | Format-Table -AutoSize
```
![unnamed_1dbe00afded540b09481b3772214f7e7](unnamed_1dbe00afded540b09481b3772214f7e7.png)
- -Oldest parameter to retrieve first events

2.3. retrieving events from .evtx files


```powershell
Get-WinEvent -Path 'C:\Tools\chainsaw\EVTX-ATTACK-SAMPLES\Execution\exec_sysmon_1_lolbin_pcalua.evtx' -MaxEvents 5 | Select-Object TimeCreated, ID, ProviderName, LevelDisplayName, Message | Format-Table -AutoSize
```
![unnamed_2bcf00d1abe84c32ac28c3f32c1b2722](unnamed_2bcf00d1abe84c32ac28c3f32c1b2722.png)
- -Path parameter for log path

2.4. filtering events with FilterHashtable




```powershell
Get-WinEvent -FilterHashtable @{LogName='Microsoft-Windows-Sysmon/Operational'; ID=1,3} | Select-Object TimeCreated, ID, ProviderName, LevelDisplayName, Message | Format-Table -AutoSize
```
![unnamed_107ce060b65940bf844abc7abc46eb8a](unnamed_107ce060b65940bf844abc7abc46eb8a.png)
```powershell
Get-WinEvent -FilterHashtable @{Path='C:\Tools\chainsaw\EVTX-ATTACK-SAMPLES\Execution\sysmon_mshta_sharpshooter_stageless_meterpreter.evtx'; ID=1,3} | Select-Object TimeCreated, ID, ProviderName, LevelDisplayName, Message | Format-Table -AutoSize
```

```powershell
$startDate = (Get-Date -Year 2023 -Month 5 -Day 28).Date
$endDate   = (Get-Date -Year 2023 -Month 6 -Day 3).Date
Get-WinEvent -FilterHashtable @{LogName='Microsoft-Windows-Sysmon/Operational'; ID=1,3; StartTime=$startDate; EndTime=$endDate} | Select-Object TimeCreated, ID, ProviderName, LevelDisplayName, Message | Format-Table -AutoSize
```


2.5. filtering events with FilterHashtable & XML





```powershell
Get-WinEvent -FilterHashtable @{LogName='Microsoft-Windows-Sysmon/Operational'; ID=3} |
`ForEach-Object {
$xml = [xml]$_.ToXml()
$eventData = $xml.Event.EventData.Data
New-Object PSObject -Property @{
    SourceIP = $eventData | Where-Object {$_.Name -eq "SourceIp"} | Select-Object -ExpandProperty '#text'
    DestinationIP = $eventData | Where-Object {$_.Name -eq "DestinationIp"} | Select-Object -ExpandProperty '#text'
    ProcessGuid = $eventData | Where-Object {$_.Name -eq "ProcessGuid"} | Select-Object -ExpandProperty '#text'
    ProcessId = $eventData | Where-Object {$_.Name -eq "ProcessId"} | Select-Object -ExpandProperty '#text'
}
}  | Where-Object {$_.DestinationIP -eq "52.113.194.132"}
```
![unnamed_80c86da53aa74a71a0410e9ef9f2ce48](unnamed_80c86da53aa74a71a0410e9ef9f2ce48.png)
```powershell
$Query = @"
	<QueryList>
		<Query Id="0">
			<Select Path="Microsoft-Windows-Sysmon/Operational">*[System[(EventID=7)]] and *[EventData[Data='mscoree.dll']] or *[EventData[Data='clr.dll']]
			</Select>
		</Query>
	</QueryList>
	"@
Get-WinEvent -FilterXml $Query | ForEach-Object {Write-Host $_.Message `n}
```
![unnamed_5e257613152748b3a042d102619b0b1d](unnamed_5e257613152748b3a042d102619b0b1d.png)

2.6. filtering events with FilterXPath


```powershell
Get-WinEvent -LogName 'Microsoft-Windows-Sysmon/Operational' -FilterXPath "*[EventData[Data[@Name='Image']='C:\Windows\System32\reg.exe']] and *[EventData[Data[@Name='CommandLine']='`"C:\Windows\system32\reg.exe`" ADD HKCU\Software\Sysinternals /v EulaAccepted /t REG_DWORD /d 1 /f']]" | Select-Object TimeCreated, ID, ProviderName, LevelDisplayName, Message | Format-Table -AutoSize
```
![unnamed_db1331ea59f24ee7bfccf00d3395021b](unnamed_db1331ea59f24ee7bfccf00d3395021b.png)
- -FilterXPath parameter to craft XPath query to filter event logs
- used to identify installation of any Sysinternal tools via registry key used during EULA acceptance



```powershell
Get-WinEvent -LogName 'Microsoft-Windows-Sysmon/Operational' -FilterXPath "*[System[EventID=3] and EventData[Data[@Name='DestinationIp']='52.113.194.132']]"
```
![unnamed_da874600267f4e2ba2eeda94ea21b018](unnamed_da874600267f4e2ba2eeda94ea21b018.png)
- to identify network connections to particular IP address

2.7. filtering events based on property values


```powershell
Get-WinEvent -FilterHashtable @{LogName='Microsoft-Windows-Sysmon/Operational'; ID=1} -MaxEvents 1 | Select-Object -Property *
```
![unnamed_3ab71fd6f53a4766a59cf743b830635d](unnamed_3ab71fd6f53a4766a59cf743b830635d.png)
- -Property * parameter used with Select-Object instructs the command to select all properties



```powershell
Get-WinEvent -FilterHashtable @{LogName='Microsoft-Windows-Sysmon/Operational'; ID=1} | Where-Object {$_.Properties[21].Value -like "*-enc*"} | Format-List
```
![unnamed_c7c172f5adbb408d939393bb09280037](unnamed_c7c172f5adbb408d939393bb09280037.png)
- $_: current object in pipeline 
- .Properties[21].Value: array containing various data about event. Index 21 corresponds to ParentCommandLine property of event

reference:
HTB academy: <https://academy.hackthebox.com/module/216/section/2322>