# 🤖 AutoReminderX: Enterprise Multi-Agent Event Automation Engine via LangGraph Shared State

AutoReminderX is a production-grade, **AI-driven multi-agent orchestration system** designed to automate end-to-end event management, monitoring, and communication pipelines. 

Unlike traditional point-to-point Agent-to-Agent (A2A) tightly coupled architectures, this system leverages **LangGraph’s centralized Shared State (GraphState) mechanism**. This ensures decoupled agent interaction, deterministic state transitions, and a clean reactive memory hub as data flows from Google Calendar to automated Gmail dispatch layers.

---

## 🧠 System Architecture & Decoupled State Flow

Instead of passing heavy payloads directly between isolated agents, each autonomous worker reads from, computes, and writes back into a single structured, thread-safe `GraphState`.

     ┌────────────────────────────────────────────────────────┐
     │              Centralized GraphState (Memory Hub)        │
     │  - raw_events []  - custom_drafts []  - status_flags   │
     └───────────▲────────────────────▲────────────────────▲────┘
                 │                    │                    │
    (Read/Write) │       (Read/Write) │       (Read/Write) │
                 ▼                    ▼                    ▼
┌───────────────────┐        ┌───────────────────┐        ┌───────────────────┐
│  Event Reader     │        │ Reminder Drafter  │        │  Reminder Sender  │
│  Agent (Worker 1) │        │  Agent (Worker 2) │        │  Agent (Worker 3) │
└─────────▲─────────┘        └───────────────────┘        └─────────┬─────────┘
│ (API Ingestion)                                         │ (MIME Dispatch)
┌─────────┴─────────┐                                     ┌─────────▼─────────┐
│  Google Calendar  │                                     │     Gmail API     │
└───────────────────┘                                     └───────────────────┘


### 🧩 Autonomous Agent Breakdown

| Agent Name | Core Subsystem | State Responsibility | Functional Description |
| :--- | :--- | :--- | :--- |
| **Agent 1: Event Reader** | Google Calendar API v3 | Pulls localized temporal events, extracts attendee metadata, and updates `state["raw_events"]`. | Queries structural calendar registries, filters time windows, and cleans dirty payload inputs. |
| **Agent 2: Reminder Drafter** | LangChain GenAI Layer | Reads `state["raw_events"]`, runs contextual LLM prompting, and writes to `state["custom_drafts"]`. | Synthesizes personalized, high-context email bodies customized to the specific meeting agenda. |
| **Agent 3: Reminder Sender** | Google Gmail API Gateway | Monitors `state["custom_drafts"]`, builds MIME attachments, and updates transaction log arrays. | Asynchronously dispatches verified drafts to all extracted attendee email strings. |

---

## ⚙️ Core Enterprise Technical Features

* **State-Driven Multi-Agent Design:** Engineered entirely on top of LangGraph to handle deterministic cyclic or acyclic loops without breaking workflow state.
* **Granular OAuth Security Matrix:** Utilizes secure tokenized pickle wrappers and explicit Google Cloud OAuth consent scopes to protect enterprise calendars and message relays.
* **Contextual Prompt Synthesis:** Integrated with state-of-the-art LLM layers via LangChain to dynamically adjust email communication tone based on event types (e.g., internal syncs vs. client reviews).
* **Robust Multi-Attendee Parsing:** Automatically parses nested JSON structures from calendar objects to guarantee zero communication gaps across distributed project teams.

---

## 🛠️ Infrastructure & Tech Stack

* **Workflow Orchestration:** LangGraph, LangChain Core (Expression Language - LCEL)
* **Underlying Foundations:** Python 3.11+
* **External Core Gateways:** Google Calendar API, Gmail API
* **Security & Tokens:** Google API Client Libraries, Secure Pickle File Handlers

---

## 🚀 Workspace Setup & Installation

### 1. Repository Provisioning
```bash
git clone [https://github.com/Abdul-Hamidd/AutoReminderX-.git](https://github.com/Abdul-Hamidd/AutoReminderX-.git)
cd AutoReminderX-
2. Dependency Resolution
Bash
pip install -r requirements.txt
3. API Authentication Configuration
Initialize a developer project on the Google Cloud Console.

Enable both the Google Calendar API and the Gmail API inside the API Library.

Configure your OAuth Consent Screen, generate Desktop App OAuth credentials, and download the payload as credentials.json.

Drop credentials.json directly into the root workspace folder. On the first localized execution, a secure login window will pop up to produce the persistent token.pkl.

▶️ Operational Execution
To boot up the complete multi-agent graph pipeline and process the current temporal queue:

Bash
python main.py
(Note: If utilizing the notebook architecture for step-by-step state verification, launch and execute all cells within building.ipynb)

🧪 Output Blueprints & Monitoring
Local Runtime Pipeline Logs:
Plaintext
[INFO] Bootstrapping GraphState Engine...
[WORKER 1] Polling Google Calendar Registry... Found Event: "Q3 Engineering Sync"
[WORKER 1] State updated with 1 active event context.
[WORKER 2] Invoking LangChain LLM Engine... Contextual draft successfully materialized.
[WORKER 3] Constructing secure MIME relay object...
[WORKER 3] Transmission successful. Notification dispatched to 6 verified attendees.
[INFO] Graph Workflow reached terminal node. Execution terminated successfully.
Dispatched Notification Sample:
Plaintext
Subject: Urgent Reminder: Q3 Engineering Sync — Tomorrow at 11:00 AM PST
Body: 
Hello Team,

This is an automated operational sync reminder for the "Q3 Engineering Sync" scheduled for tomorrow at 11:00 AM PST. 

Please ensure all core sprint dashboards are fully updated prior to the call.

Best Regards,
Autonomous Operations Assistant
🌟 Strategic Project Roadmap
[ ] Integrate AWS Lambda / EventBridge Cloud Schedulers for hands-free serverless daily cron executions.

[ ] Develop a Streamlit/React Monitoring Board to trace real-time GraphState data maps visually.

[ ] Build fallback exception edges to handle API throttling or expired OAuth tokens gracefully.

👨‍💻 Developer Architecture Profile
ABDUL HAMID AI/ML & GenAI Engineer linkedin.com/in/abdul-hamid786 | wellfound.com/u/abdul-hamid-29 | https://www.kaggle.com/hamidai

Give this repository a star ⭐ if you find this decentralized shared-state architecture helpful for your multi-agent production frameworks!
