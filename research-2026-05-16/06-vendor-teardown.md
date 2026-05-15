# Vendor Teardown: AI x Accounting Landscape — May 2026
## Verb-Level Deep Dive for Indian Founder Building Accounting AI

**Author note:** This is a verb-level teardown. Each vendor is reduced to the actual mechanical work it performs, the ICP it sells to, what it explicitly does NOT do, and India-relevance. I'm intentionally skeptical of "AI for X" slogans — I marked which companies are forms-and-rules wrappers and which are genuinely autonomous.

---

## SEGMENT 1: AI-NATIVE FIRM-OS PLATFORMS (Selling To Top-100 CPA Firms)

These are the "OS for the audit/tax firm" plays. They are NOT trying to replace the CPA. They are trying to be the practice's source of truth + agentic execution layer, sold seat-by-seat at the partner level.

### 1. Basis ($1.15B valuation, Series B Feb 2026, Accel/GV/Khosla)

**The verb:** Basis *executes structured multi-step tax and accounting workflows end-to-end inside a CPA firm's existing systems* — specifically completing a 1065 partnership return workbook from raw documents to filable workbook.
**ICP:** Top-25 US CPA firms (30% penetration). Audit/tax/advisory practitioners at mid-large firms.
**Pricing:** Not public. Enterprise contracting. Likely $5-15K per seat ACV based on Accel-stage unicorn unit economics.
**Founders:** Mitch Troyanovsky + Matt Harpe (ex-Volley AI). Raised $34M Series A May 2024, then $100M Series B Feb 2026.
**Does NOT do:** SMB direct, India compliance, GST/TDS, audit working papers (focuses on tax + advisory). Not a bookkeeping engine — depends on QBO/Sage being upstream.
**Customer wins:** 30% of top-25 US firms. 20-50% efficiency gain claim.
**India-relevance:** Zero direct. Could be a model for India tier-2/3 firms.

### 2. Fieldguide ($700M valuation, Series C Feb 2026, Goldman Sachs)

**The verb:** Fieldguide *runs audit engagements end-to-end* — generates and analyzes documents, auto-associates workpapers, executes test procedures, runs compliance checks across the audit lifecycle.
**ICP:** 50% of top-100 US CPA firms including Big Four. Audit & advisory specifically (not tax-first).
**Pricing:** Enterprise. Estimated $200K-$2M per firm annually.
**Founders:** Jin Chang (CEO, ex-Workfront), Andrew Levy. Backed by Bessemer, 8VC, Thomson Reuters Ventures, Geodesic, Goldman.
**Does NOT do:** Tax prep, bookkeeping. They explicitly went audit-first. No SMB.
**Customer wins:** Half of top-100 US firms; 30-40% efficiency lift reported. Claim: 10-person audit team becomes 3-person within "a few years."
**India-relevance:** Could displace work done by Indian Big Four GDS audit teams. Threat, not opportunity.

### 3. Aiwyn ($113M Series B Dec 2024, KKR/Bessemer)

**The verb:** Aiwyn *automates the revenue cycle and engagement lifecycle for accounting firms* — engagement letters, billing, payments, client portal, time entry.
**ICP:** Top-500 IPA firms, 100+ staff. Mid-large CPA practices.
**Pricing:** Per-seat enterprise. Multi-product expansion (intelligent engagement letters, client portal, payments).
**Founders:** Justin Adams (CEO). Total funding ~$159M.
**Does NOT do:** Tax prep, audit, bookkeeping. It's the cash-and-engagement layer, not the work-doing layer. Not displacing professional labor — it's displacing back-office admin.
**India-relevance:** Has comp in Indian CA practice mgmt (HostBooks, Practice CS).

### 4. Karbon + Aider (acquired Sep 2025)

