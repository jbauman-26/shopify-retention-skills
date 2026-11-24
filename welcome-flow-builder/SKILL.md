---
name: welcome-flow-builder
description: Write a four-email Klaviyo welcome flow for a Shopify brand from its brand voice file and top reviews. Use when a brand has no welcome flow, a one-email welcome, or a welcome that only delivers a discount code.
---

# Welcome flow builder

## What you need
- `brand-voice.md` (run brand-voice-extractor first)
- The signup offer, if any
- Top 20 reviews and the three best-selling products

## The flow
Trigger: a **list-triggered flow** on the newsletter or popup list ("when someone is added to the list"). Klaviyo advises against triggering a welcome flow on the Subscribed to List metric.
Flow filters: Placed Order zero times since starting this flow (so buyers drop out), and Placed Order zero times over all time (so existing customers who join the list don't get the new-subscriber story).

| Email | Send | Job |
|---|---|---|
| 1. Welcome | Right away | Deliver the offer, say who is behind the brand in two sentences |
| 2. Why it exists | Day 2 | The problem the product solves, in a customer's words |
| 3. Proof | Day 4 | Three short review lines and the best seller |
| 4. Last nudge | Day 7 | Answer the top doubt; say the offer expires only if it truly does |

## Steps
1. For each email write 3 subject lines, preview text and a 90 to 140 word body.
2. Use one verbatim review phrase per email. If there are no reviews, leave the slot marked and say so.
3. One link per email. No second discount on top of the first.

## Output
`welcome-flow.md` with the four emails and a setup sheet: flow name, trigger, both filters, delays, status draft.

## Rules that apply to every output

- Never invent customer quotes, results or numbers. If the data is missing, say so.
- Strip names, emails, phone numbers and order numbers from anything you quote.
- Everything you create in Klaviyo stays a draft. A person switches it on.
- Write like one person talking to one customer. Plain words, one idea per email, one link.

---

Part of the free Shopify Retention Skills pack by Jake Bauman (northsignal.studio). Drafts only: a person reads everything before it goes live.
