# Arman Christian Mendoza | AI Automation Specialist

AI automation specialist in the Philippines building n8n, Zapier and Make.com workflows and AI agents for lead follow-up, AR/AP, recruiting and reporting.

- Portfolio: https://acq-mendoza.github.io/acqmendoza.ai/
- Resume (PDF): https://acq-mendoza.github.io/acqmendoza.ai/resume.pdf
- LinkedIn: https://www.linkedin.com/in/arman-christian-mendoza
- Upwork: https://www.upwork.com/freelancers/~019e0c8ba8404ceeec
- Book a call: https://calendly.com/acq-mendoza/30min
- Email: acq.mendoza@gmail.com

## Turn Manual Chaos Into Automated Flow

I help founders, agencies, and sales & ops teams eliminate the manual busywork slowing them down (lead follow-up, proposal generation, reporting, approvals) by building automated systems and AI agents that run the process 24/7, with no dropped handoffs.

## About Me: who I am and what I build

I'm Arman Christian Mendoza, an AI automation specialist based in the Philippines who designs and ships end-to-end workflows and AI agents for sales, marketing, and operations teams. My work sits at the intersection of no-code automation platforms (n8n, Zapier, and Make.com) and modern LLMs like Claude, GPT, and Gemini. I don't just connect apps; I build systems that automate the repetitive work in sales, finance, recruiting, and operations, and route only the decisions that need a human to the right person.

Every workflow featured on this page is a live, tested build, not a course exercise. The certifications back the work; they don't substitute for it.

## What I Automate

Four areas where I build workflows and AI agents that run 24/7 and hand only the judgment calls to a person.

- **Sales & Leads:** instant lead follow-up and AI calls, lead scoring and CRM sync, proposal generation, outbound performance digests
- **Recruiting & HR:** AI resume screening, interview scheduling, candidate updates and offers, onboarding handoffs
- **Customer Comms:** AI voice appointment setters, WhatsApp and chat assistants, ad comment replies, inbox triage
- **Ops & Finance:** invoice capture to QuickBooks, payment follow-up, inventory alerts, reports and dashboards

## Tech Stack

- **Automation:** n8n, Make.com, Zapier, webhooks & REST APIs
- **AI models:** OpenAI (ChatGPT), Anthropic (Claude), Google Gemini, custom GPTs & agents
- **Developer tools:** custom JSON parsing, HTTP request headers, Google Cloud Platform, GitHub Pages
- **Platforms:** HubSpot, Notion, Slack, QuickBooks Online, Google Workspace, Airtable, GoHighLevel, Salesforce, Pipedrive

## Live Demos

The portfolio page has three interactive demos (AI Lead Qualifier, Invoice Extractor, Recruitment Screening). Each runs the same steps as the production version: AI reads the input, code checks the result, and a gate decides whether a person needs to look.

## Featured Work: systems running for clients

Each one replaces a job someone was doing by hand, and each one knows when to stop and ask a person.

### Every new lead gets a call before they cool off (Sales)

Stack: n8n, Facebook Lead Ads, ElevenLabs, Supabase, Slack

- **Problem:** Leads from Facebook ads waited hours or days for a callback, and most had moved on by then.
- **System:** A new lead form triggers an outbound AI phone call through ElevenLabs right away. When the call ends, the transcript, summary and qualification answers are saved to the lead record. Sales gets a Slack and email alert whether the lead booked or not.
- **Results:** instant AI call on every new lead; 100% of calls transcribed and summarized; 2 routes (booked or follow up).

How it works:
1. Trigger: listens for new form submissions from Facebook Lead Ads.
2. Formatting & storage: cleans up the lead payload and inserts a new record into Supabase with a "new" status.
3. AI call trigger: places an outbound call via the ElevenLabs conversational AI API with personalized details, then updates Supabase with the call tracking info.
4. Webhook handling: listens for the call completion event and parses transcripts, duration, summary, and qualification metrics.
5. Database update: writes final call outcomes back to the lead's Supabase record.
6. Conditional routing: branches on whether an appointment was booked, sending tailored Slack and Gmail alerts with full transcripts and summaries either way.

### A recruiting coordinator that never sleeps (Recruiting)

Stack: n8n, Zoho Recruit, Google Calendar, AI screening

- **Problem:** Hiring teams were screening resumes by hand, chasing interview times by email, and letting good candidates go quiet.
- **System:** An AI agent scores every applicant. Strong candidates are synced to Zoho Recruit and booked on the calendar with a personal invite. Everyone else gets a respectful reply. Offers, hires and onboarding days follow the same way.
- **Results:** score of 75+ to advance (editable); 6 stages from screening to onboarding; no code edits needed day to day.