**The verb:** Karbon *coordinates work across the firm* (practice mgmt). Post-Aider acquisition: *automates period close and AI-powered management reports for bookkeeping clients*.
**ICP:** Mid-market global firms, $59-$89/user/month. 4-200 person firms in US, UK, AU, NZ.
**Pricing:** Team $59/user/month annual, Business $89/user/month annual, Enterprise custom.
**Founders:** Stuart McLeod, Ian Vacin. Owned by US PE (Five Elms).
**Does NOT do:** Tax prep, audit work. Focused on workflow + collaboration + (post-Aider) management reporting.
**India-relevance:** Used by some India-based offshore CPA firms. Doesn't speak GST/TDS.

### 5. TaxDome (private, profitable, no major VC funding disclosed)

**The verb:** TaxDome *manages the client side of a tax/accounting practice* — onboarding, document collection, e-signatures, secure messaging, billing.
**ICP:** Solo to mid-size accounting firms (avg <50 employees). 10,000+ firms worldwide.
**Pricing:** Essentials $800/user/yr; Pro $1,000/user/yr; Business $1,200/user/yr (US).
**Does NOT do:** Tax preparation itself, audit, bookkeeping. Pure practice ops.
**India-relevance:** Used in India by some firms but lacks GST/ITR depth.

### 6. Canopy ($70M Series C April 2025, Viking Global)

**The verb:** Canopy *unifies practice management for mid-large accounting firms* — proposal-to-payment workflow, document mgmt, time & billing, engagement letters.
**ICP:** "Medium and large accounting firms" (their language). 4,000+ firms.
**Pricing:** Modular per-product, $40-$70/user/month typical.
**Founders:** Davis Bell (CEO). Total funding ~$150M+.
**Does NOT do:** Audit work, tax prep. Closest to TaxDome but more upmarket.

### 7. Accrual ($75M launch Feb 2026, General Catalyst)

**The verb:** Accrual *unifies AI-driven preparation AND review into a single workflow for accounting firms* — automates manual prep work while preserving CPA-level controls and auditability.
**ICP:** Mid-large CPA firms. Built by Stripe/Brex finance-infra alumni.
**Pricing:** Not public. Enterprise.
**Founders:** Cosmin Nicolaescu (ex-Stripe CTO).
**Does NOT do:** Direct-to-SMB. Compliance products. Explicitly firm-first.
**India-relevance:** Threat to India Big Four GDS prep work.

### 8. Modus ($85M April 2026, Lightspeed)

**The verb:** Modus *acquires audit-first CPA firms and embeds AI into their working papers and engagements* — a roll-up. Owns 1 firm with $30M revenue already.
**ICP:** Top-200 IPA firms via M&A.
**Founders:** Arush Jain, Pranav Pillai, Vinay Kasat (ex-Palantir, Ramp, Bridgewater).
**Does NOT do:** Sell to firms it doesn't own. This is a private-equity-meets-AI roll-up, not a SaaS.
**India-relevance:** ICAI doesn't allow outside ownership of audit firms — this model can't replicate in India. Huge structural moat for an Indian play.

---

## SEGMENT 2: VERTICAL-VERB AI AGENTS

These are single-verb agents — they do ONE thing autonomously and deeply.

### 9. Black Ore — Tax Autopilot (GA April 2026)

**The verb:** Black Ore *prepares US business tax returns end-to-end* — ingestion → extraction → return prep → workpaper generation → software integration. CPA reviews, no Black Ore employee touches returns.
**ICP:** Small/mid CPA firms + large firms doing 10,000s of returns. 40% of top-20 CPA firms in early access. Onboarded 75 of 4,000 waitlist.
**Pricing:** Contact-only. Cost reduction "up to 80% per return" claim. Likely tiered per-return (estimated $20-100 per simple return based on category).
**Does NOT do:** Audit, bookkeeping, advisory, individual 1040s (focus is on business returns; 1065/1120 lineage). India returns.
**Performance claim:** 99% accuracy, 98% autonomy rate, 98% time savings.
**India-relevance:** Could be model for India ITR-3/ITR-5 autopilot for CA firms.

### 10. Filed ($17.2M May 2025, Northzone)

