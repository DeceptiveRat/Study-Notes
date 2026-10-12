1. windows event log
- record of events related to system, security, and application
- used to track system and application issues
- kept under C:\WINDOWS\system32\config\folder
- can be checked with event viewer

2. windows event log elements
- log name
- event date/time
- task category
- event id
- source
- level 
- user
- computer

3. windows event log categories
- system log
   - failure to load boot-start driver
- application log
   - problem starting PowerPoint
- security
   - failed logins
   - file deletions
- setup
   - events that occur during installation of OS
- forwarded events

4. windows event log types
- information: app or service working well
   - network driver loaded
- warning: potential issues in future
   - low disk space
- error: significant issue
   - OS stops responding
- success audit: valid attempt of audited security access
   - successful login
- failure audit: failure of audited security access
   - inability to access network drive

reference:
- <https://www.solarwinds.com/resources/it-glossary/windows-event-log>