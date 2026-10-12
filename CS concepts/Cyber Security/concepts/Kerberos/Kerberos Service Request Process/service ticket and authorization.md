Great question — this is a **key confusion point in Kerberos**.

You're right that **any authenticated user with a TGT can request service tickets (TGS tickets)** for *any service registered in AD*. But — **having a service ticket ≠ being authorized to use the service**.

Here’s the breakdown:

---

### 🔑 Step 1: TGT

* When you log in, you authenticate with your password/NT hash/etc.
* The KDC gives you a **Ticket Granting Ticket (TGT)**.
* This proves "I am who I say I am" to the KDC.

---

### 🔑 Step 2: Request Service Ticket

* With the TGT, you can ask the KDC for a **service ticket** for any SPN (like `MSSQLSvc/sql01.domain.com:1433`).
* The KDC does **not** check whether you’re authorized to use the service. It just issues the ticket.
* That’s why tools like **Rubeus** can enumerate/request service tickets for kerberoasting, even if you have no rights to the service.

---

### 🔑 Step 3: Access Attempt

* You then present the **service ticket** to the target service.
* The service will decrypt the ticket with its service account’s key and see who you are.
* The service enforces **authorization** (e.g., “Is this user allowed to connect to SQL?”).
* If not authorized → you get access denied.

---

✅ **So to answer directly:**

* **Yes**: Any user with a TGT can request service tickets to any service.
* **No**: This does *not* mean you can actually *use* the service — authorization is still enforced by the service itself.

---

This distinction (tickets are *easy to get*, but actual access is restricted) is why **kerberoasting works** — attackers don’t need to access the service, just the ticket.

👉 Do you want me to also show you the flow in terms of what happens on the wire (AS-REQ, TGS-REQ, etc.), so it’s crystal clear why this separation exists?
