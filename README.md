# 📊 Weekly Workflow Analytics AI Agent (n8n)

An **automated weekly analytics and reporting system** built using **n8n** that analyzes all workflow executions, aggregates success/error/waiting statistics, calculates runtimes, and sends a **beautiful HTML report** via **Gmail and Outlook**.

This project acts as an **observability + reporting layer for n8n**, helping teams monitor automation health without manually checking execution logs.

---

##  What This Project Does 

1. Runs automatically **every 7 days**
2. Fetches **all workflows** in n8n
3. Fetches **all previous executions**
4. Merges workflows with their executions
5. Filters executions from the **last week only**
6. Aggregates:

   * Error count
   * Success count
   * Waiting count
   * Average runtime
   * Total runtime
7. Generates a **professional HTML report**
8. Sends the report via **Gmail and/or Outlook**

---

## ✨ Features

### 🗓️ Automated Scheduling

* Weekly execution using Schedule Trigger
* Zero manual intervention

### 🔍 Execution Analytics

* Per-workflow execution breakdown
* Status-based aggregation (success / error / waiting)
* Runtime calculations (avg + total)

### 📊 HTML Reporting

* Clean, responsive HTML email
* Summary dashboard (totals)
* Per-workflow detailed table
* Visual status badges

### 📧 Multi-Channel Notifications

* Gmail integration
* Microsoft Outlook integration
* HTML email support

### 🧩 Data Enrichment

* Workflow metadata merged with execution logs
* Accurate mapping using `workflowId`

---

## 🏗️ Architecture Overview

```
Schedule Trigger (Weekly)
        ↓
Get All Workflows ──┐
                    ├─→ Normalize workflowId
Get All Executions ─┘
        ↓
Merge (Workflow + Executions)
        ↓
Filter (Last 7 Days)
        ↓
Aggregate + Runtime Calculations
        ↓
Generate HTML Report
        ↓
Send via Gmail / Outlook
```

---

## 🧰 Tech Stack

| Layer         | Technology               |
| ------------- | ------------------------ |
| Automation    | n8n                      |
| Scheduling    | n8n Schedule Trigger     |
| Data Source   | n8n Internal API         |
| Processing    | JavaScript (Code Node)   |
| Reporting     | HTML + CSS               |
| Notifications | Gmail, Microsoft Outlook |

---

## ⚙️ Setup Instructions

### 1️⃣ Prerequisites

* n8n (self-hosted or cloud)
* Admin access to n8n instance
* Gmail OAuth2 credentials (optional)
* Microsoft Outlook OAuth2 credentials (optional)

---

### 2️⃣ Import Workflow

1. Copy the workflow JSON
2. Open n8n → **Import Workflow**
3. Paste JSON
4. Save the workflow

---

### 3️⃣ Configure Schedule Trigger

* Default: every **7 days**
* Customize interval if needed (daily / monthly)

---

### 4️⃣ Configure Email Nodes

#### Gmail Node

* Enable node (currently disabled by default)
* Configure OAuth2 credentials
* Set recipient email

#### Outlook Node

* Configure Microsoft credentials
* Set recipient email

> ℹ️ You can enable **one or both** email providers.

---

## 🔐 Security Best Practices

* Use n8n credential manager (never hardcode secrets)
* Restrict access to execution APIs
* Limit email recipients (avoid data leakage)
* Use read-only n8n credentials where possible
* Monitor execution time for large instances

---

## 📈 Scalability Considerations

* Handles large workflow counts
* Execution volume dependent on n8n retention
* Can be extended with:

  * Pagination handling
  * Execution status alerts
  * Slack / Teams notifications
  * Persistent metrics storage (DB)

---

## 💡 Use Cases

* Automation health monitoring
* Platform engineering observability
* Weekly ops reports
* SLA tracking
* Failure trend analysis
* Internal DevOps reporting

---

## Author

**Saeedullah Shaikh**
- GitHub: [@Saeedullahshaikh](https://github.com/Saeedullahshaikh)

## License

MIT License
