
```c
char destinationAddress[INET_ADDRSTRLEN];
struct addrinfo hints;
struct addrinfo *servinfo; // this will point to the results

memset(&hints, 0, sizeof(hints)); // make sure the struct is empty
hints.ai_family = AF_INET;
hints.ai_socktype = SOCK_STREAM; // TCP stream sockets

if(getaddrinfo(destinationName, "443", &hints, &servinfo) != 0)
{
	fatal("finding destination address");
}

struct sockaddr_in *addr = (struct sockaddr_in*)servinfo->ai_addr;
inet_ntop(AF_INET, &(addr->sin_addr), destinationAddress, INET_ADDRSTRLEN);
printf("has address: %s", destinationAddress);

freeaddrinfo(servinfo);
```


<https://beej.us/guide/bgnet/html/#getaddrinfoprepare-to-launch>

