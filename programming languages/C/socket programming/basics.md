- inet_ntoa(), inet_aton() is deprecated. Use inet_ntop() and inet_pton()
- inet_ntop(): in_addr -> string
- inet_pton(): string -> in_addr
- gethostbyname() is deprecated
- create socket:

```c
socket(AF_INET, SOCK_DGRAM, 0); // UDP
socket(AF_INET, SOCK_STREAM, 0); // TCP
```


---
reference:
<https://beej.us/guide/bgnet/html/#structs>