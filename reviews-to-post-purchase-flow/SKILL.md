---
name: reviews-to-post-purchase-flow
description: Turn a Shopify brand's product reviews and support tickets into a three-email Klaviyo post-purchase flow written in the customers' own words. Use when someone hands over a reviews export (Judge.me, Okendo, Yotpo, Shopify Product Reviews) and wants post-purchase emails, subject lines, or a flow plan.
---

# Reviews to post-purchase flow

A free skill from Jake Bauman (northsignal.studio). Give this file to Claude Code, Claude or any coding agent along with your exports, and say "build my post-purchase flow."

Your reviews already say why people bought, what almost stopped them and what they wish they'd known. This skill reads them and writes the flow from those words, instead of from your past campaigns.

## What you need

1. **reviews.csv.** Export every review from your reviews app (Judge.me, Okendo, Yotpo or Shopify Product Reviews). Keep the rating, the review body, the product and the date.
2. **tickets.csv** (optional, recommended). Your last 100 or so support tickets or customer emails, with the message body. Remove card numbers, addresses and phone numbers first.
3. `brand-voice.md` from the brand-voice-extractor skill. If you don't have one: your brand name, your main product or category, and one sentence on how your brand talks.

4. The brand's care, safety and usage instructions (a product page or care label is enough), so customer tips can be checked against them.

If a file is missing, say so and continue with what you have. Never invent customer quotes.

## Step 1. Read and clean

- Load both files. Count rows and report them back.
- Drop anything that is only a star rating or says nothing specific ("great!", "love it"). Keep any line that names at least one of these: a product detail, a use, a reason for buying, a doubt, a problem, a comparison or a tip. A six-word line can be the best one you have.
- Leave out reviews marked as gifted, sponsored or from a partner, or keep them in a separate list. Don't quote them as ordinary customers.
- Remove duplicates: the same text more than once counts once.
- Strip customers' names, emails, phone numbers, order numbers and addresses from every line you keep. The brand's own published names (the founder, the team) can stay. Customer words go into emails, customer identities do not.
- If there are more than 2,000 rows, sample the newest 1,000 plus every 1 and 2 star review.

## Step 2. Sort every line into four piles

Tag each review or ticket sentence with one or more of these:

| Pile | What goes in it |
|---|---|
| **Why they bought** | The trigger, the job, the gift, the problem they had |
| **What almost stopped them** | Price, shipping, size, doubt, a competitor, timing |
| **How they use it** | When, where, how often, with what, for whom |
| **What they wish they'd known** | Setup tips, sizing, care, the "if only I had..." lines |

For each pile, return:
- up to 5 themes that show up, each with a count. If a pile has fewer than 5 real themes, report the ones it has. Never pad. Say when a pile is thin (it usually is without support tickets).
- up to 3 short verbatim phrases per theme (under 12 words each), copied exactly. Count each customer once per theme, so one person repeating themselves doesn't inflate it.
- one line on what this means for the emails

The two piles that write the best emails are usually **what almost stopped them** and **what they wish they'd known**. Call out the strongest theme in each.

## Step 3. Write three emails

Trigger: Klaviyo **Placed Order** (or Fulfilled Order if shipping takes more than 5 days).

| Email | Send | Job | Built from |
|---|---|---|---|
| 1. What to expect | Day 2 | Confirm they chose well, set expectations, answer the top doubt before it becomes a ticket | What almost stopped them + why they bought |
| 2. What people wish they knew | Day 10 (or 3 days after delivery) | The single most useful tip from reviews, so the first use goes well | What they wish they'd known |
| 3. How other customers use it | Day 25 | Two or three real uses as the story; the one link is the review ask | How they use it |

The day timings are a starting point. Adjust to your delivery time and how fast customers use the product.

For each email, write:
- 3 subject line options. At least one uses a verbatim customer phrase.
- Preview text
- Body, 90 to 150 words, plain and warm, one idea, one link
- The customer phrases you used, with the pile they came from

Writing rules:
- Write like one person talking to one customer. No "Dear valued customer", no "we're thrilled".
- Use customer phrases as written. Do not polish them into marketing language.
- No discount in emails 1 and 2. If the brand runs a loyalty or referral program, mention it once in email 3.
- No claims the reviews don't support. If a review says "lasted two years," don't write "lasts forever."
- Match `brand-voice.md`, or the voice sentence the owner gave you.
- Check every customer tip against the brand's own care, safety and usage instructions before you repeat it. If a review recommends something the brand advises against, leave it out and flag it.

## Step 4. Build the flow in Klaviyo

Return a build sheet the owner (or an agent with Klaviyo API access) can follow:

1. Flow name: `Post-purchase | from reviews | v1`
2. Trigger and filters: Placed Order. To keep repeat buyers out of the first-order story, add the flow filter "Placed Order equals 1 over all time" (first-time buyers only). Don't filter on "ordered in the last 30 days": the order that starts the flow would count and shut everyone out. Have the owner confirm the filter with a test profile before going live. Note the trade-off: a customer who reorders before day 25 leaves the flow and misses the review ask, so cover them with a separate review request.
3. Time delays between emails as set above.
4. Smart sending on.
5. Status: **draft**. A human reads every email before the flow goes live.

If you have Klaviyo API access, create the flow and templates as drafts only. Never set a flow to live.

## Step 5. Human review checklist

Before anyone switches the flow on, check:

- [ ] Every customer quote is real and appears in the export
- [ ] No names, order numbers or personal details from reviews made it into an email
- [ ] Each email has one idea and one link
- [ ] Subject lines read like a person, not a promo
- [ ] Nothing promises a result the reviews don't back up
- [ ] The tone matches how the brand actually talks

## Step 6. Grade it after 60 days

Email 3 sends on day 25, so 30 days is too early to judge. At 60 days, track these against your current post-purchase flow (or against no flow):

- **Repeat purchase rate** for customers who entered the flow
- **Revenue per recipient** for each email
- **Review submission rate** from email 3
- Reply rate, if replies go to a real inbox

Don't judge it on open rate. Apple Mail Privacy Protection inflates opens, so they say little about whether the email worked.

If the list is big enough, keep 10% of new buyers out of the flow for the first 60 days so there is something to compare against. Rewrite the weakest email first. Re-run steps 1 and 2 every quarter as new reviews come in.

## Output

Deliver one markdown file, `post-purchase-flow.md`, containing:
1. Row counts and what was dropped
2. The four piles with themes, counts and verbatim phrases
3. The three emails with subject options, preview text and body
4. The Klaviyo build sheet
5. The review checklist

---

Built by Jake Bauman. I post one AI marketing build for Shopify brands like this regularly on LinkedIn. If you'd rather have this built and tested on your store, northsignal.studio/contact is the door. If now isn't the time, the skill is yours either way.
