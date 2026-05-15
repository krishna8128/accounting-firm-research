# Indian Accounting Industry — 3-Hour Crash Course

> A shared learning sprint for teammates building AI products/services in the accounting space. Designed for non-accountants (engineers, designers, ops) who need enough domain fluency to (a) understand customers, (b) ask intelligent questions in discovery calls, (c) spot wedges and pain points.

**Time required:** 3 hours of focused work.
**Output:** A one-page cheat sheet you fill in as you go — this IS the deliverable.
**Best done:** Block on calendar, headphones, no Slack.

---

## Why we're doing this

We're building AI products/services for accountants. None of us are CAs. Our biggest constraint right now isn't tech — it's domain ignorance. We need enough vocabulary, mental model, and pain-point awareness to:

- Not sound naive on customer discovery calls
- Recognize a wedge when we hear one
- Distinguish real pain from polite venting
- Speak the language well enough to be trusted

Content alone won't get us there — talking to actual CAs will. But content is the warmup that makes the conversations 10× more productive. This 3-hour sprint is that warmup.

---

## Pre-flight (5 min)

Open a new doc titled `MyName-IndianAccountingNotes.md`. Three sections to fill:

1. **Glossary** — target 40+ terms by the end
2. **Firm taxonomy** — Big 4 → mid-tier → local, with named examples
3. **Workflows + pain points** — the work cycles and what's broken

If you don't fill the doc, you didn't actually learn. Treat it as the deliverable, not the schedule.

---

## Block 1 — Industry Structure (60 min)

**Goal:** Know who plays at what level and what they do.

### 0:00–0:15 — Industry overview video

Open YouTube. Search and pick ONE:

- "Big 4 vs Mid-Tier CA Firms India"
- "Day in the life of a CA in India" — any vlog, pick one at a Big 4 if possible
- CA Sundaram or CA Rachana Ranade on the CA profession structure

Take notes on: roles (article assistant → senior → manager → partner), service lines (audit/tax/advisory), how firms are organized.

### 0:15–0:30 — The CA system

Wikipedia + ICAI website. Speed-read:

- **ICAI** (Institute of Chartered Accountants of India) — the regulator + professional body. ~4 lakh CAs in India.
- **CA exam path:** CA Foundation → CA Intermediate → 3-year **articleship** (mandatory training) → CA Final → membership.
- **Articleship is the key concept.** CA students working at firms for ₹15K–₹25K/month doing grunt work (data entry, recs, basic audit prep, tax return prep). This is where most "AI replacement" headroom exists — but firms get the labor cheap, so the economics differ from US.

### 0:30–0:45 — Big 4 India + their structure

Each Big 4 operates in India via TWO entities — an Indian audit firm + a Global Delivery Center.

| Global brand | India audit firm | India GDC (serves global) |
|---|---|---|
| Deloitte | Deloitte Haskins & Sells | Deloitte USI (~80,000+ employees) |
| PwC | Price Waterhouse & Co (PW & Co) | PwC AC India + Service Delivery Center |
| EY | S.R. Batliboi & Co (SRBC) | EY GDS (~70,000+ in India) |
| KPMG | B S R & Co | KPMG Global Services (KGS) |

- **GDS / USI / GDC side** = offshore work for the global firm (audit support, tax prep, transformation projects). Serves global clients via India staff.
- **Audit firm side** = serves Indian clients (Reliance, Tata, Infosys, etc.) with statutory audits + tax + advisory.
- These are functionally two different businesses inside the same brand.

### 0:45–1:00 — The next tier down

Skim 1 page each:

- **Indian Big 5 challengers** — Nangia & Co, Nexdigm (aggressive growth, modern positioning)
- **Mid-tier with global affiliations** — Walker Chandiok (Grant Thornton Bharat), BDO India, RSM India, Crowe Mak Gulati, Baker Tilly DHC
- **Strong Indian mid-tier** — ASA & Associates, Lodha & Co, N.A. Shah Associates, Khimji Kunverji
- **Local / small firms** — ~1.5 lakh small CA firms across India, mostly 1–10 partners. Long tail.

**Update your cheat sheet:** firm taxonomy with 4 tiers (Big 4 → Indian Big 5 → mid-tier with global tie-ups → local).

---

## Block 2 — The Work (60 min)

**Goal:** Know what CAs actually do day-to-day. This is where wedges hide.

### 1:00–1:20 — The compliance calendar

Read 2 articles (ClearTax blog is the best source):

**GST monthly cycle:**
- GSTR-1 (outward supplies) by 10th of next month
- GSTR-2A / GSTR-2B (auto-populated inward supplies) — reconciliation against books
- GSTR-3B (summary return + payment) by 20th
- Annual: GSTR-9 (annual return), GSTR-9C (reconciliation statement for businesses > ₹5cr turnover)

