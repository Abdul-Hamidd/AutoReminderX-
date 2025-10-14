AutoReminderX

An Intelligent Multi-Agent Reminder Automation System using LangGraph Shared State

🚀 Overview

AutoReminderX is an advanced AI-driven multi-agent system designed to automate event management tasks using LangGraph’s Shared State mechanism.
Instead of using direct A2A (Agent-to-Agent) communication, this project utilizes a shared memory graph to allow agents to collaborate through a common GraphState — ensuring smooth data flow and intelligent coordination.

The system intelligently connects with Google Calendar and Gmail, enabling it to:
1️⃣ Fetch and analyze events from Google Calendar
2️⃣ Generate event reminder drafts
3️⃣ Automatically send reminder emails to all participants

🧩 Agent System Architecture
🧠 Agents Overview
Agent	Function	Description
Agent 1	📅 Event Reader	Fetches and analyzes Google Calendar events using the Calendar API
Agent 2	🧾 Reminder Drafter	Prepares a personalized reminder draft for each event
Agent 3	📧 Reminder Sender	Sends reminder emails automatically via Gmail API
🔄 Data Flow
Google Calendar
      ↓
Event Reader Agent (fetch + analyze)
      ↓
Reminder Drafter Agent (generate draft)
      ↓
Reminder Sender Agent (send email)
      ↓
Gmail


🧩 Key Implementation Detail:
All agents communicate indirectly using LangGraph’s Shared State (GraphState), not through direct A2A messaging.
Each agent reads, updates, and passes relevant data fields within this shared memory — ensuring clean modularity and controlled data flow.

⚙️ Features

✅ Automatic event fetching from Google Calendar
✅ Smart event data analysis
✅ AI-generated personalized reminder drafts
✅ Automatic email delivery via Gmail API
✅ Built using LangGraph’s shared state (not direct A2A)
✅ Secure OAuth-based Google authentication

🧠 Technologies Used

Python 3.11x

LangGraph Framework

LangChain Core

Google Calendar API

Gmail API

Google API Client Library

Pickle (for token handling)

🔑 Prerequisites

Before running the project:

Enable both Google Calendar API and Gmail API in Google Cloud Console
.

Download your OAuth credentials (credentials.json).

Authenticate once manually to generate token.pkl.

🛠️ Installation & Setup
1️⃣ Clone the Repository
git clone https://github.com/Abdul-Hamidd/AutoReminderX-
cd AutoReminderX

2️⃣ Install Dependencies
pip install -r requirements.txt

3️⃣ Add Credentials

Place credentials.json and token.pkl in the project root.

4️⃣ Run the System
building.ipynb

💡 How It Works

Agent 1 reads and analyzes upcoming calendar events.

Agent 2 uses that shared data to generate reminder drafts.

Agent 3 reads the final draft and sends reminders through Gmail.

All agents share one GraphState object, which acts as the central memory hub for the system.

🧠 Example Output

Console Log Example:

Fetching events from Google Calendar...
Event: Project Review Meeting
Summary generated successfully.
Reminder draft prepared.
Reminder email sent to all attendees.


Email Example:

Subject: Reminder – Project Review Meeting Tomorrow  
Body: Hello Team,  
This is a quick reminder about tomorrow’s Project Review Meeting at 11:00 AM.  
See you all there!

🌐 Future Enhancements

🔹 Automate daily reminder execution using Cloud Scheduler, AWS Lambda, or Cron Jobs
🔹 Add dashboard for visual monitoring of reminders and logs
🔹 Integrate voice or chat-based command interface

🧩 Example Use Case

Imagine you’re managing multiple projects and meetings.
Instead of manually checking Google Calendar and emailing participants,
AutoReminderX handles everything — automatically fetching events, summarizing them, and sending smart reminders on time.

🏁 Project Status

✅ Ready for Showcase & GitHub Upload
🔜 Next Step: Integration & Deployment for automatic daily reminder scheduling

🧑‍💻 Author

Abdul Hamid
AI Engineer | Machine Learning Developer
📍 Pakistan
📫 LinkedIn: https://linkedin.com/in/abdul-hamid786

⭐ Stay Tuned

You can explore the full implementation of this system in my GitHub repository:
Stay tuned — you can see the implementation of this code in my repository soon.
