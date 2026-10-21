# The Plan to Keep Building: Portfolio Compounding Protocol

> **Core Principle:** A portfolio that never gets a second project goes stale. The difference between a class artifact and a career platform is a simple, repeatable habit set up while the build context is fresh.

---

## 1. How to Add the Next Case Study

### Exactly Where It Goes
- **Repository / Site Location:** 
  - **Overview card:** `index.html#work` (inserted as the newest card in `<section id="cases">` preceding the FlyRank Refresh Opportunity case).
  - **Standalone deep-dive:** `cases/gsc-rank-drift-detector.html` (mirrored from the existing case study template in `docs/paper-examples/index.html` — Door 2 case study layout).
  - **Data / Analysis artifacts:** `work/notebooks/` and metrics receipts in `outputs/`.

### The 30-Minute Addition Workflow (Reusing the Week 2 Three-Beat Shape)

Do not start from a blank page. Open the existing **Claude Project**, which already has your voice card, visual styles, and claim boundaries loaded, and follow this four-step sprint:

```text
[Step 1: 15-Min AI Interview] -> [Step 2: Voice & Claim Polish] -> [Step 3: Component Drop-In] -> [Step 4: Push & Verify]
```

#### Beat 1: The Problem (5 minutes)
- **Question to AI:** *"Interview me about the problem my new project solves. Ask me: What was stuck or manual? Who makes the operational decision? What does a false positive vs. false negative cost in real time/money?"*
- **Structure:**
  - Context & operational friction (e.g., editorial teams manually reviewing thousands of URLs).
  - The baseline rule currently in place and why an `if-else` heuristic fails.
  - The cost of a wrong call.

#### Beat 2: What You Did & Decided (15 minutes)
- **Question to AI:** *"Now ask me what I built and decided. Force me to name: The unit of analysis, the safe data contract, the ML framing vs. rule baseline, and the single hardest thing that broke during validation."*
- **Structure:**
  - Data contract & leakage audit (feature engineering boundaries, time-split validation).
  - Architectural choices (model comparison, why a simpler model won or lost).
  - One honest break/limitation caught (e.g., drift across seasonal queries, cold-start URLs).

#### Beat 3: What Came of It (10 minutes)
- **Question to AI:** *"Extract the measurable results. Do not allow generic praise. Force me to state: The precision/recall lift over baseline, the decision-support queue output, and what we directional can and cannot claim."*
- **Structure:**
  - The receipts (e.g., baseline vs. model Precision@50, ROC AUC, ranking fidelity).
  - The action playbook (who gets the queue, what action codes trigger).
  - The honest conclusion: what this proved and what remains a known limitation.

---

## 2. The Named Next Piece of Real Work

- **Project Title:** **Real-Time Search Console CTR & Rank Drift Early-Warning Classifier**
- **Domain:** Applied Search Intelligence & Automated SEO Decision Support
- **Brief Scope:**
  - Connects to Google Search Console query-level performance data (or batched multi-client export).
  - Tracks 14-day rolling rank velocity, impression drift, and CTR underperformance against position-benchmark curves.
  - Employs an XGBoost / Gradient Boosting classifier to flag decaying high-visibility queries 30 days before major traffic loss.
  - Outputs an automated Slack/Email alert queue prioritizing top 20 urgent review URLs for technical and content remediation.
- **Why this piece:** It directly builds on the FlyRank Content Refresh Opportunity Model, closing the loop from static portfolio audits to proactive real-time monitoring.

---

## 3. Concrete Reminder Set (Evidence)

A recurring calendar nudge has been scheduled to ensure this project transitions from an idea into published proof.

### Event Details
- **Calendar Event Title:** `[Career Platform] Add Next Case Study: GSC Rank Drift Classifier`
- **First Trigger Date:** Sunday, November 15, 2026
- **Time:** 10:00 AM – 11:30 AM (90-minute focused sprint)
- **Cadence / Recurrence:** Monthly on the 3rd Sunday (`RRULE:FREQ=MONTHLY;BYDAY=3SU`)
- **Alert Notifications:** 
  - 1 day before (Email alert)
  - 15 minutes before (Device pop-up nudge)
- **Event Description / Checklist:**
  ```text
  Prompt for Claude Project:
  "I am ready to add the GSC Rank Drift Classifier case study. 
  Follow the 3-beat interview:
  1. The problem (manual SERP tracking, stale traffic alerts)
  2. What I did & decided (time-split validation, XGBoost vs. rule baseline, precision@20)
  3. What came of it (+34% early detection lift over 30d drop threshold)
  Draft the case directly into my portfolio's Door 2 case study HTML layout."
  ```

### iCalendar (.ics) Specification
```ics
BEGIN:VCALENDAR
VERSION:2.0
PRODID:-//FlyRank AI Internship//Portfolio Compounding//EN
CALSCALE:GREGORIAN
BEGIN:VEVENT
SUMMARY:[Career Platform] Add Next Case Study: GSC Rank Drift Classifier
UID:flyrank-next-case-20261115@internship.flyrank.ai
DTSTAMP:20261021T093000Z
DTSTART:20261115T043000Z
DTEND:20261115T060000Z
RRULE:FREQ=MONTHLY;BYDAY=3SU
DESCRIPTION:30-minute case addition sprint using the Claude Project voice card and 3-beat shape.
BEGIN:VALARM
TRIGGER:-P1D
ACTION:DISPLAY
DESCRIPTION:Reminder: Tomorrow is portfolio update sprint.
END:VALARM
BEGIN:VALARM
TRIGGER:-PT15M
ACTION:DISPLAY
DESCRIPTION:Start Claude Project interview for new case study.
END:VALARM
STATUS:CONFIRMED
END:VEVENT
END:VCALENDAR
```

---

## 4. Preserved Build Context (Claude Project Specification)

The Claude Project ensures future updates require **zero setup time**. The project persists:

| File / Context Asset | What It Holds | Why It Prevents a Rebuild |
|---|---|---|
| **`voice_card.md`** | 5–7 words: *"Direct, warm, plain, decision-first, no buzzwords."* Explicit instruction to keep one honest failure/limitation. | Keeps writing voice consistent across years without prompt coaching. |
| **`case_template.html`** | Reusable 3-beat HTML markup (`#problem`, `#solution`, `#results`), metric badges, figure containers. | AI outputs drop-in semantic HTML matching existing CSS classes instantly. |
| **`style_tokens.css`** | Palette (Mint, Dark Slate, Muted Grey), typography (Geist / Manrope), border-radius, card shadows. | Eliminates CSS styling drift and visual misalignment. |
| **`claim_boundaries.md`** | Safety rules: *"observed, directional, decision-support"*, zero client names, strict out-of-time validation metrics. | Prevents model hallucinations or unsupportable causal claims. |
| **`stack_context.md`** | Static HTML5 + Vanilla CSS on Netlify/GitHub Pages, Python ML pipeline (`sklearn`, `pandas`, `duckdb`). | Guarantees code snippets and deployment commands match the current architecture. |
