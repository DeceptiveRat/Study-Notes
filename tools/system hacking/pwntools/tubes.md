## receiving data
- recv(n)
- recvn(n)
- recvline()
- recvuntil(delim)
- recvregex(pattern)
- recvrepeat(timeout)
- clean()

## sending data
- send(data)
- sendline(line)

## integer manipulation
- pack(int)
- unpack()

## networking
- remote()

```python3
io = remote('google.com', 80)
dns  = remote('8.8.8.8', 53, typ='udp')
tcp6 = remote('google.com', 80, fam='ipv6')
```

- listen()

```python3
client = listen(8080).wait_for_connection()
```


## secure shell
- session()



```python3
session = ssh('bandit0', 'bandit.labs.overthewire.org', 2220, password='bandit0')
io = session.process('/bin/sh', env={"PS1":""})
```
## serial ports
- serialtube

```python3
io = serialtube('/dev/ttyUSB0', baudrate=115200)
```


reference:
<https://github.com/Gallopsled/pwntools-tutorial/blob/master/tubes.md>