**TDS quarterly cycle:**
- Form 24Q (salary), 26Q (non-salary residents), 27Q (non-residents)
- Deadlines: 31 Jul, 31 Oct, 31 Jan, 31 May

**Income Tax cycle:**
- Advance tax (quarterly) — 15 Jun, 15 Sep, 15 Dec, 15 Mar
- ITR filing — 31 Jul (individuals, no audit), 31 Oct (audited cases), 30 Nov (with transfer pricing)

**Statutory audit cycle:**
- Year-end typically 31 Mar
- Audit Apr–Sep
- AGM by 30 Sep
- ROC filings: AOC-4 (financials) within 30 days of AGM, MGT-7 (annual return) within 60 days
- Tax audit (Section 44AB) — required if turnover > ₹1cr (business) or ₹50L (profession)

**This calendar IS the work.** Every CA firm runs on this cycle. Every pain point you hear in customer discovery will map to a step in this calendar.

### 1:20–1:40 — Service line breakdowns

Skim Big 4 India service-line pages. Understand:

- **Audit & Assurance** — statutory audit, tax audit, internal audit, IFRS conversion, SOC reports, agreed-upon procedures
- **Tax** — direct (income tax + transfer pricing), indirect (GST + customs), international (DTAA, expatriate tax, M&A tax)
- **Advisory** — deals, valuation, M&A, due diligence, forensic
- **Consulting / Transformation** — tech, ops, risk consulting, ESG

### 1:40–2:00 — Listen to one long-form CA podcast (at 1.5×)

Search Spotify/YouTube for:

- **The Finance Story** — Indian CA-founder interviews. Pick one Big 4 partner + one boutique firm founder.
- **Zerodha Daily Brief** episodes on accounting/tax/regulations
- Any 30–60 min interview with a mid-tier firm partner

**Listen for:**
- What they complain about
- What they say is changing
- What tools they mention by name
- The vocabulary they use unconsciously

**Update your cheat sheet:** compliance calendar diagram, 4 service lines, 5 pain points you heard from the podcast.

---

## Block 3 — Tools & Pain Points (60 min)

**Goal:** Know the tech stack so you don't sound naive in calls.

### 2:00–2:20 — Tally Solutions

Watch a Tally Prime walkthrough on YouTube (15 min). You need to understand:

- It's the dominant accounting software in India (~70%+ SMB share)
- Used by 90%+ of small/mid CA firms for client books
- ~₹500cr+ revenue, profitable, family-owned, near-monopoly status
- Data model: vouchers (sales, purchase, payment, receipt, journal, contra)
- Standard reports: trial balance, P&L, balance sheet, day book, ledgers
- File format is proprietary; getting data IN/OUT is the eternal pain
- **No open API** — this is Tally's moat and everyone else's constraint
- "Tally connector" market is a whole ecosystem (Excellytics, Suvit, others)

### 2:20–2:40 — Other tools in the stack

Scan product pages, 3-5 min each:

| Tool | What it does | Who uses it |
|---|---|---|
| **Zoho Books** | Cloud-native accounting | Tally's main challenger, open API, growing SMB share |
| **Busy** | Accounting software | Tally competitor, common in tier-2/3 cities |
| **Marg ERP** | Accounting + inventory | Pharma, retail, distribution segments |
| **Vyapar / KhataBook** | SMB record-keeping app | Mobile-first SMBs, kirana stores |
| **ClearTax (Defmacro)** | GST + ITR + TDS filing | Both individuals AND CA firms; raised $140M+ |
| **KDK Spectrum** | Tax software for CA firms | Deep pro segment penetration |
| **Saral / Genius** | Tax + payroll for CA firms | Mid-tier, less marketing |
| **GSTN portal** | Government GST filing | Mandatory; notoriously slow + buggy |
| **Income Tax e-filing portal** | Government ITR portal | Mandatory; UX has improved post-2023 redesign |
| **MCA portal** | Ministry of Corporate Affairs (ROC filings) | Mandatory; UX is famously bad |

### 2:40–3:00 — Pain-point reading

Skim 3 sources:

