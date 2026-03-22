# Channel Architecture & Routing Logic

## Overview

Three inbound channels feed into one unified AI engine.
The system handles input type detection, channel-specific
response formatting, and cross-channel migration automatically.

---

## Channel Entry Points

### WhatsApp Cloud API
- Primary channel — highest conversion rate
- Supports: text, voice, image, document inputs
- Voice-to-voice capability fully active
- Rich message formatting available

### Instagram Messenger API
- Secondary channel — high volume for visual product discovery
- Supports: text, image inputs
- Migration to WhatsApp triggered after first qualifying interaction

### Facebook Messenger API
- Secondary channel — broader demographic reach
- Supports: text, image inputs
- Migration to WhatsApp triggered after first qualifying interaction

---

## Input Type Detection & Processing

```
On message received:

  message.type == "audio"
    → Download audio file
    → Send to Whisper API for transcription
    → Process transcribed text through AI engine
    → Generate text response
    → Send to OpenAI TTS for voice synthesis
    → Reply with synthesized voice message

  message.type == "image"
    → Download image
    → Send to GPT-4 Vision with product context prompt
    → Identify product in image if applicable
    → Generate contextual response
    → Reply with text

  message.type == "text"
    → Process directly through AI engine
    → Reply with text
    → If conversation score triggers HOT → add voice CTA
```

---

## AI Response Engine — RAG Architecture

Every response combines two data sources:

### Source 1 — Real-Time Scraped Data
```
Triggered when: query contains product name, pricing, profitability,
                or hosting keywords

Scrape targets:
  - ASIC Miner Value (asicminervalue.com)
    Fields: model, hashrate, power, price, daily revenue, ROI days
  - Company hosting pages
    Fields: package name, price/month, included hashrate, location

Data freshness: scraped at query time — always current
```

### Source 2 — Pinecone Vector Knowledge Base
```
Contains: company policies, FAQs, service descriptions,
          contact information, team details, location,
          warranty terms, payment methods, delivery info

Query method: semantic search against user message
Top-K: 5 most relevant chunks retrieved per query

Combined with scraped data for complete response context
```

---

## WhatsApp Migration Strategy

Instagram and Facebook users are migrated to WhatsApp
through natural conversation — not hard redirects.

```
Migration trigger conditions (any one):
  - Lead score crosses WARM threshold (40+)
  - User asks about pricing or specific products
  - Second message exchange completed

Migration message approach:
  - Acknowledge their question
  - Offer fuller assistance via WhatsApp
  - Include direct WhatsApp link with pre-filled message
  - Do NOT interrupt the current conversation thread

Post-migration:
  - Both channels remain monitored
  - Conversation history merged in Airtable
  - Primary channel updated to WhatsApp in CRM
```

---

## Conversation History Management

```
Storage: Airtable (per lead, per channel)

Stored per message:
  - timestamp
  - direction (inbound / outbound)
  - channel
  - input_type (text / voice / image)
  - content (transcribed if voice)
  - ai_response
  - score_at_time

Context window management:
  - Last 10 message pairs passed to AI on each turn
  - Full history available in Airtable for sales team
  - Summary generated when lead reaches HOT tier
```

---

## Sales Team Notification Format

```
🔥 HOT LEAD ALERT

Name: [extracted name]
Channel: WhatsApp / Instagram / Facebook
Contact: [phone / username]
Score: [score] / 100

SUMMARY:
[AI-generated 3-sentence summary of conversation and intent]

SIGNALS COLLECTED:
Budget: [value or "not stated"]
Timeline: [value or "not stated"]
Location: [value or "not stated"]
Experience: [level]

LAST MESSAGE:
"[verbatim last customer message]"

→ View full conversation: [Airtable record link]
→ Open in Zoho CRM: [CRM record link]
```