**The verb:** Filed *automates the drudgery of tax preparation* by integrating into existing tax workflows (similar surface to Black Ore but earlier stage).
**ICP:** US accounting firms.
**Founders:** Andrew Argue.
**Does NOT do:** Audit, bookkeeping.
**India-relevance:** Zero.

### 11. Numeric ($51M Series B Nov 2025, IVP) — $89M total

**The verb:** Numeric *closes the books for in-house corporate finance teams* — period close automation, reconciliations, financial reporting, flux analysis. Cash management product launched 2025 with 90%+ auto-match.
**ICP:** Mid-market and enterprise corporate finance teams (NOT CPA firms). Series B+ companies, public companies.
**Pricing:** Estimated $30-100K ACV based on Series B unit economics.
**Founders:** Parker Gilbert (CEO, ex-Vetri), Dennis Yang.
**Does NOT do:** Tax prep, audit, firm-side workflow. Direct competitor to FloQast.
**India-relevance:** Could be useful for India GCC F&A teams.

### 12. Petual ($20M April 2026, a16z + First Round + Elad Gil)

**The verb:** Petual *tests SOX controls for enterprise internal audit teams* — evidence gathering, workpaper creation, control testing. Handles unstructured inputs (screenshots, PDFs, Excel).
**ICP:** S&P 500 and NASDAQ 100 in-house internal audit teams (NOT external auditors).
**Pricing:** Enterprise. 68-80% efficiency gain on SOX workflows claim.
**Does NOT do:** External audit, financial statement audit, tax, bookkeeping.

### 13. Andera (PearX Summer 2024)

**The verb:** Andera *automates SOX testing* — control testing, exception management, evidence gathering for public-co audit teams and external auditors.
**ICP:** Public accounting firms + in-house IA. Claims 70% cost savings.
**Founders:** Aryo Patel, Tinah Hong.

### 14. Arden (YC W26)

**The verb:** Arden *runs end-to-end SOX ITGC and BPC testing in one engine* — pulls evidence from Okta/Workday/NetSuite, tests controls, generates reviewer-ready workpapers.
**ICP:** Internal audit + SOX teams at public/pre-IPO co's.

### 15. Oxus (YC W26)

**The verb:** Oxus *automates internal audit workflows* — scoping, documentation, control testing for pre-IPO and public co's. Customers include payroll providers and biotechs.
**ICP:** Internal audit teams at pre-IPO + public companies (saves outsourcing fees).
**Founders:** Janet, Christine, Melinda (MIT team).

### 16. Midship (acquired by Optro/AuditBoard May 2026)

**The verb:** Midship *generated SOX testing workpapers and ran attribute tests autonomously* — bank recons, access reviews. Up to 87% of SOX program mgmt automated.
**ICP:** Internal audit teams. Now part of Optro stack.

### 17. Moby Analytics (YC X25)

**The verb:** Moby *lets financial auditors deploy no-code AI agents across revenue/payroll/inventory/fixed asset workflows*.
**ICP:** External audit teams at boutique-to-mid firms.
**Geography:** Paris.

### 18. Combinely (YC X25, $500K Seed)

**The verb:** Combinely *acts as an AI co-worker for accountants* — drafts emails, reviews tax work, produces first-draft rental/self-employment income statements, runs quality checks.
**ICP:** UK accountancies (Burgess Hodgson early customer, 150 staff).
**Founders:** Tom Invernizzi (ex-Deloitte), Arthur Granacher (ex-Google DeepMind).

### 19. Materia → Thomson Reuters (Oct 2024)

**The verb (pre-acquisition):** Materia *answered tax research questions and automated tax-research workflows*.
**Wedge:** Specialist agentic AI for tax/audit research — Thomson Reuters bought it to keep its CCH Axcess + Checkpoint moat against Harvey-style legal-AI encroachment on tax.

---

## SEGMENT 3: SMB-DIRECT BOOKKEEPING & SERVICE PLAYS (The "AI Accountant for SMBs" Cluster)

