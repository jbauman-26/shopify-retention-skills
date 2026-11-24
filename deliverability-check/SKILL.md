---
name: deliverability-check
description: Check a Shopify brand's email deliverability basics: SPF, DKIM, DMARC, sending domain, list hygiene and a sunset policy. Use when revenue per send drops, emails land in spam or promotions more than usual, or before a big send.
---

# Deliverability check

## What you need
- The sending domain
- DKIM selector names. Get them from Klaviyo (Settings, Domains) or from the `s=` value in the DKIM-Signature header of an email the brand sent. Without them, try common ones (`kl`, `kl2`, `kl1`, `km1`, `km2`, `kt1`, `kt2`, `k1`, `google`, `selector1`, `s1`). A miss doesn't prove DKIM is absent: Klaviyo's current setup hands a sending subdomain to Klaviyo with NS records, so the DKIM record may not sit on the root domain at all. Ask which subdomain the brand sends from and check that too. If you find nothing, mark DKIM "not checked", never "fix".
- Klaviyo bounce, spam complaint and unsubscribe rates by send, last 90 days (optional)
- Google Postmaster Tools spam rate if the brand has it (optional)
- List size and how many profiles haven't clicked or bought in 180 days (optional)

## Steps
1. Look up the DNS records and report what you found, word for word. If a lookup comes back empty, retry against a second resolver (for example 1.1.1.1 and 8.8.8.8) before calling a record missing.
2. Mark each as pass, fix or missing using these tests:

| Record | Fix if |
|---|---|
| SPF | more than one SPF record; more than 10 DNS lookups (count every include, a, mx, redirect, nested ones too); an include that no longer resolves; ends in `+all` or `?all` |
| DKIM | no record at the selector; key shorter than 1024 bits |
| DMARC | no record; no `rua` reporting address. `p=none` is "review", not "fix": it is fine while setting up, but it only monitors. Move to `quarantine` once the reports are clean. |

3. Check whether the brand sends from its own branded sending domain in Klaviyo or the shared default. With a branded sending subdomain, the root domain's SPF does not cover Klaviyo mail, so a clean root SPF says nothing about Klaviyo. Say which domain each finding applies to.
4. Complaints: Google's limit is a spam rate under 0.3%, and it advises staying under 0.1%. Klaviyo's complaint rate leaves out Gmail, so use Postmaster Tools for the real number when available.
5. Size the unengaged segment (no click or order in 180 days). Recommend a two-email sunset, then suppression.
6. List fixes in order: authentication, then suppression, then send frequency.

## Output
`deliverability.md` with the pass or fix table and the records as found. For records Klaviyo must generate (branded sending domain, DKIM), point the owner to Klaviyo's Domains settings. Their values are unique to each account, so never write them yourself. DNS changes go to whoever manages the domain.

## If something is missing
Do the parts you can, mark every skipped part "not checked: <what was missing>", and list what to send next time. Never fill a gap with a guess.

## Rules that apply to every output

- Never invent customer quotes, results or numbers. If the data is missing, say so.
- Strip names, emails, phone numbers and order numbers from anything you quote.
- Everything you create in Klaviyo stays a draft. A person switches it on.
- Write like one person talking to one customer. Plain words, one idea per email, one link.

---

Part of the free Shopify Retention Skills pack by Jake Bauman (northsignal.studio). Drafts only: a person reads everything before it goes live.
