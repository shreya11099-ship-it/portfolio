---
name: ai-pm-digest
description: >
  Fetches, curates, and summarizes a daily digest of fresh articles, blog posts, and newsletters
  focused on AI product management, AI product discovery, and tools that simplify or automate PM work.
  Use this skill whenever the user asks for their daily digest, says "what's new in AI PM", asks
  about new AI product tools, wants a roundup of PM-related AI content, or says anything like
  "catch me up on AI product news". Also trigger proactively when the user starts the day and 
  mentions wanting to stay current on AI/PM trends.
compatibility:
  tools:
    - web_search
    - web_fetch
---

# AI PM Daily Digest Skill

Deliver a curated, opinionated daily digest of the freshest content across AI product management,
AI-powered product discovery, and tools that simplify or automate PM work.

---

## Step 1: Source Discovery

Search across two tiers of sources:

### Tier 1 — Trusted Newsletters & Publications (search these specifically)
- **Lenny's Newsletter** — `site:lennysnewsletter.com`
- **Product Hunt** — `site:producthunt.com` (focus on AI tools launched recently)
- **Mind the Product** — `site:mindtheproduct.com`
- **The Pragmatic Engineer** — `site:newsletter.pragmaticengineer.com`
- **Every.to** — `site:every.to`
- **a16z / Andreessen Horowitz** — `site:a16z.com`
- **Substack AI PM newsletters** — search `substack.com AI product management`

### Tier 2 — Broad Web Search
Run targeted searches such as:
- `"AI product management" article OR blog -site:linkedin.com after:YYYY-MM-DD`
- `"AI for product managers" tools 2025`
- `"product discovery" AI tools new`
- `"PM workflow automation" AI 2025`
- `new AI tools product managers`

Use today's date (or yesterday's) in `after:` filters to prioritise freshness.

---

## Step 2: Collect & Filter

For each result:
1. Fetch the page to get enough detail to evaluate it (title, intro, key claims).
2. **Skip** if: paywalled without preview, pure ad/promotional, older than ~7 days, or clearly off-topic.
3. Collect at least **5 and up to 10** distinct articles/posts before moving on.

---

## Step 3: Score Relevance

Rate each article **1–5** against the user's three interest areas:

| Score | Meaning |
|-------|---------|
| 5 | Directly and deeply relevant — must-read |
| 4 | Highly relevant, clear takeaways |
| 3 | Moderately relevant, worth skimming |
| 2 | Tangentially related |
| 1 | Weak fit — omit from digest |

**Only include articles scoring 3 or above.**

Relevance dimensions:
- **AI Product Management** — strategy, roadmapping, stakeholder alignment, AI-native PM craft
- **AI Product Discovery** — user research with AI, opportunity identification, validation, ideation tools
- **PM Productivity Tools** — tools/apps/workflows that automate or accelerate PM tasks (specs, PRDs, meeting notes, prioritisation, analytics, etc.)

---

## Step 4: Format the Digest

Output the digest in this exact structure:

---

### 🗞️ AI PM Daily Digest — [Day, Date]

**[N] articles found | Estimated read time: ~[X] min**

---

#### 🔥 Must-Reads (Score 5)

**[Article Title]**
↗ [Source Name] · [Estimated read time]
⭐ Relevance: 5/5 · *[One of: AI PM Strategy / Product Discovery / PM Tools]*

> [2–3 sentence summary in plain English. What's the core idea? What's new or interesting about it?]

**Key takeaways:**
- [Takeaway 1]
- [Takeaway 2]
- [Takeaway 3 if warranted]

**Tools/products mentioned:** [comma-separated list, or "None"]

[🔗 Read more](URL)

---

*(Repeat for each article, grouped by score tier: Must-Reads → Worth Reading → Quick Scans)*

---

#### 📦 Worth Reading (Score 4)
*(same format, slightly more compact — 2 takeaways is fine)*

---

#### ⚡ Quick Scans (Score 3)
*(just title, source, 1-sentence summary, link — no full breakdown)*

---

### 🛠️ Tools Spotted Today
A consolidated list of any new or notable tools mentioned across all articles:
- **[Tool Name]** — [one-line description] · [link if available]

---

### 💡 Today's Signal
One 2–3 sentence synthesis: what's the broader trend or theme emerging from today's content?

---

## Step 5: Delivery Notes

- Write for a busy PM who has ~10 minutes. Be crisp, opinionated, and useful.
- Summaries should highlight *so what*, not just *what*.
- If fewer than 3 articles are found after filtering, say so honestly and suggest the user check back later or widen the time window.
- Never fabricate articles. If a source returns no fresh content, skip it.
- Always include working URLs.