How it works:
1. Sourcing & intake: a daily trigger searches job boards and LinkedIn for candidates, while a webhook captures new applications. Both paths normalize candidate data and log it to the Applications pipeline sheet.
2. AI screening & scoring: an AI resume screening agent scores each candidate; a threshold check (score 75 or higher) decides whether the candidate advances.
3. Advance path: qualified candidates are upserted into Zoho Recruit, set to Interview Scheduled, booked on Google Calendar, and sent an AI-drafted interview invite.
4. Below-threshold path: other candidates get an AI-drafted follow-up email, logged to the Screened tab.
5. Hiring decision webhook: drafts and sends an offer or rejection, updates Zoho Recruit, and logs the outcome.
6. Offer response webhook: if accepted, sets status to Hired, schedules an onboarding day, and sends a welcome email; if declined, logs it and closes the record.

### Phone bookings answered at 2 a.m. (Voice AI)

Stack: n8n, Vapi, Google Calendar

- **Problem:** Field-service companies (roofing, HVAC, plumbing) missed after-hours calls, and every missed call was a missed job.
- **System:** The backend behind a Vapi voice agent. It checks real calendar availability, reads open slots to the caller, and books the job the moment they pick a time. Work hours, slot length and buffers live in one settings node.
- **Results:** 24/7 answering with real availability; 2 tools (check and book); 3 nodes to edit for a new client.

How it works:
1. Webhook: the single entry and exit point; Vapi sends every tool call here and gets the result back to speak to the caller.
2. Configuration node: timezone, work hours, appointment length, buffers, and slot interval.
3. Route by tool name: sends checkAvailability or bookAppointment requests down the matching path.
4. Availability path: pulls the day's Google Calendar events, generates time blocks, removes overlapping or past slots, and returns the open ones.
5. Booking path: creates the calendar event and confirms success back to Vapi.

### Invoices in, payments chased, nobody retyping (Ops & Finance)

Stack: n8n, GPT-4o, QuickBooks Online, Twilio, Slack

- **Problem:** A small finance team was keying vendor bills into QuickBooks by hand and chasing overdue clients whenever they found time.
- **System:** Two connected workflows. Incoming invoices are read by GPT-4o, re-checked in code and posted to QuickBooks, with uncertain ones sent to Slack. Outgoing invoices are watched daily, and overdue clients move up a risk-based reminder ladder by email, SMS and call task.
- **Results:** 0.85 confidence needed to post without review; 5 reminder stages, paused for disputes; daily sync with live QuickBooks data.

**Automated AR & Payment Follow-Up System (QuickBooks + Twilio + Slack):**
1. Daily trigger (8am): pulls open invoices from QuickBooks and reads the Invoices and Clients tabs from Google Sheets.
2. Compute actions & content: a Code node decides, per invoice, whether to skip and which content and channel (email, SMS or call) comes next.
3. Skip logic: skips invoices that are disputed, on a payment plan, or already paid.
4. Escalation sequence: routes to email, SMS (Twilio), call task, or internal alert depending on how overdue the invoice is, and notifies the AR team on Slack when a human call is needed.
5. Monthly risk recalculation: recalculates each client's risk and decay score so the daily sequence always uses fresh risk data.

**Process Email Invoices with OCR, GPT-4, Slack, QuickBooks and Google Sheets:**
1. Intake: a Gmail trigger polls a labeled AP inbox every 5 minutes for emails with attachments.
2. Text extraction: PDFs go to a PDF text extractor; images and scans go to an OCR API.
3. AI structuring: a GPT-4o agent extracts invoice fields, line items, totals, and a confidence score per field as structured JSON.
4. Validation & masking: code recalculates totals, flags mismatches, and masks PAN/GST/bank account numbers.
5. Review gate: failed validation or confidence below 0.85 sends a review request to Slack and pauses until resumed.
6. Bookkeeping & audit: creates the bill in QuickBooks, appends an audit record to Google Sheets, and confirms on Slack.

## Other Workflows I've Built

