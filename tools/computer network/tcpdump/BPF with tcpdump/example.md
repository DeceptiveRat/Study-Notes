Great question! This is a powerful `tcpdump` command used to capture **HTTP GET requests** by filtering raw TCP packet payloads.

Let's break it down part by part:

---

### ✅ Full command:

```bash
tcpdump -i <system_interface> -s 0 -A 'tcp[((tcp[12:1] & 0xf0) >> 2):4] = 0x47455420'
```

---

## 🔹 Part 1: General options

### `tcpdump -i <system_interface>`

* `-i <system_interface>`: Listen on the given network interface (e.g., `eth0`, `wlan0`).

### `-s 0`

* Sets the **snapshot length** to 0 (unlimited). This tells `tcpdump` to capture the **entire packet**, not just the first 96 bytes (which is default on some systems).

### `-A`

* Print packet contents in **ASCII** format (so we can read things like HTTP methods).

---

## 🔹 Part 2: The filter

```bash
'tcp[((tcp[12:1] & 0xf0) >> 2):4] = 0x47455420'
```

This is a **BPF (Berkeley Packet Filter)** expression that matches only packets whose TCP payload starts with `"GET "` (HTTP GET request).

Let’s go step by step:

---

### ✅ Inner part: `tcp[12:1] & 0xf0`

* `tcp[12:1]`: This reads **1 byte** at offset **12** of the TCP header.
* Byte 12 of the TCP header contains:

  * **Data Offset** (high nibble)
  * **Reserved bits** and **flags** (low nibble)
* The **Data Offset** (first 4 bits of byte 12) tells us where the payload begins. It's in **32-bit words** (4 bytes).

So:

```c
(tcp[12] & 0xf0) >> 4   = data offset (in 32-bit words)
(tcp[12] & 0xf0) >> 2   = data offset in bytes
```

**Why `>> 2` instead of `>> 4`?**
Because we want to calculate the **byte offset** from the beginning of the TCP header. Since the value is in 4-byte words, `>> 2` is equivalent to multiplying by 4.

So, the full part:

```c
tcp[((tcp[12:1] & 0xf0) >> 2):4]
```

Reads **4 bytes** from the start of the **TCP payload** (i.e., after the TCP header).

---

### ✅ What is `0x47455420`?

This is the hex representation of the ASCII string:

```
'G' 'E' 'T' ' '  →  0x47 0x45 0x54 0x20
```

So this expression matches:

```c
if the first 4 bytes of the TCP payload == "GET "
```

---

## ✅ Putting it all together

This command:

```bash
tcpdump -i <interface> -s 0 -A 'tcp[((tcp[12:1] & 0xf0) >> 2):4] = 0x47455420'
```

**Means**:

> Capture all TCP packets where the payload starts with **"GET "**, i.e., HTTP GET requests. Print the full ASCII content for inspection.

---

## 🧠 Bonus: Want to match POST?

Just change `0x47455420` to:

```bash
0x504f5354  # "POST"
```

Or use:

```bash
tcpdump -i <interface> -s 0 -A 'tcp[((tcp[12:1] & 0xf0) >> 2):4] = 0x504f5354'
```

---

Let me know if you want a version that matches **any HTTP method** or how to modify it for other purposes (e.g., filtering by host or URI).
