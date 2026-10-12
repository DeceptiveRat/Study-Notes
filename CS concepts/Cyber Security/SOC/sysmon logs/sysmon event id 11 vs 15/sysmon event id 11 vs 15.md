Great question — `Sysmon Event ID 11` and `Event ID 15` **both relate to file creation**, but they focus on different *levels* of file system activity. Here's the difference:

---

### 🔹 **Sysmon Event ID 11 – FileCreate**

* **What it logs:**
  When a **file is created or overwritten** on disk.
* **Triggered by:**
  Any standard file creation (e.g., creating a new `.exe`, `.txt`, etc.).
* **Fields include:**

  * File name
  * Creation UTC time
  * Process ID / Image
  * User

📝 **Use case:**
Useful for monitoring suspicious files being written to disk (e.g., malware dropping payloads, persistence artifacts, logs, temp files).

---

### 🔹 **Sysmon Event ID 15 – FileCreateStreamHash**

* **What it logs:**
  When an **alternate data stream (ADS)** is created in a file.
* **Triggered by:**
  Creation of NTFS **streams** (e.g., `file.txt:malicious.exe`).
* **Fields include:**

  * File name
  * Stream name
  * Hash of the stream content
  * Process info

📝 **Use case:**
Critical for detecting **living off the land** techniques, stealthy malware, or fileless attacks using ADS for hiding code or payloads.

---

### 🧠 What are Alternate Data Streams (ADS)?

They're a **feature of NTFS** that allows data to be stored *alongside* the main file content but **invisibly** to most tools.
Example:

```bash
notepad evil.txt:payload.exe
```

Creates a hidden stream called `payload.exe` inside `evil.txt`. Traditional antivirus or file listings often miss this.

---

### ✅ Summary Table

| Event ID | Name                 | Logs...                      | Use Case                            |
| -------- | -------------------- | ---------------------------- | ----------------------------------- |
| 11       | FileCreate           | Normal file creation         | Detect malware writing to disk      |
| 15       | FileCreateStreamHash | Creation of NTFS ADS streams | Detect hidden/stealthy file storage |

---

If you're monitoring for attacks, **Event ID 15** is especially powerful for catching advanced or stealthy threats that hide in ADS.
Let me know if you want example logs or detection rules.
