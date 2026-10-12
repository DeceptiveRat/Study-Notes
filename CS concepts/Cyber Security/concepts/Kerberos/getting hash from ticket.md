That’s an excellent question — you’ve spotted the subtle part that trips up a lot of people. Let’s unpack it carefully.

---

### 🔑 First important detail

When people say *“the ticket is encrypted with the hash”*, they don’t mean the hash itself is sitting somewhere inside the ticket.

They mean:

* The KDC takes the service account’s **password hash** (e.g., NTLM hash).
* It uses that hash as a **key** to encrypt part of the ticket (the service session key).
* The service (like SQL, IIS, etc.) can later decrypt it, because it *knows its own password* (so it can derive the same hash).

So:

* You don’t get the hash directly.
* You get something that has been **encrypted using the hash as the key**.

---

### 🔑 What the attacker sees

* When you dump the service ticket (using Rubeus, Mimikatz, Impacket, etc.), you get a **blob of ciphertext**.
* That blob corresponds to “some data encrypted with the service account’s password hash as the key.”

It looks like this when formatted for cracking (example Kerberoast hash):

```
$krb5tgs$23$*user$realm$service*...$ciphertext
```

---

### 🔑 How cracking works then

* You have the ciphertext.
* You don’t know the key (the service account’s hash).
* But you can try guessing the password → hash it → use that hash to try decrypting/validating the ciphertext.
* If it works (i.e., decryption produces a valid structure or checksum), then you’ve found the right password.

So cracking tools like Hashcat don’t need the original hash. They simulate:

1. Take a guess password.
2. Compute its hash (the candidate key).
3. Try to decrypt the captured ticket with it.
4. If the decryption is valid → bingo, cracked.

---

### ✅ Analogy

Imagine a locked box:

* The lock is keyed to a secret number (the password hash).
* You don’t know the number.
* But you have the box (ciphertext).
* You keep trying numbers until the box opens cleanly.

You never had the key itself — you brute-forced it by testing candidate passwords.

---

👉 So to answer your exact concern:

* We don’t “get” the hash out of the ticket.
* Instead, we brute-force passwords, hash them, and test whether that hash (as a key) can correctly decrypt the ticket.
* When it succeeds, we’ve discovered the real password.

---

Would it help if I walk you through a **step-by-step example with a toy hash/encryption**, showing how the ciphertext is used to check guesses? That way you can see exactly where the validation comes from.