- **Generate and send personalized client proposals with AI (n8n + OpenAI):** validates input, classifies budgets into tiers, applies dynamic pricing, drafts a 7-section AI proposal, and emails branded HTML via SendGrid with Google Sheets logging and Slack alerts. For sales teams, agencies, and freelancers sending 10+ proposals a week.
- **Capture leads from any form to HubSpot and notify your team in Slack (n8n template):** replaces a classic Form to CRM to Slack zap at zero per-task cost.
- **Daily Outbound Performance Digest (n8n + Claude):** reads campaign sheets, analyzes sentiment with Claude, ranks follow-ups, and emails a concise morning digest.
- **Auto reply to Instagram & Facebook ad comments with lead capture (n8n + OpenRouter):** classifies comments as query, positive review, negative review, or spam; drafts replies from a knowledge base; flags negative reviews to Slack.
- **HubSpot Lead Generation & AI Qualification Pipeline (Zapier + Groq):** scores new HubSpot contacts with AI, emails the team, logs to Google Sheets, and creates prioritized Google Tasks.
- **Salesforce New Lead Nurture & Compliance Audit Trail (Zapier):** waits 1 day after a new lead, sends a team reminder with the lead ID, and logs the activity to Zapier Tables.
- **Intelligent Gmail Email Triage & Categorization (Zapier):** analyzes sender domain, subject keywords and content patterns, and auto-applies labels.
- **Trivia Generation and Facebook Posting with Telegram Approval (n8n + Gemini):** generates a trivia fact, builds card art in Google Slides, routes it through a Telegram approval gate, and posts approved items to a Facebook Page.
- **Telegram Crypto Analysis Bot (n8n + Gemini):** pulls MEXC market data, computes RSI, EMA, MACD and Bollinger Bands, scores each asset with Gemini, and returns a BUY/SELL/HOLD alert with levels to Telegram, logged to Google Sheets.

## Verified Certifications

- Zapier Academy: Building AI Agents (July 22, 2026), Building Intermediate Zaps (July 22, 2026), Building Basic Zaps (July 21, 2026)
- n8n Academy: Integrations: APIs & Workflows, N8N102 (July 23, 2026); Essentials: Your First Workflows, N8N101 (July 22, 2026)
- Make.com Academy: Make Intermediate (July 2026), AI Agent Builder (July 2026)
- Anthropic: Claude 101, Claude Code 101, Claude Code in Action (July 2026)
- Airtable Builder Certification (July 28, 2026)
- HubSpot Data Integration Certified (July 2026)

## Frequently Asked Questions

### What does AI automation specialist Arman Christian Mendoza do?

Arman Christian Mendoza builds automated workflows and AI agents that take repetitive work off sales, finance, and operations teams. Typical builds include lead capture and qualification, accounts receivable follow-up, invoice processing into QuickBooks Online, recruiting pipelines, and AI voice appointment setting, using n8n, Zapier, Make.com, and LLMs such as Claude, GPT, and Gemini.

### Should I use n8n, Zapier, or Make.com for my automation?

It depends on volume, complexity, and who will maintain it. Zapier is the fastest to set up and easiest for non-technical teams to own. Make.com handles visual branching and multi-app scenarios at a lower per-operation cost. n8n suits complex, high-volume, or AI-heavy workflows and can be self-hosted, which removes per-task pricing. Arman builds on all three and recommends one after mapping your process.

### Can Arman Christian Mendoza automate accounts receivable and accounts payable in QuickBooks Online?

Yes. His portfolio includes an n8n accounts receivable system that pulls open QuickBooks Online invoices daily, scores client risk, and runs a 5-stage email, SMS, and call-task escalation, and an accounts payable workflow that uses GPT-4o to extract vendor invoices from email, validates the totals, sends low-confidence invoices to Slack for human review, and posts approved bills to QuickBooks.

### What's the process to start a project with Arman Christian Mendoza?

The process starts with a discovery call to map out your current manual process and where it's breaking down. From there, Arman scopes the workflow, builds and tests it in n8n, Zapier, or Make.com, and hands it off with documentation so your team can run it confidently.

### Who does Arman Christian Mendoza typically work with?

He typically works with founders, agencies, and sales & ops teams who need to eliminate manual busywork like lead follow-up, proposal generation, reporting, and approvals.

### What other platforms and tools does Arman Christian Mendoza work with?

He works with HubSpot, Notion, Slack, QuickBooks Online, Google Workspace, Airtable, GoHighLevel, Salesforce, and Pipedrive.

### Does Arman Christian Mendoza offer support after a workflow is built, and what time zone is he in?

Yes, he offers post-launch support to fix issues and refine workflows as your business evolves. He is based in the Philippines (GMT+8), giving overlapping working hours with both Asia-Pacific and, later in the day, US-based teams.

## Contact

Tell me what's eating your team's week.

- Email: acq.mendoza@gmail.com
- Schedule a call: https://calendly.com/acq-mendoza/30min
- LinkedIn: https://www.linkedin.com/in/arman-christian-mendoza
- Upwork: https://www.upwork.com/freelancers/~019e0c8ba8404ceeec
