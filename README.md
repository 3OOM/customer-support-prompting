# FlexTime Customer Support Prompt Engineering Pipeline

## Project Information
- **Student Name:** Abhishek Nikam
- **Assessment:** Customer Support Prompting Assessment (Assessment 3)
- **Repository:** `customer-support-prompting`

---

## Project Overview

This repository delivers a production-grade, multi-stage **Customer Support Prompt Engineering System** built for **FlexTime**, a cloud-based scheduling and workforce management SaaS platform. 

The system implements a robust 5-stage conversational pipeline capable of routing requests, generating policy-compliant empathetic responses, self-auditing against strict financial guardrails (such as a $20 autonomous refund cap), dispatching structured Tier-2 escalation tickets, and formatting CRM operational summaries.

---

## Repository Structure & Deliverables

```
customer-support-prompting/
├── README.md                    # Project overview, Loom video walkthrough, and architecture guide
├── support_prompt_library.md    # The complete 5-stage production prompt library
├── conversations_portfolio.md   # End-to-end execution transcripts for Scenarios A, B, and C
└── chatbot_documentation.md     # Corporate policy manual, system specifications, and Mermaid.js flowchart
```

### Deliverable Manifest

| File | Purpose |
|---|---|
| [`support_prompt_library.md`](support_prompt_library.md) | Fully documented prompt templates for all 5 pipeline stages (Classifier, CARE Responder, Self-Verification Auditor, Escalation Ticket Dispatcher, and CRM Logger). |
| [`conversations_portfolio.md`](conversations_portfolio.md) | Complete multi-turn transcripts for 3 realistic customer scenarios (Email Change, $15 Double Billing, and $120 Renewal Escalation with ticket). |
| [`chatbot_documentation.md`](chatbot_documentation.md) | FlexTime Corporate Policy Manual ($20 refund limit, security rules, PII protection), pipeline architecture, and interactive Mermaid.js diagram. |
| [`README.md`](README.md) | High-level synthesis, setup guide, and public Loom walkthrough link. |

---

## Loom Walkthrough Video

Watch the complete project walkthrough and live execution demonstration here:  
**[Watch the Public Loom Video](YOUR_PUBLIC_LOOM_URL)**

### Walkthrough Outline (3–4 Minutes)
- **0:00–0:45 (Introduction):** Overview of the FlexTime customer support system, 5-stage architecture, and key business constraints ($20 refund cap, PII protection).
- **0:45–1:45 (Prompt Library Tour):** Deep dive into [`support_prompt_library.md`](support_prompt_library.md), explaining the CARE responder framework and the Stage 3 self-verification audit layer.
- **1:45–2:45 (Live ChatGPT Demo - Scenario C):** Live execution in ChatGPT simulating the $120 annual charge dispute, showing the model safely recognizing the $20 ceiling, de-escalating customer distress, and producing an escalation ticket.
- **2:45–3:30 (Portfolio & Documentation Review):** Walkthrough of [`conversations_portfolio.md`](conversations_portfolio.md), the Mermaid.js flowchart in [`chatbot_documentation.md`](chatbot_documentation.md), and final concluding remarks.

---

## The 5-Stage Pipeline Architecture

```
[Customer Inbound] 
        │
        ▼
[Stage 1: Intent & Sentiment Classifier] ──► Extracts intent (5 categories), sentiment (4 tiers), entities
        │
        ▼
[Stage 2: CARE Responder] ───────────────► Crafts warm, policy-grounded response (max 100 words)
        │
        ▼
[Stage 3: Self-Verification Auditor] ────► Audits refund limit ($20 cap), PII masking, tone, and length
        │
    ┌───┴────────────────────────┐
 (Pass)                      (Escalate)
    │                            │
    │                            ▼
    │               [Stage 4: Escalation Ticket] ──► Dispatches structured Tier-2 handover
    │                            │
    ▼                            ▼
[Stage 5: Conversation Summarizer & CRM Logger] ─► Generates CRM summary card & Markdown table
```

---

## Core Corporate Policy Guardrails

1. **Autonomous Refund Ceiling:** The AI agent is authorized to directly refund up to **$20.00 USD**. Any request exceeding $20.00 is strictly barred from autonomous approval and must be escalated to the Senior Finance Team.
2. **Account Security:** Frontline agents and AI systems cannot manually alter registered email addresses. All modifications require an automated verification link sent to the current email on file.
3. **Data Privacy (SOC2 / GDPR):** Full credit card numbers, passwords, and sensitive personal identifiers are strictly forbidden from being ingested or output unmasked.

---

## How to Test and Run the Pipeline

1. Open [`support_prompt_library.md`](support_prompt_library.md).
2. Choose a customer message or use the sample scenarios from [`conversations_portfolio.md`](conversations_portfolio.md).
3. Execute **Stage 1** in ChatGPT ([chatgpt.com](https://chatgpt.com)) to extract intent and sentiment JSON.
4. Pass the extracted data into **Stage 2** to generate the draft response.
5. Pipe the draft into **Stage 3** to verify compliance against the $20 refund cap and privacy rules.
6. If the inquiry exceeds authority limits, execute **Stage 4** to generate the Tier-2 ticket.
7. Run **Stage 5** to log the interaction into the CRM record.