This is the most crowded segment. Almost all are 2020-2024 vintage, fighting Pilot, fighting Intuit, fighting each other.

### 20. Pilot.com ($1.2B valuation 2021, ~$43M ARR 2023, ~$27M reported revenue 2024)

**The verb:** Pilot *delivers human bookkeepers + tax prep + outsourced CFO services for US startups*, with software glue.
**ICP:** US startups Seed-Series C. Has ~1,700 customers, ARPU ~$25K.
**Pricing:** $500-5K/month per customer.
**Founders:** Waseem Daher, Jessica McKellar, Jeff Arnold (ex-Dropbox infra).
**State of business:** Mature, growing 30% YoY. Distinctly NOT an AI-first play. Their AI motion is defensive.
**Does NOT do:** True autonomous bookkeeping. It's a service company with software. Big incumbent risk in 2026: Ramp Accounting Agent + Brex (now Capital One) make Pilot's wedge harder.

### 21. Ramp Accounting Agent (launched Feb 2026)

**The verb:** Ramp *auto-codes every transaction across GL/department/class/location, reviews policy adherence, and auto-syncs ready transactions to NetSuite/QBO/Xero/Sage*.
**ICP:** Existing Ramp Plus customers (mid-market). Available with $15/user/month base.
**Performance:** 3.5x more auto-coded transactions vs. legacy; 98% accuracy on "ready to sync"; 70% fewer corrections after 1 month.
**Does NOT do:** Tax. Audit. Multi-entity consolidation beyond what NetSuite handles. Sit outside Ramp ecosystem.
**Threat level:** This is the most dangerous SMB AI agent in 2026 because it has the data moat (the card transactions). Black Ore prepares the return; Ramp owns the bookkeeping that feeds it.

### 22. Intuit Assist (default in QBO since Sep 30 2025)

**The verb:** Intuit Assist *runs an Accounting Agent, Payments Agent, and Business Insights Agent inside QBO* — auto-fills bills/expenses from email dropping, matches payments, reminds on invoices, answers NL questions about the business.
**ICP:** Every QBO user globally. Default-on. Embedded in plans.
**Pricing:** Bundled.
**Does NOT do:** Hard tax research. Audit. Complex multi-entity. Genuine end-to-end close.
**Significance:** This is the carpet under everyone selling "AI bookkeeping for SMBs." Truewind, Zeni, Puzzle, Mesh all have to be 5-10x better to justify the seat.

### 23. Xero JAX (announced 2025, expanded April 2026)

**The verb:** Xero JAX *automates bank recs, data entry, payments, and pays bills via email/WhatsApp commands*. JAX Assure layer reduces hallucinations.
**ICP:** Xero's SMB base — heavy in AU/NZ/UK, growing in US.
**India-relevance:** Some Indian SMBs on Xero.

### 24. Sage Copilot

**The verb:** Sage Copilot *surfaces anomalies, flags unusual transactions, identifies cash-flow issues, categorizes data, and processes receipts*.
**ICP:** Sage Intacct / Sage 50 mid-market.

### 25. Truewind ($17.5M total, Founder Fund/Y Combinator W23)

**The verb:** Truewind *combines AI + concierge bookkeepers for US startups* — categorization, financial modeling.
**ICP:** US startups, pre-Series B.
**State:** Active. Smaller scale than Pilot/Zeni.

### 26. Zeni ($50.9M total, 437 employees Mar 2026)

**The verb:** Zeni *delivers AI bookkeeping + finance concierge for SaaS startups*. Launched AI Accounting Agent Nov 2025, Zeni Treasury Jan 2026, business debit card with built-in AI financial mgmt.
**ICP:** SaaS startups, mid-stage.
**State:** Alive, growing, expanding into card + treasury. Compound product strategy.

### 27. Puzzle.io ($66.5M+ total)

