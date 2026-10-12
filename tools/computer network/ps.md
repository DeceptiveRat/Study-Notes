## (1) examples
1. view all running processes
- ps -A
- ps -e

2. all processes in BSD format
- ps aux

3. for full format listing
- ps -f
- ps -F

4. all processes owned by you
- ps -X

5. processes by RUID
- ps -U 1000

6. processes by EUID
- ps -u 1000

7. processes by RGID
- ps -G apache

8. processes by PPID
- ps --ppid 1154

9. processes by tty
- ps -t pts/0

10. process tree
- ps --forest

11. to print in custom format
- ps -o pid,ppid,user,cmd

## (2) notes
1. fields
- USER = user owning the process
- PID = process ID of the process
- %CPU = It is the CPU time used divided by the time the process has been running.
- %MEM = ratio of the process’s resident set size to the physical memory on the machine
- VSZ = virtual memory usage of entire process (in KiB)
- RSS = resident set size, the non-swapped physical memory that a task has used (in KiB)
- TTY = controlling tty (terminal)
- STAT = multi-character process state
- START = starting time or date of the process
- TIME = cumulative CPU time
- COMMAND = command with all its arguments

2. state codes
- D: uninterruptible sleep (usually IO) 
- I: Idle kernel thread 
- R: running or runnable (on run queue) 
- S: interruptible sleep (waiting for an event to complete) 
- T: stopped by job control signal 
- t: stopped by debugger during the tracing 
- W: paging (not valid since the 2.6.xx kernel) 
- X: dead (should never be seen) 
- Z: defunct ("zombie") process, terminated but not reaped by its parent