1. basic searching

```plain-text
search index="main" "UNKNOWN"
```

- query narrows down to events stored in main index
- UNKNOWN is used as keyword to retrieve events including this term
- wildcards (*) can be used

2. fields and comparison operators

```plain-text
index="main" EventCode!=1
```

- search main index for events without event code 1

3. fields command

```plain-text
index="main" sourcetype="WinEventLog:Sysmon" EventCode=1 | fields - User
```

- exclude User field from search results

4. table command

```plain-text
index="main" sourcetype="WinEventLog:Sysmon" EventCode=1 | table _time, host, Image
```

- arranges selected fields in tabular format

5. rename command

```plain-text
index="main" sourcetype="WinEventLog:Sysmon" EventCode=1 | rename Image as Process
```

- rename Image field to Process

6. dedup command

```plain-text
index="main" sourcetype="WinEventLog:Sysmon" EventCode=1 | dedup Image
```

- remove duplicates based on Image field

7. sort command

```plain-text
index="main" sourcetype="WinEventLog:Sysmon" EventCode=1 | sort - _time
```

- sort in descending order of timestamps

8. stats command

```plain-text
index="main" sourcetype="WinEventLog:Sysmon" EventCode=3 | stats count by _time, Image
```

- returns table where each row represents a unique combination of a timestamp and a process
- count column indicates number of network connections

9. chart command

```plain-text
index="main" sourcetype="WinEventLog:Sysmon" EventCode=3 | chart count by _time, Image
```

- return table where each row represents a unique timestamp and each column represents a unique process
- cell values indicate number of network connections

10. eval command

```plain-text
index="main" sourcetype="WinEventLog:Sysmon" EventCode=1 | eval Process_Path=lower(Image)
```

- creates new field Process_Path which contains lowercase version of Image
- the new field can be changed without affecting Image

11. rex command

```plain-text
index="main" EventCode=4662 | rex max_match=0 "[^%](?<guid>{.*})" | table guid
```

- regex pattern {.*} looks for substrings that begin with { and end with }
- [^%] ensures match does not begin with %
- captured value within curly braces is assigned to named capture group guid

12. lookup command
- enriches data with external sources
- malware_lookup.csv


```plain-text
filename, is_malware
notepad.exe, false
cmd.exe, false
powershell.exe, false
sharphound.exe, true
randomfile.exe, true
```

```plain-text
index="main" sourcetype="WinEventLog:Sysmon" EventCode=1 | rex field=Image "(?P<filename>[^\\\]+)$" | eval filename=lower(filename) | lookup malware_lookup.csv filename OUTPUTNEW is_malware | table filename, is_malware
```

- extract filename
- perform lookup operation with filename as key
- if match is found, new field is_malware is added to event
- format output to show only the fields filename and is_malware

13. inputlookup command

```plain-text
| inputlookup malware_lookup.csv
```

- retrieves data from lookup file without joining it to search results
- used to verify content of lookup file or subsequent operations

14. time range

```plain-text
index="main" earliest=-7d EventCode!=1
```

- retrieve events that occurred in the last 7 days

15. transaction command

```plain-text
index="main" sourcetype="WinEventLog:Sysmon" (EventCode=1 OR EventCode=3) | transaction Image startswith=eval(EventCode=1) endswith=eval(EventCode=3) maxspan=1m | table Image |  dedup Image 
```

- group events based on Image
- the grouped transactions start with event with EventCode 1 and ends with EventCode 3
- transaction happened in 1-minute span

16. subsearches

```plain-text
index="main" sourcetype="WinEventLog:Sysmon" EventCode=1 NOT [ search index="main" sourcetype="WinEventLog:Sysmon" EventCode=1 | top limit=100 Image | fields Image ] | table _time, Image, CommandLine, User, ComputerName
```

- exclude results from subsearch

references
- htb academy
<https://academy.hackthebox.com/module/218/section/2356>
