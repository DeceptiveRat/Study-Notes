Malware most commonly uses Berkeley compatible sockets, whose functionality is almost identical on Windows and UNIX systems. They are implemented in the Winsock libraries

## 1) tips
- the WSAStartup function must be called before any other networking function. It is useful to find this function to find the start of networking
- 