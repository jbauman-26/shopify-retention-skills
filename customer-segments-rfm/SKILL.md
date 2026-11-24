---
name: customer-segments-rfm
description: Turn a Shopify orders export into practical customer segments (new, repeat, VIP, at risk, lapsed) with sizes, revenue share and the Klaviyo segment definition for each. Use when a brand sends every campaign to its whole list.
---

# Customer segments (RFM)

## What you need
- Shopify orders export, 12 months or more, with a customer id (or email), order date and total. One row per line item is fine: group by order first.
- Today's date. Exclude cancelled and fully refunded orders.

## Steps
1. Per customer, compute recency (days since last order), frequency (number of orders) and spend (sum of totals).
2. Compute **G, the reorder gap**: take every gap in days between consecutive orders from the same customer, pool them all, and take the median. If there are fewer than 200 gaps, say G is a rough estimate. Then set **N = 2 x G, rounded to a whole number of days**, and use that same N everywhere. (Customers who haven't reordered yet have no gap to count, so G runs a little short. Say so in the output.)
3. Put each customer in **exactly one** segment. Check the rules in this order and stop at the first match:

| Order | Segment | Rule |
|---|---|---|
| 1 | Lapsed | recency is more than N days |
| 2 | At risk | recency is more than G days, up to N |
| 3 | VIP | 4 or more orders, or spend at or above the 90th percentile of customers not Lapsed or At risk (ties at the cutoff are in) |
| 4 | Repeat | 2 or 3 orders |
| 5 | New | 1 order |

Every customer matches one row, and the shares must add to 100%. Check that before reporting.

4. Report each segment's size, share of customers and share of revenue in the export period.
5. Write a Klaviyo segment definition for each, using the Placed Order metric: count conditions ("has Placed Order at least 4 times over all time") and date conditions ("has Placed Order zero times in the last N days", using G and N). **Every definition needs its recency condition as well as its count condition**, or Klaviyo will put lapsed big spenders back into VIP: VIP, Repeat and New all include "has Placed Order at least once in the last G days". The spend part of VIP needs a spend condition or a custom property; say plainly that the owner must confirm which one their account supports. Don't claim a definition works until it is built.
6. Give one sentence on what each segment should and should not receive.

## Output
`segments.md` with: G and how many gaps it came from, the table, the Klaviyo definitions, and send guidance. Flag any segment under 100 people as too small to test on.

## Rules that apply to every output

- Never invent customer quotes, results or numbers. If the data is missing, say so.
- Strip names, emails, phone numbers and order numbers from anything you quote.
- Everything you create in Klaviyo stays a draft. A person switches it on.
- Write like one person talking to one customer. Plain words, one idea per email, one link.

---

Part of the free Shopify Retention Skills pack by Jake Bauman (northsignal.studio). Drafts only: a person reads everything before it goes live.
