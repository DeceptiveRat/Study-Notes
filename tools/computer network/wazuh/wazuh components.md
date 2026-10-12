Wazuh is a powerful open-source security monitoring platform that integrates various components to provide capabilities like threat detection, compliance monitoring, log analysis, and more. Here's a breakdown of the **main Wazuh components** and **how they interact**:

---

## 🧩 **Wazuh Components Overview**

### 1. **Wazuh Agent**

* **Installed on:** Endpoints (servers, workstations, etc.)
* **Purpose:**

  * Collects logs, monitors file integrity, detects rootkits, runs security policies.
  * Sends collected data to the Wazuh Server/Manager.
* **Lightweight and secure**, with support for Linux, Windows, macOS.

---

### 2. **Wazuh Manager (Server)**

* **Installed on:** A centralized server.
* **Purpose:**

  * Receives, processes, and analyzes data from agents.
  * Applies detection rules and decoders.
  * Generates alerts (stored in `/var/ossec/logs/alerts/alerts.json`).
* **Also handles:**

  * Agent management (registration, configuration).
  * Correlation and rule matching.

---

### 3. **Elastic Stack (formerly ELK)**

> Often used *with* Wazuh, but not a core component unless visualization/log management is needed.

#### a. **Elasticsearch**

* **Purpose:** Stores alerts and log data.
* **Allows:** Searching, filtering, and analysis of large volumes of data.

#### b. **Logstash** *(optional in newer setups)*

* **Purpose:** Used for processing logs before they go into Elasticsearch.
* **Can be replaced by:** Wazuh's internal data forwarding if Logstash is not used.

#### c. **Kibana (with Wazuh App/Plugin)**

* **Purpose:** Visualizes data stored in Elasticsearch.
* **Wazuh App** provides dashboards for alerts, rules, PCI DSS compliance, etc.

---

### 4. **Wazuh Indexer (alternative to Elasticsearch)**

* Part of the newer Wazuh architecture.
* It replaces Elasticsearch in self-managed Wazuh deployments (Wazuh 4.x+).
* **Purpose:** Stores and indexes alert and event data.

---

### 5. **Wazuh Dashboard**

* Replaces Kibana in the modern Wazuh stack (Wazuh 4.x+).
* Web interface to visualize and manage security data.
* Built specifically for Wazuh, without needing Kibana plugins.

---

## 🔁 **How the Components Interact**

```
[Agent(s)] --> [Wazuh Manager] --> [Wazuh Indexer / Elasticsearch] --> [Wazuh Dashboard / Kibana]
```

### Data Flow:

1. **Agent collects data** (e.g., file changes, system logs).
2. **Sends to the Wazuh Manager** securely via encrypted communication.
3. **Manager decodes and analyzes** the data using rules, and generates alerts if necessary.
4. **Forwards alerts to the Indexer/Elasticsearch**, which stores and indexes the data.
5. **Dashboard/Kibana** queries the index to show alerts, stats, dashboards.

---

## 🛠️ Optional Components

* **Filebeat**: For forwarding logs to Logstash or Elasticsearch (used in some setups).
* **Active Responses**: Wazuh can trigger automated responses (e.g., block IP, kill process).
* **Syscollector**: Inventory collection tool integrated with the agent (hardware/software details).

---

## 🧠 Summary Table

| Component       | Role                       | Runs On        | Communicates With  |
| --------------- | -------------------------- | -------------- | ------------------ |
| Wazuh Agent     | Data collection            | Endpoints      | Wazuh Manager      |
| Wazuh Manager   | Analysis, alert generation | Central server | Indexer, Dashboard |
| Wazuh Indexer   | Stores and indexes data    | Central server | Dashboard          |
| Wazuh Dashboard | Visualization, management  | Web UI         | Indexer            |
| Elasticsearch   | (Alt. to Indexer)          | Central server | Kibana             |
| Kibana          | (Legacy UI)                | Web UI         | Elasticsearch      |

---

Let me know if you want diagrams or examples of specific data flow (e.g., alert generation for a file integrity change).
