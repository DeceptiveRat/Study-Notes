That's a great observation — and the author's behavior **actually makes a lot of sense from a threat hunting perspective**, even if there’s no explicit mention of alternate data streams (ADS). Here's why:

---

### 🧩 Why use both **Event ID 15** and **Event ID 11** for the *same file*?

Even if there’s no *visible* reference to a stream like `invoice.one:streamname`, the presence of an Event ID 15 **suggests a file stream was created**, possibly **in addition to** a regular file write (Event ID 11).

Here's why corroboration is important:

---

### ✅ **Reasons the hunter checks Event ID 11 after seeing Event ID 15**

1. ### 🔍 **Corroboration of file existence**

   * **Event ID 15** tells you that an **ADS was written** (e.g., suspicious data hidden in a stream).
   * But ADS can’t exist *without* a host file. So they check **Event ID 11** to confirm:

     * Was `invoice.one` also *created as a file*?
     * Which process did it?
     * Was it tampered with?

2. ### 🧠 **Building context for the investigation**

   * Event ID 11 gives more details about:

     * The **file creation process** (e.g., `powershell.exe`, `wscript.exe`, etc.)
     * **Parent-child process chains**
     * **File path**
     * Creation time
   * All of this helps confirm **how** and **why** the file got there.

3. ### 🪓 **It might not *look* like a stream — but it is**

   * Malware authors often use **file names** like `invoice.one` or `invoice.pdf.exe` to **trick the user or analyst**.
   * A file like `invoice.one` might be just a **weird file** — or it might **contain a stream** or be **used as a container** for malicious content.
   * Event ID 15 logging is sometimes triggered even if the stream has a **null or unnamed** stream (`:$DATA` is the default stream).

4. ### 🔐 **Not all Event ID 15 entries are obvious**

   * You can get an Event ID 15 entry even **without a visible stream name**, especially in compressed or encrypted file operations, or tools writing via stream APIs.

---

### 🧪 Example Scenario

Imagine malware drops `invoice.one`:

* Event ID 15 logs:
  - A stream is written to `invoice.one` (could be shellcode, config, payload).

* Hunter checks Event ID 11:
  - Sees that the same file was created 10 seconds earlier by `powershell.exe`, from a suspicious script.

Together, these events confirm:

* When and how the file was created,
* Who did it,
* That it was then modified with a stream (potential payload or obfuscation).

---

### 📌 TL;DR

The author used **Event ID 11** after **Event ID 15** to:

* **Corroborate the file was actually created** and not just written to as a stream.
* **Build a clearer picture** of the process and timeline.
* **Confirm the file wasn't already present or created by another benign process.**

Even if `invoice.one` doesn't *look* like it uses ADS, Event ID 15 tells you a **non-default stream write** occurred. So checking Event ID 11 helps ensure it's **not a false positive** or to **track initial creation.**

---

Let me know if you want to test this out or write a detection rule!
