Using **created pipes** (named pipes / `\\.\pipe\...`) in **Splunk** to detect **malicious behavior** is a powerful detection technique. Named pipes are often used by malware, post-exploitation frameworks (like Cobalt Strike, Metasploit), or LOLBins (like `rundll32`, `wmic`) for **inter-process communication (IPC)** or **command-and-control (C2)**.

Here’s how you can approach it in **Splunk**:

---

## 🧠 Step 1: Understand Pipe Creation Events

### Primary Windows Event:

* **EventCode = 17** (Sysmon): Pipe Created (`Pipe Created`)

  * `EventCode=17` is logged when a named pipe is created.
  * Fields to look at:

    * `PipeName`
    * `Image` (process that created it)
    * `CommandLine`
    * `ParentImage`

Make sure Sysmon is configured with the proper rule group:

```xml
<PipeEvent onmatch="include">
    <PipeCreate />
</PipeEvent>
```

---

## 🛠️ Step 2: Example SPL to Detect Created Pipes

```spl
index=sysmon EventCode=17
| stats count by PipeName, Image, CommandLine, ParentImage
| sort - count
```

This shows the most frequently created pipes, which can help you build a **baseline**.

---

## 🧪 Step 3: Hunt for Suspicious Pipe Names

### Common Suspicious Patterns:

1. Pipes used by known malware or tools:

   * `\\.\pipe\msagent_*` (Cobalt Strike)
   * `\\.\pipe\postex_*`
   * `\\.\pipe\remcom_*`
   * `\\.\pipe\shadow*`
   * Pipes starting with:

     * `\\.\pipe\meterpreter`
     * `\\.\pipe\mypipe`
     * `\\.\pipe\*bot*`

2. Unusual/random names:

   * UUIDs or random strings: `\\.\pipe\{7A1FC2A3-BFAB-4413}`

### SPL Example:

```spl
index=sysmon EventCode=17 PipeName="\\.\pipe\\*"
| eval is_suspicious=if(match(PipeName, "(?i)(cobalt|meterpreter|shadow|remcom|postex|bot|msagent)"), "yes", "no")
| where is_suspicious="yes"
| table _time, Image, CommandLine, PipeName, ParentImage
```

---

## 🧨 Step 4: Correlate with Other Events

To confirm suspicious behavior, **correlate with events from the same process or PID**:

* **Module loads (EventCode=7)** → Look for `clr.dll`, `amsi.dll` (indicates .NET or AV evasion)
* **Network connections (EventCode=3)** → Did the process connect out?
* **Process creation (EventCode=1)** → Parent/child relationship
* **Process access (EventCode=10)** → Is this pipe used in suspicious inter-process access?

Example correlation:

```spl
index=sysmon (EventCode=17 OR EventCode=10 OR EventCode=1 OR EventCode=7)
| stats values(PipeName) as Pipes, values(TargetImage) as TargetProcess, values(Image) as Process by ProcessId
```

---

## 📊 Optional: Use Lookup Table of Known Bad Pipes

Create a lookup like:

**known\_bad\_pipes.csv**

```
pipe_name
\\.\pipe\msagent_
\\.\pipe\meterpreter
\\.\pipe\remcom
\\.\pipe\postex
```

```spl
index=sysmon EventCode=17
| lookup known_bad_pipes.csv pipe_name AS PipeName OUTPUT pipe_name AS found
| where isnotnull(found)
| table _time, Image, PipeName, CommandLine
```

---

## 🚩 Step 5: Build an Alert

After you've built your SPL for suspicious pipe creation, set it as a scheduled alert:

* Trigger condition: `if results > 0`
* Run every 5 or 10 minutes
* Include context: process, parent, and user

---

## ✅ Summary

| Step | Action                                                        |
| ---- | ------------------------------------------------------------- |
| 🔍 1 | Log `EventCode=17` (Sysmon Pipe Creation)                     |
| 📈 2 | Look for pipe names used by malware or tools                  |
| 🔗 3 | Correlate with process creation, module loads, network events |
| 📁 4 | Use lookup tables for known bad pipe names                    |
| 🚨 5 | Create alerts on suspicious pipe creation                     |

---

Let me know if you want help creating detection rules for specific tools like **Cobalt Strike**, **Meterpreter**, or **Remcom** — all of which use pipes heavily.