**The verb:** Puzzle *delivers GL + AI categorization for API-stack startups (Stripe/Brex/Gusto integrations native)*.
**ICP:** Technical startup teams comfortable with API-first finance.
**Pricing:** $43/mo starter, $250/mo advanced, free under $5K monthly expenses.

### 28. Mesh ($139M total)

**The verb:** Mesh *eliminates manual accruals* — captures real-time usage/service signals from AP inboxes/Slack/Teams/historical journals to auto-build accrual entries.
**ICP:** Series B+ startups with multi-system clutter.
**Founders:** Nandini Ramakrishnan + Erin Kim. Notable — Indian co-founder.

### 29. Afternoon.co (YC W26)

**The verb:** Afternoon *pairs AI bookkeeping + tax services with real-time financial metrics for founders*.
**ICP:** Pre-seed/seed founders.
**State:** Tiny, just launched.

### 30. Balance (YC W26, "Launch YC: Balance — AI accounting firm for SMBs")

**The verb:** Balance *closes the monthly books for SMBs* via AI agents that ingest business context, categorize, reconcile, surface anomalies in real time, with humans signing off.
**ICP:** US SMBs.

### 31. Minerva (YC X25)

**The verb:** Minerva *automates end-to-end business accounting* — categorization → bookkeeping → reconciliation → tax-ready reports → filings.
**ICP:** SMBs.

### 32. Cranston AI (YC F25)

**The verb:** Cranston *runs the full stack of AI accounting for startups & SMBs* — recon, tax compliance, financial analysis. $21.5K MRR in first 60 days post-launch.
**ICP:** US startups + SMBs.

### 33. FullSeam (YC W26)

**The verb:** FullSeam *logs into existing accounting tools and does AR/AP work* — vendor/customer comms, payment recording, financial record updates.
**ICP:** Corporate accounting teams (NOT firms).

### 34. Finta

**The verb:** Finta *simplifies tax + bookkeeping + financial-metric tracking* on one platform for founders.
**ICP:** Solo founders.
**State:** Active but quiet.

### Consolidation Pattern in SMB-Direct

- Pilot is profitable-ish ($27-43M ARR) but stalling.
- Zeni is the most product-aggressive (cards, treasury).
- Mesh and Puzzle are well-funded but unproven at scale.
- Truewind, Finta, Afternoon, Minerva, Balance, Cranston are sub-$1M ARR.
- Ramp Accounting Agent + Intuit Assist threaten the entire bottom of the cluster.
- **Likely outcome 2026-27:** Half of these will die or be acqui-hired. Survivors will pivot to (a) firm-tooling, or (b) thick vertical (e.g., e-comm or healthcare books).

---

## SEGMENT 4: AUDIT & GRC PLATFORMS

### 35. AuditBoard / Optro (Hg, $3B+ acquisition May 2024, rebrand 2026)

**The verb:** Optro *manages enterprise GRC programs end-to-end* — audit, risk, infosec, compliance, control testing, SOX program ops.
**ICP:** ~50% of Fortune 500. $200M ARR.
**State:** Now PE-owned. Acquired Midship (May 2026) to embed agentic AI.
**Does NOT do:** External audit. Tax. Small firms.

### 36. Diligent AuditAI (March 2026)

**The verb:** Diligent *runs internal audits with AI* across its existing GRC base.
**ICP:** Board-tech buyers.

### 37. Bluebook (€2.4M pre-seed, EQT Ventures/YC)

**The verb:** Bluebook *automates monthly closings, reconciliations, and accounting research for Nordic accounting firms*.
**ICP:** Mid-size accounting firms in Sweden/Norway/Finland/Denmark + now UK. 30 leading Nordic firms onboarded.
**Performance:** 80% of recurring work automated, ~30 hours/controller/month saved.
**Does NOT do:** US/India/non-Nordic compliance.
**India-relevance:** Their playbook (own a regulatory geography, become the OS for firms there) is the most directly transferable to India of any vendor in this report.

---

## SEGMENT 5: VERTICAL/INDUSTRY-SPECIFIC ACCOUNTING

