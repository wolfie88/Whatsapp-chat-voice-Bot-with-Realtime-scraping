# Lead Scoring Logic

## Overview

Every conversation is scored continuously as signals are collected.
The score determines routing — hot leads go to sales instantly,
warm leads enter nurture, cold leads enter reactivation.

---

## Scoring Signals

| Signal | Condition | Points |
|---|---|---|
| **Budget** | Mentioned specific budget | +20 |
| **Budget** | Asked about pricing (implied interest) | +10 |
| **Timeline** | Ready within 30 days | +25 |
| **Timeline** | Ready within 90 days | +15 |
| **Timeline** | Exploring / no timeline | +5 |
| **Location** | UAE-based (hosting relevant) | +15 |
| **Location** | International (shipping viable) | +10 |
| **Experience** | Existing mining operation | +20 |
| **Experience** | Researched and ready to buy | +15 |
| **Experience** | First-time buyer | +5 |
| **Engagement** | Asked 3+ specific product questions | +10 |
| **Engagement** | Requested site visit or call | +20 |
| **Engagement** | Shared contact details proactively | +15 |

Maximum score: 100

---

## Score Tiers & Actions

### 🔥 HOT — Score 70+
```
Action:
  1. Immediately send WhatsApp notification to sales team
  2. Notification includes:
     - Lead name and contact info
     - Channel they came from
     - Full conversation summary
     - Score breakdown
     - Last message timestamp
  3. Log to Zoho CRM as HOT lead
  4. Assign to next available sales rep
```

### 🌡️ WARM — Score 40–69
```
Action:
  1. Log to Airtable as WARM
  2. Enroll in nurture sequence
  3. Flag for follow-up within 48 hours
  4. Continue AI engagement on channel
```

### ❄️ COLD — Score < 40
```
Action:
  1. Log to Airtable as COLD
  2. Determine segment (premium / mid-tier / dormant)
  3. Enroll in daily reactivation campaign
  4. Re-score if they re-engage
```

---

## Score Recalculation

The score recalculates after every message exchange.
A COLD lead that re-engages and provides budget/timeline
information can move to HOT within a single conversation.

Score history is stored in Airtable per lead.
Sales team sees the trajectory, not just the final score.

---

## Reactivation Segments

```
premium_segment:
  condition: any mention of high-end ASICs (Antminer S21, Whatsminer M60+)
             OR budget signal > $5,000
  template:  ROI-focused, performance specs, hosting ROI calculator

mid_tier_segment:
  condition: entry-level ASIC interest OR budget $1,000–$5,000
  template:  accessibility framing, starter packages, hosting bundles

dormant_segment:
  condition: no activity for 14+ days
  template:  market update angle, new stock arrivals, price movement alerts
```

---

## CRM Field Mapping

### Airtable Schema
| Field | Type | Source |
|---|---|---|
| `lead_name` | Text | Extracted from conversation |
| `contact_channel` | Select | WhatsApp / Instagram / Facebook |
| `contact_id` | Text | Platform user ID |
| `score` | Number | Calculated |
| `tier` | Select | HOT / WARM / COLD |
| `budget_signal` | Text | Extracted from conversation |
| `timeline_signal` | Text | Extracted from conversation |
| `location` | Text | Extracted from conversation |
| `experience_level` | Select | New / Experienced |
| `conversation_summary` | Long text | AI-generated |
| `last_contact` | DateTime | Auto |
| `reactivation_segment` | Select | Premium / Mid-tier / Dormant |

### Zoho CRM (HOT leads only)
- Contact created with full profile
- Opportunity created with estimated value
- Assigned to sales rep
- Activity log includes full conversation history