- Quora / Reddit r/IndianCharteredAccountants — search "articleship reality" or "worst part of being a CA"
- Search "Why GST reconciliation is hell" or "GSTR-2B mismatch issues"
- Inc42 / YourStory coverage of Indian accounting tech startups (ClearTax, Razorpay's RazorpayX, Recko's exit to Stripe, Khatabook's wind-down) — note what's been tried and what failed

**Update your cheat sheet:** Tools table with what each does, 10 specific pain points you can name.

---

## Cheat Sheet Template (fill as you go)

Copy this template into your notes doc. By the end of 3 hours, every section should have content.

```markdown
# My Indian Accounting Cheat Sheet
Started: [date]

## Glossary (target: 40+ terms)
- TDS — Tax Deducted at Source. ...
- TCS — ...
- GSTR-1 — ...
- GSTR-2A / 2B — ...
- GSTR-3B — ...
- GSTR-9 / 9C — ...
- ITR-1 through ITR-7 — different return forms for different taxpayers
- Form 16 — ...
- Form 26AS — ...
- Section 44AB — tax audit threshold
- Section 44AD / 44ADA — presumptive taxation
- AOP, HUF, OPC, LLP, OPC, Partnership, Pvt Ltd — entity types
- MAT, AMT — minimum alternate tax
- Articleship — ...
- ICAI, ICSI, ICMAI — professional bodies (CA, CS, CMA respectively)
- Statutory audit vs Tax audit vs Internal audit — distinctions
- ROC, MCA, AOC-4, MGT-7 — corporate filing terms
- Transfer pricing — when applicable
- DTAA — Double Taxation Avoidance Agreement
- Voucher types in Tally — sales, purchase, payment, receipt, journal, contra
- ...

## Firm Taxonomy
### Tier 1: Big 4 (audit + GDC dual structure)
- Deloitte (Haskins & Sells) + Deloitte USI
- PwC (PW & Co) + PwC AC India
- EY (SRBC & Co) + EY GDS
- KPMG (B S R & Co) + KPMG Global Services

### Tier 2: Indian Big 5 challengers + global mid-tier
- Nangia & Co — ...
- Nexdigm — ...
- Walker Chandiok (Grant Thornton Bharat) — ...
- BDO India — ...
- RSM India — ...

### Tier 3: Strong Indian mid-tier
- ASA & Associates
- Lodha & Co
- N.A. Shah Associates
- Khimji Kunverji

### Tier 4: Long tail (~1.5 lakh small firms)
- 1–10 partner firms across all cities

## Compliance Calendar
### Monthly
- 10th: GSTR-1
- 20th: GSTR-3B
- ...

### Quarterly
- ...

### Annual
- ...

## Service Lines
- Audit & Assurance: ...
- Tax (Direct + Indirect + International): ...
- Advisory: ...
- Consulting / Transformation: ...

## Tech Stack
| Tool | What | Who uses |
|------|------|----------|
| Tally Prime | ... | ... |
| Zoho Books | ... | ... |
| ...

## Top 10 Pain Points (collect as you go)
1. ...
2. GST reconciliation hell — mismatch between GSTR-2A/2B and books
3. ...
4. ...

## Questions I have / Things I don't understand
- ...
- ...
```

---

## After the 3 Hours — The Action That Doubles Your ROI

Content alone won't make you fluent. **Book 2 calls with real CAs within 48 hours of finishing this sprint.** Warm intros if you have them; LinkedIn cold outreach if not.

Use this opener:

> "I've been studying the industry but I want to understand YOUR firm specifically. Could you walk me through last week — what took the most time, what you wish was easier?"

3 hours of content + 1 hour of real conversation > 10 hours of content alone. The content lets you ask intelligent questions; the conversation is where you actually learn.

After each call, update your cheat sheet with:
- New terms you heard
- Specific pain points (with exact phrasing)
- Tools the person mentioned by name
- Questions you couldn't answer in the moment

---

## Optional Extensions (if you finish early or want to go deeper)

- **History of Indian accounting tech** — Search Inc42, YourStory, ET Tech for ClearTax, Vyapar, KhataBook, Refrens, Recko coverage. Understand what's been tried (and failed).
- **GST history** — How the 2017 rollout reshaped CA workflows; ClearTax's role.
- **Big 4 GDS economics** — How offshored audit/tax actually works; arbitrage on labor cost.
- **Tally moat** — Why no one has dethroned Tally; what Zoho Books has done well.
- **Articleship economics** — Why firms hire articles cheap, how it shapes incentives.
- **ICAI politics + 2025 regulatory changes** — Recent CA Act amendments, multi-disciplinary partnerships, foreign firm entry rules.

---

## When you've completed this

You should be able to:

- [ ] Name 4 firm tiers with 3+ examples in each
- [ ] List 10+ pain points specific to Indian accounting
- [ ] Define 40+ terms without looking them up
- [ ] Draw the monthly + annual compliance calendar from memory
- [ ] Name 5 tools in the stack and what each does
- [ ] Recognize the difference between statutory audit, tax audit, and internal audit
- [ ] Explain what an article assistant does day-to-day
- [ ] Identify 3 hypothesis-grade wedges you'd want to test in customer discovery

If you can't yet, keep filling the cheat sheet until you can. Then go book those calls.
