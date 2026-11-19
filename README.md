
# Urban Style BD — AI Customer Support & Lead Generation Agent

An end-to-end automated AI customer support agent built for **Urban Style BD** (an e-commerce clothing brand in Bangladesh). The agent answers product and delivery queries using a custom Knowledge Base and automatically escalates unresolved customer issues to a human support team by capturing and logging leads into Google Sheets in real time.

---

## System Architecture

```text
Customer Query
      │
      ▼
┌───────────────────┐
│  Voiceflow Agent  │ ──► Answers FAQs via Knowledge Base
└─────────┬─────────┘
          │ (Unresolved / Human Support Requested)
          ▼
┌───────────────────┐
│  save_lead Tool   │ ──► Extracts Name, Email & Issue (JSON POST)
└─────────┬─────────┘
          │
          ▼
┌───────────────────┐
│ Make.com Webhook  │ ──► Receives & parses structured payload
└─────────┬─────────┘
          │
          ▼
┌───────────────────┐
│   Google Sheets   │ ──► Logs lead row in "Urban Style Leads"
└───────────────────┘
Key Features
Knowledge-Grounded Responses: Strictly answers shipping, delivery charges (e.g., outside Dhaka rates), and store policy questions from the configured Knowledge Base without hallucinating.
Autonomous Lead Capture (save_lead): Detects when a customer needs human intervention, collects their Full Name, Email Address, and Issue, and triggers a custom API tool.
Real-Time Webhook Automation: Integrates Voiceflow with Make.com via a POST webhook to process incoming JSON payloads instantaneously.
Automated CRM Logging: Appends structured customer tickets directly into the Urban Style Leads Google Sheet for immediate follow-up by the support team.
Tech Stack
Conversational AI & Agent Logic: Voiceflow (Voiceflow Core 4.2)
Workflow Automation & API Routing: Make.com (Custom Webhooks)
Database / Lead Tracker: Google Sheets
Project Files Included
README.md — Project documentation, system architecture, and setup guide
.vf Project File — Exported Voiceflow agent configuration (v1.0.0)
blueprint.json — Exported Make.com Webhook-to-Google-Sheets automation scenario
Screenshots — Live execution proofs showing save_lead tool call, active Make.com scenario, and automated Google Sheets lead entry
How to Import & Run
1. Voiceflow Setup:
Import the .vf project file into a Voiceflow workspace.
Open Tools → save_lead and replace the Webhook URL with your active Make.com webhook endpoint.
Publish the agent (v1.0.0) or test directly in the Run panel.
2. Make.com & Google Sheets Setup:
Create a Google Sheet named Urban Style Leads with column headers: Name, Email, Issue.
Import blueprint.json into a new Make.com scenario, connect your Google account, map the webhook fields (name, email, issue) to Sheet1, and toggle the scenario to Active.
Author
Raufun Hasan
GitHub:[@raufunhasan78-create](https://github.com/raufunhasan78-create) • Focused on Artificial Intelligence, Data Science & Workflow Automation
