# FlexTime Support Conversations Portfolio

This portfolio documents three end-to-end customer support test interactions executed through the 5-stage FlexTime prompt engineering pipeline. Each scenario demonstrates intent classification, policy-grounded empathetic response generation, automated self-verification auditing, escalation management, and CRM logging.

---

## Master Operations Summary Table

| Ticket ID | Customer | Scenario | Intent | Sentiment | AI Decision | Refund Impact | Outcome |
|---|---|---|---|---|---|---|---|
| `FT-88310` | John Doe | Scenario A: Email Change | `ACCOUNT_MANAGEMENT` | `NEUTRAL` | Autonomous Self-Service | $0.00 | Resolved (Security Link Sent) |
| `FT-88311` | Sarah Connor | Scenario B: Double Charge ($15) | `BILLING_REFUND` | `FRUSTRATED` | Autonomous Refund Issued | $15.00 Processed | Resolved by AI |
| `FT-ESC-90812` | Michael Scott | Scenario C: $120 Refund Escalation | `BILLING_REFUND` | `URGENT_ANGRY` | Escalated to Tier-2 | $120.00 Flagged | Handed to Senior Billing |

---

## Scenario A: Account Management (Email Address Update)

### 1. Inbound Customer Message
> **Customer:** John Doe (`john.doe@email.com`)  
> **Message:**  
> *"Hi FlexTime support, I recently switched companies and need to update the login email address on my FlexTime team account to my new corporate address: john.newwork@apexsoftware.com. Can an agent please switch this over for me in your database right away? Thanks, John."*

### 2. Stage 1: Intent & Sentiment Classification
```json
{
  "intent": "ACCOUNT_MANAGEMENT",
  "sentiment": "NEUTRAL",
  "urgency": false,
  "confidence": 0.99,
  "entities": {
    "customer_name": "John Doe",
    "email": "john.doe@email.com",
    "new_email": "john.newwork@apexsoftware.com",
    "order_id": null,
    "amount": null
  },
  "routing_target": "Frontline AI"
}
```

### 3. Stage 2: CARE Responder Output
> *"Hi John, thank you for reaching out! To safeguard your account security and organization data, our team does not manually edit credentials in our backend database.*  
>  
> *I have initiated a secure verification link sent to your registered address (`j***@email.com`). Simply click that link within the next 24 hours to confirm your identity and authorize the change to your new work address.*  
>  
> *Once approved, your login and team workspaces will update instantly. Please let me know if you run into any issues during the verification step!"*  
> *(Word Count: 88 words)*

### 4. Stage 3: Self-Verification Audit
```markdown
- Audit Status: PASS
- Refund Cap Check: NOT_APPLICABLE
- PII Leak Check: SECURE (Original email masked as j***@email.com; no passwords requested or revealed)
- Word Count: 88 words (PASS - strictly under 100-word limit)
- Tone & Empathy: PASS (Polite, reassuring, frames security restriction as protection for the customer)
- Policy Alignment: COMPLIANT (Enforces FlexTime Policy §2.1: Email changes require self-service 2FA verification link)
- Remediation Note: None. Response approved for delivery.
```

### 5. Stage 4: Escalation Assessment
- **Escalation Required:** `FALSE` (Standard self-service procedure completed autonomously).

### 6. Stage 5: CRM Summary Record
#### CRM Summary Card
- **Customer:** John Doe (`j***@email.com`)
- **Interaction Outcome:** `RESOLVED_BY_AI`
- **Primary Driver:** Account Email Change Request
- **Financial Adjustment:** $0.00
- **Customer Satisfaction Estimate:** 5 / 5 Stars

---

## Scenario B: Double Billing ($15 Autonomous Refund)

### 1. Inbound Customer Message
> **Customer:** Sarah Connor (`sarah.c@email.com`)  
> **Order ID:** `FT-44120`  
> **Message:**  
> *"I just checked my credit card statement and I see two charges of $15.00 for the FlexTime Team Calendar add-on this morning! I only subscribed once. This is unacceptable and sloppy. Please fix this mistake and give me my $15 back immediately."*

### 2. Stage 1: Intent & Sentiment Classification
```json
{
  "intent": "BILLING_REFUND",
  "sentiment": "FRUSTRATED",
  "urgency": true,
  "confidence": 0.98,
  "entities": {
    "customer_name": "Sarah Connor",
    "email": "sarah.c@email.com",
    "order_id": "FT-44120",
    "amount": "$15.00"
  },
  "routing_target": "Frontline AI"
}
```

### 3. Stage 2: CARE Responder Output
> *"Hi Sarah, I am so sorry for the double charge on your Team Calendar add-on—I completely understand your frustration with this billing glitch.*  
>  
> *I have reviewed transaction `FT-44120`, canceled the duplicate invoice, and immediately issued a full $15.00 refund back to your original payment method. You will see this credit reflect on your banking statement within 3 to 5 business days.*  
>  
> *Your subscription remains fully active with zero interruption. Thank you for your patience while I resolved this for you today!"*  
> *(Word Count: 85 words)*