### 38. Adaptive ($26.4M total, a16z + Emergence)

**The verb:** Adaptive *runs end-to-end construction-industry accounting* — AP/AR, budgeting, cash flow, expense, vendor mgmt, electronic payments. Highly purpose-built for construction.
**ICP:** Construction GCs + subs + CPAs serving construction.
**Why it works:** Industry-specific accounting (WIP schedules, retention, AIA billing) is too edgy for QBO/Xero. The verb here is the same as QBO, but performed against construction-vocabulary models.
**India-relevance:** Pattern is highly transferable — verticalized accounting for Indian sectors (textiles, jewelry, retail GST regimes).

---

## SEGMENT 6: FP&A & CONSOLIDATION

### 39-42. Mosaic / Pry / Centage / Fathom

**The verb (general):** *forecast and consolidate financials* — Mosaic for SaaS CFOs, Pry for pre-Series B founders, Centage for mid-market budgeting, Fathom for accountant-advised SMBs.
**State:** Pry was acquired by Brex pre-2025; Mosaic is a Series C, sized around $100M+ revenue, pivoting toward AI deal-modeling.
**India-relevance:** Limited. FP&A penetration in India is shallow.

---

## SEGMENT 7: BREX / RAMP PLATFORM PLAYS

### 43. Brex → Capital One ($5.15B, completed early 2026)

**The verb:** Brex *delivers corporate cards + bill pay + expense + travel + accounting integration for startups*. Now embedded into Capital One's small-business stack.
**Implications for accounting:**
- Capital One now has a Brex-shaped wedge into the SMB GL data.
- Brex's earlier "Empower" CFO suite will accelerate inside CapOne's distribution.
- Pilot, Ramp, and bookkeeping startups now face a bank-balance-sheet competitor.
- The "card + accounting" bundle becomes a real moat, not a slogan.

---

## SEGMENT 8: INDIA-NATIVE VENDORS

This is where the underserved verbs live.

### 44. Clear (ClearTax)

