---
name: winback-flow-builder
description: Build a winback flow for a Shopify brand timed to its real reorder cycle from a Shopify orders export, with three emails that give lapsed customers a reason to return. Use when repeat purchase rate is falling or there is no winback flow.
---

# Winback flow builder

## What you need
- Shopify orders export, 12 months or more
- `brand-voice.md`. If there isn't one, ask the owner for three sentences on how the brand talks, or write plainly and flag it.
- What is new since customers last ordered (products, restocks, changes). Ask for it. If the owner has nothing, email 1 becomes a simple reminder.
- 10 or more reviews for email 2. If there are none, build email 2 from a use or care tip in the brand's own site copy instead. Never invent a review.
- Which customers are subscribed to email. If the export doesn't say, report audience sizes as upper limits.

## Steps
1. Pool every gap in days between consecutive orders from the same customer. Report the median (G), the 75th and the 90th percentile.
2. **Trigger: more than N days since the last order, where N = 2 x G rounded to whole days.** This is the same line the segments skill uses for Lapsed, so the two agree. Also report the share of all past reorder gaps that were longer than N days. That is how often customers this quiet have come back on their own.
3. Audience: customers with at least one order who are subscribed to email and have not ordered since the trigger. Exclude anyone in another flow that week.
4. Write 3 emails: email 1 at the trigger (what is new, or a plain reminder); email 2 ten days after email 1 (how other customers use it, one review line); email 3 eleven days after email 2, which is day 21 (an honest last note). No discount in email 1. An offer goes in email 3 only if the owner chooses one.
5. **Backlog:** customers already past the trigger today do not all enter the flow at once. Send them the same three emails as a one-time campaign, most recently lapsed first, in daily batches no bigger than a fifth of the brand's normal campaign send. Leave out anyone whose last order is more than 18 months old unless the owner asks for them.
6. **No response:** anyone who gets all three and neither clicks nor orders goes into a "winback no response" segment. Leave them out of regular campaigns.
7. If fewer than 200 gaps exist, say the timing is a rough estimate.

## Output
`winback-flow.md` with: the timing table, the share who return unprompted, the audience and backlog sizes, the three emails (3 subject lines each), and a setup sheet. Klaviyo has no "time since last order" trigger, so the flow is built as: trigger **Placed Order**, a first time delay of N days, and the flow filter "Placed Order zero times since starting this flow" so anyone who reorders drops out. Then the delays between emails, status draft.

## Rules that apply to every output

- Never invent customer quotes, results or numbers. If the data is missing, say so.
- Strip names, emails, phone numbers and order numbers from anything you quote.
- Everything you create in Klaviyo stays a draft. A person switches it on.
- Write like one person talking to one customer. Plain words, one idea per email, one link.

---

Part of the free Shopify Retention Skills pack by Jake Bauman (northsignal.studio). Drafts only: a person reads everything before it goes live.
