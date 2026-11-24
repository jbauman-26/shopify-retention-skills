---
name: klaviyo-flow-audit
description: Audit a Shopify brand's Klaviyo flows from an export or API access: find missing flows, rank existing ones by revenue per recipient, and list the fixes in order. Use when someone asks what is wrong with their flows, where email revenue is leaking, or what to build next.
---

# Klaviyo flow audit

## What you need
- Klaviyo flow analytics export (last 90 days), or read-only API access
- The account's attribution settings (Settings, Attribution)
- Shopify total revenue for the same 90 days

## Klaviyo names to use
On Shopify the metrics are **Checkout Started**, **Placed Order**, **Viewed Product**, and **Added to Cart** (only if add-to-cart tracking is installed). Welcome flows are list-triggered, not metric-triggered. Klaviyo's standard "Abandoned Cart" flow is triggered by Checkout Started. Identify every flow by its trigger, never by its name.

## Steps
1. List every live flow with trigger, number of messages, recipients, revenue and revenue per recipient.
2. Check the core set by trigger:

| Flow | Trigger |
|---|---|
| Welcome | list trigger: added to the newsletter list |
| Abandoned checkout (Klaviyo calls it Abandoned Cart) | Checkout Started |
| Browse abandonment | Viewed Product |
| Post-purchase | Placed Order |
| Winback | Placed Order, then a long first delay, with the filter "Placed Order zero times since starting this flow" |
| Sunset | no engagement for 120 to 180 days |
| Added to cart (optional) | Added to Cart, only if tracked |

Mark each present, missing or stalled (live but under 20 recipients a month). Don't mark "added to cart" missing if the store doesn't track it.
3. For each live flow, flag: only one message, a discount in message one, no filter to keep repeat buyers out of first-order copy, smart sending off.
4. Rank flows by revenue per recipient **against each other**. State the attribution window with the ranking. Klaviyo's default credits email revenue after an open, and Apple Mail auto-opens, so the absolute numbers run high. The ranking is still useful; the totals are not proof.
5. Work out flow revenue as a share of store revenue. Report it as the brand's own baseline.
6. Don't use open rate to judge anything.

## Output
`flow-audit.md` with: the flow table, the missing list, the attribution window, and a ranked fix list (what, why, effort: small, medium or large). Top three first.

## If something is missing
Do the parts you can, mark every skipped part "not checked: <what was missing>", and list what to send next time. Never fill a gap with a guess.

## Rules that apply to every output

- Never invent customer quotes, results or numbers. If the data is missing, say so.
- Strip names, emails, phone numbers and order numbers from anything you quote.
- Everything you create in Klaviyo stays a draft. A person switches it on.
- Write like one person talking to one customer. Plain words, one idea per email, one link.

---

Part of the free Shopify Retention Skills pack by Jake Bauman (northsignal.studio). Drafts only: a person reads everything before it goes live.