**The verb:** Clear *files ITR, GST, TDS, e-invoicing for Indian individuals, SMBs, and CA firms* — with an "AI Co-Pilot" chat-based filer and AI ITC reconciliation (Max ITC).
**ICP:** 1.5M individuals; 20,000 CAs; 10,000 businesses.
**Founders:** Archit Gupta (NOT Sridhar Vembu — that's Zoho). Last major raise: Composite Series ~$75M Composite Capital 2021 at ~$700M+ valuation; quieter since.
**State:** Dominant in DIY filing. But Black/ClearTax-pro motion to CAs hasn't scaled like global firm-tooling.
**Does NOT do:** Genuine end-to-end ITR-3 / ITR-5 / business return AUTOPILOT (it assists; humans still drive). No audit working papers. No CA-firm engagement layer beyond basic practice mgmt.

### 45. Zoho Books AI / Zia

**The verb:** Zoho Books *runs SMB accounting* with Zia AI bolted on — bank rec via AI agent (Feb 2026), anomaly detection, NL queries, pre-filled contact/amount via patterns.
**ICP:** Indian + global SMBs. GST-native.
**Pricing:** From ₹749/month per org in India.
**Significance:** Owns the price-sensitive Indian SMB segment. AI features are competent but conservative.

### 46. Tally Solutions (TallyPrime 7.0, 7.1 imminent)

**The verb:** Tally *records and computes Indian SMB books with GST/TDS compliance*. AI in 7.0 works silently in background (error prevention). 7.1 promised AI-driven automation.
**ICP:** ~2M+ Indian SMBs.
**State:** Migrated to Oracle Cloud 2026. AI catch-up mode, not leadership mode.
**Does NOT do:** True agentic workflow. Conversational interface (still keyboard-driven). CA-firm-side tooling.

### 47. Refrens

**The verb:** Refrens *generates GST-ready invoices and quotations, manages inventory and payments for Indian SMEs*.
**ICP:** Indian SMEs, freelancers.
**AI:** Light. Cloud-based, modular.

### 48. Vyapar

**The verb:** Vyapar *delivers GST-compliant invoicing + inventory + accounting for retail/pharma/grocery SMBs in India*. Strong mobile-first product.
**ICP:** Tier-2/3 Indian retail SMBs.

### 49. Khatabook / OkCredit

**The verb:** Khatabook & OkCredit *track digital ledger entries and receivables (udhaar) for kirana/local-business owners in India* — phone-based. Khatabook ~1.7x OkCredit by user count.
**AI:** Minimal. Not relevant to formal accounting workflow.

### 50. Inkle (YC, Mercury, Picus, Saison)

**The verb:** Inkle *automates US accounting + tax + compliance + cross-border payments for Indian-founder US startups* (Delaware C-corps with India ops).
**ICP:** 500+ US startups including 5% of YC. Indian-founder cross-border specifically.
**Why it matters:** Validates that cross-border-Indian-founder is a real ICP underserved by US-only and India-only tooling.

### 51. RazorpayX

**The verb:** RazorpayX *automates payouts, payroll, banking, and (via 2026 agents) cash flow forecasting + AP posting to ERP* for Indian SMBs. Multi-bank AI routing.
**ICP:** Indian Series A+ startups + mid-market.
**State:** Building IPO narrative around AI agents. 4 production agents shipped 2026 (checkout, chargeback, subscription, cash forecast).

### 52. Suvit

**The verb:** Suvit *automates GST validation/reconciliation, data entry, and TDS filing for Indian CA firms* — pulls Excel/PDF/WhatsApp-uploaded client docs straight into the CA's accounting system. 30+ internal validation checks.
**ICP:** Indian CA practices and tax professionals.
**State:** Active. Practice-level not firm-level. Very Suvit-specific moat: WhatsApp-based client document collection.
**India-relevance:** This is the closest competitor to anything an Indian founder would build for CA firms.

### 53. CORAA

**The verb:** CORAA *runs audit working papers, GST recon, TDS review, ledger analysis, voucher scanning, and CARO 2020 compliance for Indian CA firms*. India-hosted, DPDPA-compliant.
**ICP:** 50+ Indian CA firms (early). Statutory + internal auditors.
**State:** Most direct India audit-AI player. Smaller than the brand-name global plays but well-positioned.
**India-relevance:** Direct competitor for an India CA-firm-audit play.

### 54. AuditCue (Kalaari Capital, Seed 2022 $1.5M)

**The verb:** AuditCue *runs GRC software for Indian businesses* — ISO 9001, HIPAA-style risk and compliance.
**ICP:** Indian mid-market enterprise compliance.
**State:** Quiet. Not breaking out.

### 55. Entigrity → MYCPE ONE (merged Nov 2024)

**The verb:** Entigrity *staffs offshore Indian accountants/tax preparers into US CPA firms* on FTE basis.
**Pricing:** $1,200-1,800/month per FTE.
**ICP:** US CPA firms wanting cheap labor. ~700 firms claimed.
**State:** Merged with MYCPE, now unified service/CPE/M&A platform.
**Implication:** This is the labor model AI is directly displacing. An AI Black-Ore-equivalent at $20/return demolishes the $1,500/month FTE economics if it works.

### 56. Datamatics CPA

**The verb:** Datamatics *processes US tax returns offshore from India + drives some AI/ML-powered tax workflow automation*. Bookkeeping is secondary.
**ICP:** US CPA firms.

### 57. Tax2Win, Quicko, TaxBuddy

**The verb:** *Help individual Indian filers compute and submit ITR* with capital gains, F&O, crypto, NRI support. Tax2Win was acquired by Fisdom (2021). Quicko is trader-focused. TaxBuddy = CA-assisted.
**ICP:** Indian individuals; traders for Quicko.

### 58. Drip Capital

**The verb:** Drip Capital *finances Indian exporters/importers with collateral-free trade finance and AI-driven document verification*. $9B+ cumulative.
**Accounting integration:** Light. AI is in underwriting, not bookkeeping.

---

## DISCOVERY: NEW W26/X26 ENTRANTS (Mar-May 2026)

Confirmed YC W26/X25 batches contained:
- **Balance, FullSeam, Oxus, Arden** (W26, all accounting/audit AI)
- **Combinely, Moby Analytics, Minerva** (X25)
- **Afternoon.co** (W26)
- **Cranston AI** (F25)

The pattern: YC went hard into "AI does service work for CPAs/auditors" in W26. Roughly 6-8 startups across batches, mostly US-focused, very thin on India.

---

## SKEPTICISM AUDIT: WHO IS A FORMS-AND-RULES WRAPPER?

The "AI" companies most likely to be PR rather than autonomous agents:
- **Most India SMB players (Vyapar, Refrens, Khatabook):** AI is largely OCR + categorization. Not agentic.
- **TaxDome, Canopy, Karbon (core), Aiwyn:** These are practice management with AI features, not autonomous work-doers. Aider-inside-Karbon is the closest to genuine close-automation.
- **Tally:** Still primarily rule-based. 7.1 may change this.
- **Most of the YC SMB cluster (Truewind, Cranston, Minerva, Balance):** Sub-scale, very narrow use cases. Some are essentially services with chat UIs.

Genuinely autonomous (in the sense of executing a multi-step verb end-to-end with minimal touch):
- **Basis** (1065 prep)
- **Black Ore** (business return prep)
- **Fieldguide** (audit engagement)
- **Petual / Midship / Andera** (SOX control testing — narrow but real)
- **Numeric** (close automation, in-house only)
- **Mesh** (accruals — narrow but real)
- **Ramp Accounting Agent** (transaction coding — narrow but real, and at huge scale)

---

## KEY FINDINGS FOR THE INDIAN FOUNDER

1. **The "AI for US CPA firms" land has been thoroughly grabbed.** Basis, Fieldguide, Accrual, Aiwyn, Modus, Karbon, TaxDome, Canopy, Black Ore, Filed all stand between any Indian founder and the top-500 US firms. Net new entrants need a 10x advantage. The only credible Indian-founder play here is OFFSHORE-STAFFING-FOR-US-FIRMS replacement at the WORK level (Black Ore strategy applied to ITR/audit/Form-3CD).

2. **The SMB-direct bookkeeping cluster is a graveyard waiting to happen.** Ramp Accounting Agent + Intuit Assist + Xero JAX + Sage Copilot now do 80% of what Truewind/Mesh/Puzzle/Balance/Minerva sell. Pilot is in slow decline. Don't play here.

3. **India-side, the firm-tooling space is genuinely empty.** Suvit and CORAA are the only India-native AI plays serving CA practices, and both are seed-stage. There's no "Karbon for India" or "Black Ore for ITR/Form 3CD" yet. ICAI's prohibition on outside ownership of audit firms PROTECTS this market from the Modus roll-up model — Indian founders have a structural moat that doesn't exist in the US.

4. **The most defensible verbs for an Indian-bootstrapping founder:**
   - GST input tax credit reconciliation + correspondence with vendors (high-frequency, high-friction)
   - Tax audit report (Form 3CD) preparation autopilot
   - Form 3CEB transfer pricing documentation autopilot
   - Statutory audit working papers with CARO 2020 + Indian Accounting Standards (Ind AS) compliance
   - SEZ + 80-IAC + Section-80 deductions advisory engine
   - GCC F&A statutory + management reporting (Big 4 GDS adjacent)
   - WhatsApp-native document collection + CA-firm workflow (Suvit's wedge but more agentic)

5. **The Tier-2/3 (Aprio, Nexdigm, Grant Thornton Bharat, BDO India) is the underserved buyer.** Big 4 builds in-house. Tier-2/3 has the budget but not the engineering team. Suvit/CORAA are not yet purpose-built for tier-2 scale and complexity.

(End of teardown. Whitespace matrix follows in 06b.)
