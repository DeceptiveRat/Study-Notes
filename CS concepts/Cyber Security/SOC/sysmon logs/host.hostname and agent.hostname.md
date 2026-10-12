Great question — and an important one for anyone using the Elastic Stack for threat detection or observability.

In short:

| Field            | Description                                                        |
| ---------------- | ------------------------------------------------------------------ |
| `host.hostname`  | The **actual hostname of the system** being monitored/logged.      |
| `agent.hostname` | The **hostname of the system where the Elastic Agent is running**. |

They are **often the same**, but not always. Here's the full breakdown:

---

## 🔹 `host.hostname`

* Comes from the **monitored endpoint** (e.g., a Windows machine, Linux server).
* This is the **real system name** reported by the OS.
* Used to identify the **device** that the logs or telemetry originate from.
* Populated by the agent or Beats based on the host's settings.

### ✅ Example:

If you're collecting logs from `server123.company.local`, this will be:

```json
"host.hostname": "server123"
```

---

## 🔹 `agent.hostname`

* Refers to the **system on which the Elastic Agent or Beat itself is running**.
* In most cases, the agent is installed on the same system it collects logs from — so these fields **match**.
* But in some setups (like centralized logging or containerized environments), they **can differ**.

### ✅ Example:

If you deploy Filebeat in a container or gateway system to collect logs from other systems, you might see:

```json
"agent.hostname": "log-collector01"
"host.hostname": "webserver01"
```

---

## 🧠 When are they different?

| Situation                                 | `host.hostname` | `agent.hostname` |
| ----------------------------------------- | --------------- | ---------------- |
| Normal endpoint monitoring (default case) | `desktop123`    | `desktop123`     |
| Centralized agent collecting remote logs  | `appserver01`   | `logforwarder01` |
| Agent in container on host                | `container123`  | `host123`        |

---

## 🔍 Why this matters

* **In security hunting**: You should **group by `host.hostname`** to track endpoint activity.
* **In agent management**: You might want to track or troubleshoot by `agent.hostname` (e.g., to find broken or overloaded agents).
* **In misconfigured setups**: Seeing different values helps catch misrouted data or improperly tagged sources.

---

### ✅ TL;DR

| Field            | What it refers to                               |
| ---------------- | ----------------------------------------------- |
| `host.hostname`  | The name of the system where the event happened |
| `agent.hostname` | The name of the system where the agent runs     |

In most simple setups, they are identical — but **in complex or containerized environments, they can differ**, and it’s important to track both.

Let me know if you'd like help designing dashboards or filters based on this!