### 4. Stage 3: Self-Verification Audit
```markdown
- Audit Status: PASS
- Refund Cap Check: COMPLIANT ($15.00 is within the autonomous $20.00 refund cap specified in FlexTime Policy §3.1)
- PII Leak Check: SECURE (No card numbers or sensitive financial data disclosed)
- Word Count: 85 words (PASS - strictly under 100-word limit)
- Tone & Empathy: PASS (Immediate empathy, validates user frustration, transparent resolution)
- Policy Alignment: COMPLIANT (Duplicate charge identified and autonomously corrected within authority limits)
- Remediation Note: None. Response approved for delivery.
```

### 5. Stage 4: Escalation Assessment
- **Escalation Required:** `FALSE` (Amount of $15.00 is strictly under the $20.00 autonomous threshold).

### 6. Stage 5: CRM Summary Record
#### CRM Summary Card
- **Customer:** Sarah Connor (`s***@email.com`)
- **Interaction Outcome:** `RESOLVED_BY_AI`
- **Primary Driver:** Duplicate Add-on Charge ($15.00)
- **Financial Adjustment:** Refund Processed ($15.00)
- **Customer Satisfaction Estimate:** 4.8 / 5 Stars

---

## Scenario C: Major Charge Dispute ($120 Refund Escalation)

### 1. Inbound Customer Message
> **Customer:** Michael Scott (`m.scott@dunder.com`)  
> **Order ID:** `FT-ANNUAL-9921`  
> **Message:**  
> *"WHAT IS THIS?! I just got hit with a massive $120.00 annual subscription renewal charge on my card for FlexTime Pro! I thought I set this to cancel three weeks ago before the trial expired! I demand an immediate $120.00 refund right now, or I will dispute the charge with my bank and report you to consumer protection!"*

### 2. Stage 1: Intent & Sentiment Classification
```json
{
  "intent": "BILLING_REFUND",
  "sentiment": "URGENT_ANGRY",
  "urgency": true,
  "confidence": 0.99,
  "entities": {
    "customer_name": "Michael Scott",
    "email": "m.scott@dunder.com",
    "order_id": "FT-ANNUAL-9921",
    "amount": "$120.00"
  },
  "routing_target": "Tier-2 Billing"
}
```

### 3. Stage 2: CARE Responder Output
> *"Hi Michael, I completely understand your shock and distress at seeing an unexpected $120.00 annual renewal fee, and I apologize for the worry this has caused.*  
>  
> *Because this transaction exceeds our standard automated threshold, I have personally escalated your case directly to our Senior Finance Team under priority ticket `FT-ESC-90812`.*  
>  
> *Our billing manager is pulling your cancellation request logs and will issue the manual refund determination within 4 business hours. You will receive an update at `m***@dunder.com` shortly. We are committed to making this right for you."*  
> *(Word Count: 92 words)*

### 4. Stage 3: Self-Verification Audit
```markdown
- Audit Status: PASS
- Refund Cap Check: COMPLIANT (Customer requested $120.00, which exceeds the $20.00 autonomous cap. The agent did NOT promise or issue an immediate refund, but correctly routed the inquiry to Senior Finance under FlexTime Policy §3.2)
- PII Leak Check: SECURE (Customer email masked as m***@dunder.com; zero financial credentials exposed)
- Word Count: 92 words (PASS - strictly under 100-word limit)
- Tone & Empathy: PASS (Calm, highly empathetic, de-escalates high customer anxiety, sets clear 4-hour SLA)
- Policy Alignment: COMPLIANT (Escalation protocol executed without unauthorized financial commitments)
- Remediation Note: None. Response approved for delivery.
```

### 5. Stage 4: Generated Tier-2 Escalation Ticket

```markdown
### FlexTime Internal Escalation Ticket
- **Ticket ID:** `FT-ESC-90812`
- **Timestamp:** Mon, 28 Sep 2026 14:45:00 EST
- **Customer Information:**
  - Name: Michael Scott
  - Registered Email: m.scott@dunder.com
  - Account/Order ID: `FT-ANNUAL-9921`
- **Priority Level:** CRITICAL (Chargeback Threat / High Churn Risk)
- **Category:** Billing & Finance (Disputed Annual Renewal)
- **Trigger Policy:** FlexTime Policy §3.2 — Refund Request ($120.00) Exceeds Frontline Autonomous Threshold ($20.00)
- **Summary of Issue:** Customer charged $120.00 for annual renewal following a trial period. Customer claims cancellation was initiated 3 weeks prior. High churn risk with explicit chargeback dispute warning.
- **Financial Impact:** $120.00 USD at risk
- **Recommended Action for Tier-2 Agent:** 
  1. Inspect customer event logs in Segment/Mixpanel for trial cancellation button clicks.
  2. If cancellation attempt occurred within grace period, process full $120.00 manual refund via Stripe.
  3. Send personalized confirmation from Tier-2 Finance Desk within the 4-hour SLA window.
```

### 6. Stage 5: CRM Summary Record
#### CRM Summary Card
- **Customer:** Michael Scott (`m***@dunder.com`)
- **Interaction Outcome:** `ESCALATED_TIER_2`
- **Primary Driver:** Disputed Annual Renewal ($120.00)
- **Financial Adjustment:** Escalated ($120.00 Pending Finance Review)
- **Customer Satisfaction Estimate:** 2.0 / 5 Stars (Pending Resolution)
