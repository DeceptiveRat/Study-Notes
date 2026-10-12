You’re absolutely right that for a basic server, you primarily need a **port number** to bind on. However, there are additional details that go into setting up a socket, and `AI_PASSIVE` helps automate those as part of the `getaddrinfo()` function. Here’s what it takes care of for you:

---

### **1. Choosing an IP Address**
Without `AI_PASSIVE`, you would have to manually decide:
- Should the server bind to a **specific interface IP** or use a **wildcard address** (`INADDR_ANY`)?
- If using IPv6, should it bind to **`IN6ADDR_ANY_INIT`**?

This involves:
- Setting up the **`sin_addr`** field in a `sockaddr_in` structure for IPv4 (or `sin6_addr` for IPv6).
- Deciding between wildcard or loopback addresses.

With `AI_PASSIVE` and `host = NULL`:
- **IPv4:** It automatically sets the IP to `INADDR_ANY`.
- **IPv6:** It sets it to `IN6ADDR_ANY_INIT`.

This ensures the server can listen on **all interfaces** without you manually specifying this detail.

---

### **2. IP Version (IPv4/IPv6)**
When you manually set up a socket, you need to decide:
- Will it use **IPv4** (set `sin_family = AF_INET`) or **IPv6** (set `sin_family = AF_INET6`)?

With `AI_PASSIVE`, you can:
- Set `ai_family = AF_UNSPEC` to let `getaddrinfo()` determine the correct IP version based on your system's capabilities.
- Avoid hardcoding IPv4 or IPv6.

---

### **3. Structure Population**
Here’s the data `AI_PASSIVE` fills in for you:
- **`sin_family / sin6_family`:** Automatically set to `AF_INET` or `AF_INET6`.
- **`sin_addr / sin6_addr`:** Set to `INADDR_ANY` or `IN6ADDR_ANY_INIT` for wildcard binding.
- **`sin_port / sin6_port`:** Converts the provided port (e.g., "8080") to network byte order.

Without `getaddrinfo()`:
- You would need to manually set each field:
  ```c
  struct sockaddr_in addr;
  memset(&addr, 0, sizeof(addr));
  addr.sin_family = AF_INET;
  addr.sin_addr.s_addr = htonl(INADDR_ANY); // Wildcard address
  addr.sin_port = htons(8080);             // Convert port to network byte order
  ```

---

### **4. Dual-Stack Compatibility**
- If you want your server to support both IPv4 and IPv6, you would need extra logic to handle:
  - Binding to `INADDR_ANY` for IPv4.
  - Binding to `IN6ADDR_ANY_INIT` for IPv6.

With `AI_PASSIVE`, you just specify `AF_UNSPEC` in the `hints` structure, and `getaddrinfo()` will automatically handle this for you.

---

### **What Does `AI_PASSIVE` Save You From?**
- Writing manual code to handle **wildcard addresses** (`INADDR_ANY`/`IN6ADDR_ANY_INIT`).
- Managing the choice between **IPv4 and IPv6**.
- Populating `sockaddr` structures and converting ports/IPs to the correct format.
- Dealing with **platform-specific quirks**.

If you want to bind a server on a specific port **without caring about other details**, `AI_PASSIVE` saves you the hassle of setting up everything manually. However, for simple applications, manually setting `sin_addr` and `sin_family` for IPv4 (or IPv6) is still doable if you prefer control over convenience.