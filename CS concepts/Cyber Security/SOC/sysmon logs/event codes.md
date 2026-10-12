1. event code 1
- process creation
- find abnormal parent-child hierarchy

2. event code 2
- process changed file creation time
- spot "time stomp" attacks

3. event code 3
- network connection

4. event code 4
- sysmon service state changed

5. event code 5
- process terminated
- detect sacrificial processes

6. event code 6
- driver loaded
- potential flag for Bring Your Own Driver (BYOD) attacks

7. event code 7
- image loaded
- detect dll hijacks

8. event code 8
- CreateRemoteThread
- identify injected threads

9. event code 10
- ProcessAccess
- detect remote code injection and memory dumping
- records when handles on processes are made

10. event code 11
- FileCreate
- correlate or identify file's origin

11. event code 12/13
- RegistryEvent (object create and delete/value set)

12. event code 15
- FileCreateStreamHash
- relates to file streams and external downloads

13. event code 16
- sysmon config state changed

14. event code 17/18
- pipe created/pipe connected
- observe malware IPC, PSExec, and SMB lateral movement

15. event code 22
- DNSEvent

16. event code 23
- FileDelete

17. event code 25
- ProcessTampering