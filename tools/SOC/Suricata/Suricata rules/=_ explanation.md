Excellent question — and this is exactly what makes `=>` a bit subtle.

Let’s go step by step.

---

### ⚙️ What happens under the hood

When you write a Suricata rule with

```
any any => any 80
```

you’re telling Suricata:

> “This rule applies to **sessions** that involve these endpoints, and it may match traffic in **either direction**, but I still care about which packets are client→server and which are server→client.”

So even though the signature’s “arrow” points **from client to server**, the **`=>` operator makes Suricata track both sides** of the TCP connection.

Suricata’s flow engine knows which packets belong to the **client side** and which belong to the **server side**.
This is why you can use keywords like:

* `flow:to_server` → match only packets in that direction
* `flow:to_client` → match only packets in the opposite direction

Both keywords are evaluated **within the same connection**.

---

### 🧠 In simpler terms

* With `->`, Suricata **only** evaluates traffic that matches the literal source→destination direction in the rule.
* With `=>`, Suricata evaluates **both directions of the connection**, but applies your **directional keywords** properly depending on whether the packet is from client or server.

---

### 📊 Example

Rule:

```suricata
alert tcp any any => any 80 (
    msg:"HTTP GET or 200 OK";
    flow:established;
    content:"GET"; flow:to_server;
    content:"200 OK"; flow:to_client;
)
```

Traffic:

```
Client (10.0.0.5) → Server (10.0.0.10:80): "GET /index.html"
Server (10.0.0.10:80) → Client (10.0.0.5): "HTTP/1.1 200 OK"
```

**How Suricata handles this:**

* The connection (flow) is tracked bidirectionally because of `=>`.
* When it sees the client packet, it checks the `flow:to_server` condition (`"GET"`).
* When it sees the server packet, it checks the `flow:to_client` condition (`"200 OK"`).
* Both can match in the same flow, even though only one arrow (`=>`) is written.

---

### ✅ So the key idea:

> `=>` doesn’t flip the packet direction — it tells Suricata to evaluate **both sides of the flow** as part of the same connection, respecting directionality internally.

That’s why a response from the server → client can still match, even though the written direction looks like client → server.
