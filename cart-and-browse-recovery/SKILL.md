---
name: cart-and-browse-recovery
description: Write abandoned cart, abandoned checkout and browse abandonment emails for a Shopify brand, led by the real objections in its reviews and support tickets instead of a discount. Use when recovery flows are missing, discount-only, or underperforming.
---

# Cart and browse recovery

## What you need
- `brand-voice.md`
- Reviews and support tickets (to find what almost stopped buyers)
- Shipping, returns and sizing policies
- Whether the store tracks Added to Cart in Klaviyo

## Steps
1. From reviews and tickets, list the top 5 reasons people hesitate, ranked by how often they appear.
2. **Abandoned checkout** (Klaviyo's standard "Abandoned Cart" flow; trigger: **Checkout Started**), 3 emails: 1 hour (did something go wrong, link back to the cart), 24 hours (answer objection one with a review line), 72 hours (answer objection two; an offer only if the brand already discounts here).
3. **Added to cart** (trigger: **Added to Cart**), 2 emails at 4 and 48 hours. Build it only if the store tracks that event. Filter out anyone who has Checkout Started since, so nobody gets both flows.
4. **Browse abandonment** (trigger: **Viewed Product**), 1 email at 24 hours: the product viewed and one thing customers say about it. No discount. Filter out anyone who has Checkout Started or Added to Cart since starting, so the stronger flow wins.
5. Flow filters on all three: Placed Order zero times since starting this flow; skip anyone who ordered in the last 14 days.

## Output
`recovery-flows.md` with the emails (3 subject lines each), the objection list they came from, and a setup sheet per flow: name, trigger, filters, delays, status draft.

## Rules that apply to every output

- Never invent customer quotes, results or numbers. If the data is missing, say so.
- Strip names, emails, phone numbers and order numbers from anything you quote.
- Everything you create in Klaviyo stays a draft. A person switches it on.
- Write like one person talking to one customer. Plain words, one idea per email, one link.

---

Part of the free Shopify Retention Skills pack by Jake Bauman (northsignal.studio). Drafts only: a person reads everything before it goes live.
