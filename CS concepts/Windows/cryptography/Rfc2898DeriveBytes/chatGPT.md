Excellent questions! You're touching on important internals of how PBKDF2 and `Rfc2898DeriveBytes` work. Let's walk through it clearly.

---

### 🔁 Short Answer:
Yes — if you call `.GetBytes(n)` multiple times **on the same instance**, each call gives you a **different** chunk of derived bytes, continuing from where the previous one left off.

```csharp
var kdf = new Rfc2898DeriveBytes(passwordBytes, salt, 1000);
byte[] first = kdf.GetBytes(16); // gets bytes 0-15
byte[] second = kdf.GetBytes(16); // gets bytes 16-31
```

They **do not** return the same bytes — they are part of a single derived key stream.

---

### ⚙️ How does `Rfc2898DeriveBytes` work internally?

1. **PBKDF2 uses HMAC (e.g., HMAC-SHA1) as a building block.**
2. It **repeatedly hashes** the password and salt in a deterministic way.
3. It produces a **key stream**, made up of "blocks" (`T1`, `T2`, `T3`, etc.).
   - Each block is derived using:
     ```
     T_i = F(password, salt, iterations, i)
     ```
     where `i` is the block index (1-based).

4. **`GetBytes(n)`** collects the necessary number of bytes by computing as many blocks as needed.

   Example: If you're asking for 48 bytes, and the HMAC output is 20 bytes, it will generate 3 blocks (`T1`, `T2`, `T3`) and use the first 48 bytes from them.

---

### 🧠 What is stored inside the object?
The `Rfc2898DeriveBytes` object stores internal state to keep track of:
- The password and salt
- The iteration count
- The HMAC function (usually HMAC-SHA1)
- The current block index (`i`)
- A buffer of the last block generated
- An internal counter to track how many bytes have been returned

So, when you call `.GetBytes()`, it:
- Checks if it needs to generate a new block
- Calculates the next block using the PBKDF2 formula
- Updates its internal state
- Returns the next chunk of derived bytes

---

### 🔄 Want the same result on repeated calls?
If you want to generate the **same** bytes again, you need to **create a new instance** of `Rfc2898DeriveBytes` with the same inputs. Its internal state will reset, and `GetBytes()` will return the same sequence.

```csharp
var kdf1 = new Rfc2898DeriveBytes(passwordBytes, salt, 1000);
var a = kdf1.GetBytes(16);

var kdf2 = new Rfc2898DeriveBytes(passwordBytes, salt, 1000);
var b = kdf2.GetBytes(16); // a and b are identical
```

---

Would you like a code example showing block generation or how HMAC is used in PBKDF2?