1. creating socket

```python3
# TCP
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
# UDP
s = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
```


2. get IP

```python3
try: 
    host_ip = socket.gethostbyname('www.google.com') 
except socket.gaierror:
```


3. connect

```python3
s.connect((host_ip, port))
```


4. send data

```python3
# TCP

# UDP
s.sendto(MESSAGE, (UDP_IP, UDP_PORT))
```


5. receive data

```python3
# TCP

# UDP
sock.bind((UDP_IP, UDP_PORT))
data, addr = sock.recvfrom(1024) # buffer size is 1024 bytes
```


reference:
- geeksforgeeks - python socket programming: <https://www.geeksforgeeks.org/python/socket-programming-python/>
- python wiki - UDP communication: <https://wiki.python.org/moin/UdpCommunication>