Here's a solid list of **Linux commands** a **SOC analyst** should know, along with explanations of **when and why** to use each:

---

### 🧠 **System Information & Monitoring**
| Command | When to Use | Description |
|--------|-------------|-------------|
| `uname -a` | Checking kernel & system info | Shows OS, kernel version, architecture |
| `top` / `htop` | Monitoring live system usage | CPU, memory, process load |
| `uptime` | Checking how long the system has been up | Also shows load averages |
| `vmstat` | Investigating system performance | Shows memory, processes, I/O, etc. |
| `lsof` | Checking open files & processes | Useful for detecting suspicious activity |

---

### 📁 **File & Directory Investigation**
| Command | When to Use | Description |
|--------|-------------|-------------|
| `ls -la` | Listing detailed contents | Shows hidden files and permissions |
| `find / -name "filename"` | Locating suspicious files | Full disk search for files |
| `du -sh *` | Checking large directories | Helpful for detecting storage anomalies |
| `stat filename` | Viewing file metadata | See creation/modification times |
| `md5sum filename` / `sha256sum filename` | File integrity check | Compare hashes with known safe versions |

---

### 🔍 **Log Analysis**
| Command | When to Use | Description |
|--------|-------------|-------------|
| `cat /var/log/auth.log` | Reviewing login attempts | Audit SSH login activity |
| `journalctl -xe` | Viewing system logs | Systemd-based log analysis |
| `grep "keyword" filename` | Searching logs | Find patterns in log files |
| `tail -f /var/log/syslog` | Live log monitoring | Watch logs in real time |
| `less /var/log/messages` | Navigating logs | Easier navigation with scroll/search |

---

### 👤 **User and Permission Management**
| Command | When to Use | Description |
|--------|-------------|-------------|
| `who` / `w` | See who's logged in | Shows user sessions |
| `last` | Check login history | Good for incident timelines |
| `id` | Check user permissions | Groups and UID info |
| `groups username` | See group memberships | Helps verify access levels |
| `sudo -l` | List allowed sudo actions | For privilege escalation investigation |

---

### 📡 **Network Monitoring**
| Command | When to Use | Description |
|--------|-------------|-------------|
| `netstat -tulnp` | List open ports and connections | Detect unexpected services |
| `ss -tulwn` | Faster alternative to netstat | Shows open ports and listening addresses |
| `ifconfig` / `ip a` | Check IP addresses | Confirm network interface configurations |
| `tcpdump -i eth0` | Capture network packets | Deep packet inspection |
| `ping` / `traceroute` | Network troubleshooting | Test connectivity or trace routes |
| `nmap localhost` | Scan open ports/services | Localhost or remote machine scanning |

---

### 📂 **Processes & Services**
| Command | When to Use | Description |
|--------|-------------|-------------|
| `ps aux` | View all processes | Great for spotting rogue processes |
| `kill -9 PID` | Stop malicious process | Forcefully kill a PID |
| `systemctl status service` | Check service status | Verify if a suspicious service is running |
| `service --status-all` | List all services | Quick glance at system services |

---

### 🔐 **Security & Audit**
| Command | When to Use | Description |
|--------|-------------|-------------|
| `auditctl -l` | See current audit rules | What’s being logged by auditd |
| `ausearch -x /bin/bash` | Search audit logs | Investigate command execution |
| `chkrootkit` / `rkhunter` | Check for rootkits | Use to detect known malware |
| `crontab -l` / `cat /etc/crontab` | Review scheduled tasks | Check for persistence mechanisms |

---

Would you like a printable version (PDF or markdown), or maybe a cheat sheet format? Also, I can add examples of suspicious behavior to detect with these commands if that’d help.