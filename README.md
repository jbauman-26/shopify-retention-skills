# Shopify Retention Skills

12 free Claude Skills that cover the work of a retention team for a Shopify brand on Klaviyo, plus 8 more from my LinkedIn series. By Jake Bauman, northsignal.studio.

A skill is a set of instructions Claude follows the same way every time. You set it up once and it does that job properly on every run.

## Install

**Claude Code:** download this repo (green Code button, then Download ZIP, or `git clone https://github.com/jbauman-26/shopify-retention-skills`) and copy the skill folders into `~/.claude/skills/` (or `.claude/skills/` inside a project). Then ask for the job in plain words, for example "audit my Klaviyo flows".

**Claude app:** open Settings, find Skills, and upload each folder as a zip. Or paste a `SKILL.md` into a chat with your files.

## Start here

1. `brand-voice-extractor` first. Every writing skill reads the file it makes.
2. `klaviyo-flow-audit` second. It tells you what to build next.
3. Then build what the audit says is missing.

## The 12

| Skill | What it does |
|---|---|
| brand-voice-extractor | Builds a one-page voice file from your site, emails and reviews |
| klaviyo-flow-audit | Finds missing flows and ranks the rest by revenue per recipient |
| welcome-flow-builder | Writes a four-email welcome flow |
| cart-and-browse-recovery | Writes recovery emails led by real objections, not discounts |
| reviews-to-post-purchase-flow | Turns reviews and tickets into a three-email post-purchase flow |
| winback-flow-builder | Times a winback flow to your real reorder cycle |
| customer-segments-rfm | Turns an orders export into five usable segments |
| campaign-calendar-planner | Plans a month of campaigns with a brief for each |
| subject-line-lab | Writes and tests subject lines in your customers' words |
| sms-flow-companion | Adds short, compliant texts to your email flows |
| deliverability-check | Checks SPF, DKIM, DMARC and list hygiene |
| weekly-retention-report | Writes a one-page Monday report with three actions |

## More skills (from the LinkedIn series)

These go beyond retention. Same rules: they write drafts and reports, and a person reads everything before it is used.

| Skill | What it does |
|---|---|
| shopify-toolkit-safe-start | Rules for using Shopify's AI Toolkit with Claude Code: read-only first, a test store second, one approved change at a time |
| marketing-engineer-scorecard | A hiring scorecard for a part-time marketing engineer: 30-day outcomes, interview questions, a paid test task |
| post-engagers-to-leads | Turns an export of LinkedIn post engagers into a short, hand-checked lead list with the drop-off at every step |
| chatgpt-store-check | Checks whether ChatGPT mentions your store and gets your facts right, then writes the fix list |
| email-sameness-check | Finds generic, AI-sounding lines in an email draft and swaps in your customers' own words |
| reviews-to-ad-concepts | Turns your reviews into ranked static ad concepts with Meta policy risks flagged |
| skills-folder-audit | Audits a Claude skills folder for duplicates, vague descriptions and contradictions. Read-only |
| founder-hat-audit | Sorts a founder's week by role and names the one job to hand off first |

## What to know

- These skills write drafts. A person reads everything before it goes live.
- They never invent customer quotes or results. If your data is thin, they say so.
- Remove card numbers, addresses and phone numbers from exports before you share them.
- They are new. I tested them on public reviews from one real store and on made-up order data, then fixed what broke. They have not been run inside a live Klaviyo account. Tell me what breaks.

If you'd rather have this built and tested on your store, northsignal.studio/contact is the door. If now isn't the time, the skills are yours either way.
