1. sysmon
- addon for windows logging
- capabilities
   - logs process creation with full command line for both current and parent processes
   - record hash of process image files
   - includes process GUID in process creation events => can correlate even if PID is reused
   - includes session GUID in each event => can correlate events on same logon session
   - logs loading of drivers/DLLs with their signature/hashes
   - logs opens for raw read access of disks/volumes
   - optionally logs network connections
   - detects changes in file creation time
   - automatically reload configuration if changed in registry
   - rule filtering to include/exclude events
   - generates events from early in boot process => captures activity by sophisticated kernel-mode malware

reference:
- Microsoft - Sysmon: <https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon>