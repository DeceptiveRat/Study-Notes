
```c
#define MAX_EVENTS 2
#define BUFFER_SIZE 1024

int main() {
    int ipv4_sock = create_udp_socket(NULL, "5353", AF_INET);   // IPv4 socket
    int ipv6_sock = create_udp_socket(NULL, "5353", AF_INET6); // IPv6 socket

    set_nonblocking(ipv4_sock);
    set_nonblocking(ipv6_sock);

    // Create an epoll instance
    int epfd = epoll_create(1);
    if (epfd == -1) {
        perror("epoll_create");
        exit(1);
    }

    // Add both sockets to the epoll instance
    struct epoll_event event;
    event.events = EPOLLIN; // We want to monitor incoming data

    event.data.fd = ipv4_sock;
    epoll_ctl(epfd, EPOLL_CTL_ADD, ipv4_sock, &event);

    event.data.fd = ipv6_sock;
    epoll_ctl(epfd, EPOLL_CTL_ADD, ipv6_sock, &event);

    struct epoll_event events[MAX_EVENTS];

    while (1) {
        int ready_fds = epoll_wait(epfd, events, MAX_EVENTS, -1);
        if (ready_fds == -1) {
            perror("epoll_wait");
            exit(1);
        }

        for (int i = 0; i < ready_fds; i++) {
            int sockfd = events[i].data.fd;
            struct sockaddr_storage client_addr;
            socklen_t addr_len = sizeof(client_addr);
            char buffer[BUFFER_SIZE];

            ssize_t bytes_received = recvfrom(sockfd, buffer, BUFFER_SIZE, 0, 
                                              (struct sockaddr *)&client_addr, &addr_len);
            // logic
        }
    }

    close(ipv4_sock);
    close(ipv6_sock);
    close(epfd);
    return 0;
}

```

- <sys/epoll.h>