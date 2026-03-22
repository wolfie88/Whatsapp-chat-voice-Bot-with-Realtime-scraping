# Multi-Channel AI Chatbot with Real-Time Scraping & Lead Qualification
### Voice. Text. Image. WhatsApp. Instagram. Facebook. One Unified System.

<div align="center">

![Type](https://img.shields.io/badge/Type-Delivered%20Client%20System-%233A7CFF?style=for-the-badge)
&nbsp;
![Leads](https://img.shields.io/badge/700–900-Leads%2FMonth-%2300C853?style=for-the-badge)
&nbsp;
![Conversion](https://img.shields.io/badge/Conversion-20%25%20Improvement-%23FF6B35?style=for-the-badge)

</div>

<br/>

---

## What This Is

A fully unified AI customer engagement system built for **CryptoMiners UAE** — handling inbound leads across WhatsApp, Instagram, and Facebook Messenger simultaneously, with voice-to-voice conversation capability, real-time product data scraping, conversational lead qualification, and automated hot lead routing to the sales team.

700–900 inbound leads per month. Every one answered instantly. The best ones surfaced to sales automatically.

<br/>

---

## The Problem

Crypto mining retailers operate across multiple social channels simultaneously — and customers don't choose which channel to use based on what's convenient for the sales team. They message on WhatsApp, DM on Instagram, and reach out via Facebook Messenger, often asking the same questions:

- What miners do you have in stock?
- What's the current profitability on this model?
- What are your hosting package prices?
- Can I visit your location?

Answering these manually across three platforms — while also qualifying leads, routing hot prospects to sales, and following up with dead leads — creates a bottleneck that kills conversions. The team spends the day answering product questions instead of closing deals.

<br/>

---

## System Architecture

```
┌─────────────────────────────────────────────────────────────────────┐
│                    INBOUND MESSAGE RECEIVED                         │
│            WhatsApp · Instagram DM · Facebook Messenger             │
└──────────────────────────────┬──────────────────────────────────────┘
                               │
                    ┌──────────▼──────────┐
                    │   INPUT DETECTION   │
                    │  Text / Voice / Image│
                    └──────────┬──────────┘
                               │
          ┌────────────────────┼────────────────────┐
          ▼                    ▼                     ▼
     TEXT INPUT           VOICE INPUT          IMAGE INPUT
     Pass directly        Whisper              GPT-4 Vision
     to AI engine         transcription        analysis
          │                    │                     │
          └────────────────────┴─────────────────────┘
                               │
                               ▼
┌─────────────────────────────────────────────────────────────────────┐
│                      AI RESPONSE ENGINE                             │
│                                                                     │
│   ┌─────────────────┐      ┌──────────────────────────────────┐    │
│   │  REAL-TIME DATA  │      │      COMPANY KNOWLEDGE           │    │
│   │                  │      │                                  │    │
│   │ Web scrape:      │  +   │  Pinecone vector embeddings      │    │
│   │ ASIC Miner Value │      │  Policies · FAQs · Services      │    │
│   │ Pricing · Specs  │      │  Hosting packages · Contacts     │    │
│   │ Profitability    │      │                                  │    │
│   └─────────────────┘      └──────────────────────────────────┘    │
│                               │                                     │
│                     GPT-4.1 Mini generates response                 │
└──────────────────────────────┬──────────────────────────────────────┘
                               │
                    ┌──────────▼──────────┐
                    │  RESPONSE FORMAT    │
                    │  Voice input?       │
                    │  → TTS synthesis    │
                    │  Text input?        │
                    │  → Text reply       │
                    └──────────┬──────────┘
                               │
          ┌────────────────────┼────────────────────┐
          ▼                    ▼                     ▼
   LEAD QUALIFICATION    CHANNEL ROUTING        CRM LOGGING
   Score calculated      Instagram/Facebook     Airtable +
   HOT / WARM / COLD     → migrate to WA        Zoho CRM
          │
   HOT (70+) → Instant
   WhatsApp alert
   to sales team
```

<br/>

---

## Five Core Capabilities

### 1. Voice-to-Voice Conversations
The system handles complete voice conversations without the customer ever needing to type:
- Incoming voice message → **Whisper** transcribes to text
- AI generates response
- Response → **OpenAI TTS** synthesizes to voice
- Voice message sent back via WhatsApp

Customers who prefer voice get a voice experience. No friction, no format switching.

### 2. Real-Time Product Intelligence
Rather than relying on a static knowledge base that goes stale, the system scrapes live data at query time:
- **ASIC Miner Value** — current specs, pricing, profitability calculations
- **Hosting pages** — current package pricing and availability
- Combined with Pinecone embeddings for company-specific knowledge

Every product answer reflects real-time market data.

### 3. Conversational Lead Qualification
The AI qualifies leads naturally through conversation — no forms, no interruptions. It collects four key signals:

| Signal | How It's Collected |
|---|---|
| **Budget** | Conversationally through product interest and questions |
| **Timeline** | "When are you looking to start?" |
| **Location** | For hosting relevance and site visit routing |
| **Experience** | First-time buyer vs. experienced miner |

### 4. Lead Scoring & Hot Lead Routing
Every conversation generates a lead score:

| Score | Tier | Action |
|---|---|---|
| **70+** | 🔥 HOT | Instant WhatsApp alert to sales team with full context |
| **40–69** | 🌡️ WARM | Added to nurture sequence |
| **< 40** | ❄️ COLD | Enrolled in reactivation campaign |

Hot leads reach the sales team within seconds of qualification — not hours.

### 5. Cross-Channel Migration Strategy
Instagram and Facebook users are strategically moved to WhatsApp — where response rates are higher, conversations are richer, and the full voice capability is available. The migration is handled conversationally, not as a redirect.

<br/>

---

## Automated Dead Lead Reactivation

On a daily schedule, the system runs reactivation campaigns against cold and stale leads:

| Segment | Template | Trigger |
|---|---|---|
| **Premium** | High-value ASIC focus, ROI framing | Leads who inquired about $5K+ miners |
| **Mid-tier** | Entry-level options, hosting packages | Leads who browsed but didn't commit |
| **Dormant** | Re-engagement with market update angle | No activity in 14+ days |

Every reactivation message is personalized using conversation history stored in Airtable.

<br/>

---

## Results Delivered

| Metric | Outcome |
|---|---|
| Inbound leads handled monthly | **700–900** |
| Average daily volume | **30–40 leads** |
| Conversion rate improvement | **20%** |
| Manual product lookups eliminated | **100%** |
| Response time across all channels | **Instant** |
| Hot leads missed due to slow routing | **Zero** |
| Channels covered simultaneously | **3 (WhatsApp · Instagram · Facebook)** |
| Input types supported | **Voice · Text · Image** |

<br/>

---

## Tech Stack

| Layer | Tool | Purpose |
|---|---|---|
| **Orchestration** | n8n | Workflow automation and channel routing |
| **WhatsApp** | WhatsApp Cloud API | Primary conversation and voice channel |
| **Instagram / Facebook** | Meta Messenger API | Secondary inbound channels |
| **Conversational AI** | OpenAI GPT-4.1 Mini | Response generation and lead qualification |
| **Voice Transcription** | OpenAI Whisper | Incoming voice message processing |
| **Voice Synthesis** | OpenAI TTS | Outgoing voice message generation |
| **Company Knowledge** | Pinecone | Vector embeddings for RAG responses |
| **Live Product Data** | Web scraping | Real-time ASIC specs and pricing |
| **Lead Tracking** | Airtable | Conversation history and lead records |
| **CRM** | Zoho CRM | Sales pipeline and hot lead management |
| **Supporting AI** | Google Gemini | Supplementary analysis tasks |

<br/>

---

## Repository Structure

```
📁 multi-channel-ai-chatbot-lead-qualification/
├── 📄 README.md
├── 📁 workflow/
│   └── crypto-chatbot-system.json        ← n8n workflow export
└── 📁 docs/
    ├── lead-scoring-logic.md              ← Scoring algorithm detail
    └── channel-architecture.md           ← Multi-channel routing logic
```

<br/>

---

## Built by Trilles AI

This system was designed and delivered by **[Awais Ali](https://www.linkedin.com/in/awais-ali-tillesai)**, CEO & Co-Founder of **[Trilles AI](https://www.trillesai.com)**.

If your business is losing leads to slow responses across multiple social channels — or your team is spending their day answering product questions instead of closing — this is exactly what we build.

<div align="center">

[![Connect on LinkedIn](https://img.shields.io/badge/Connect%20on%20LinkedIn-%230A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/awais-ali-tillesai)
&nbsp;
[![Visit Trilles AI](https://img.shields.io/badge/Visit%20Trilles%20AI-%233A7CFF?style=for-the-badge&logoColor=white)](https://www.trillesai.com)
&nbsp;
[![Email](https://img.shields.io/badge/Email%20Me-%23EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:letsautomatewithawais@gmail.com)

</div>

<br/>

---

<div align="center">
<sub>Built with precision · Powered by Trilles AI · <code>www.trillesai.com</code></sub>
</div>
