# Gap 3: Account Aggregator for CA Firms — State of the Wedge (May 2026)

**Author:** Research agent
**Date:** 2026-05-16
**Question:** Is the Account Aggregator (AA) framework a 2026 wedge for CA-firm tooling, or a 2028 wedge?
**TL;DR:** AA is **strategic infrastructure that is now production-grade for the data plane, but the consent UX and the FIU access path are both still hostile to a bootstrapped CA-tooling startup.** AA-as-a-feature is 2026-ready (via Perfios/Setu/Precisa). AA-as-the-wedge is closer to 2027 once consent UX improves, GSTN-FIP stabilises for time-series tax reads, and TSP pricing falls. The right founder play is **AA-enabled CA tooling via a TSP partnership** rather than chasing your own NBFC-AA or direct-FIU registration.

---

## 1. The 17 Operational AAs — Who Actually Serves Whom

As of the Sahamati ecosystem dashboard (31 March 2026), the ecosystem has **17 RBI-licensed Account Aggregators, 179 FIPs, 989 FIUs, and 1,157 total registered entities** (Sahamati Varta newsletter, March 2026). Cumulative consents fulfilled crossed 431 million; monthly run-rate is 22.3 million consents and 276 million data deliveries. Linked accounts hit 284 million cumulatively, growing 38% MoM Feb→Mar 2026.

The 17 AAs are not uniformly live. CASParser's "State of AA 2026" report identifies **13 with active FIP integrations**; four (Upmint, Cygnet AA, PB Financial, Scoreme) have zero meaningful live FIP coverage. The top-tier by FIP count:

| AA | Operator | FIP Coverage | Primary Customer Base |
|---|---|---|---|
| Anumati | Perfios | 80+ FIPs | Banks, NBFCs, large fintechs, embedded TSP play |
| CAMS AA (FinServ) | CAMS | 70+ FIPs | Mutual funds, wealth managers, RIAs |
| OneMoney | FinSec | 65+ FIPs | NBFCs, lenders, the original FIU broad-base |
| Finvu | Cookiejar Technologies | 60+ FIPs | Fintechs, embedded lending, developer-first |
| NADL | NeSL (govt subsidiary) | 60+ FIPs | Bank-adjacent, govt verification, IU stack |
| Setu AA (Agya) | Pine Labs/Setu | 55+ FIPs | API-first fintech, embedded onboarding |
| Protean SurakshAA | Protean (NSDL e-Gov) | 50+ FIPs | Govt rail use cases, Aadhaar-linked |
| Saafe | Dashboard AAS | 40+ FIPs | Mid-tier lenders, NBFC underwriting |
| Digio AA | Digio | 35+ FIPs | eSign-bundled flows, KYC adjacency |
| Tally Edge | Tally Solutions | not live in FIP | Anchored to Tally Prime; pre-launch state |
| CRIF Connect | CRIF | 40+ FIPs | Credit bureau adjacency, lender underwriting |
| Unacores | Unacores | minimal | Boutique |
| KFin | KFintech | live but light | Mutual fund anchor; wealth-side |
| Cygnet AA | Cygnet | not yet live | TSP-led, hybrid play |
| PB Financial | Policybazaar group | not live | Insurance anchor (planned) |
| Upmint | Upmint | not live | Pre-launch |
| Scoreme | Scoreme | not live | Underwriting-tech anchor |

**Critical finding for CA-firm angle:** Of all 17, only **Tally Edge** has explicit CA-tooling DNA (via the Tally accounting parent), and even Tally Edge does not appear in Sahamati's "live FIP integrations" set as of March 2026. **No AA in 2026 has shipped a CA-firm-specific product layer.** The closest adjacencies are CAMS AA (which serves wealth managers and RIAs, the SEBI-side cousins of CAs) and Anumati (which has SME-lending plumbing via its Perfios parent's broader DPI stack).

This is the single most actionable finding: **no AA has yet positioned itself as the "CA channel,"** which means a TSP-mediated entrant can pick its partner freely.

---

## 2. CA-Side Vendor Profiles — Who Actually Ships AA-Enabled CA Tooling

### Precisa (precisa.in)
The most mature commercial CA-adjacent AA tool. Precisa serves both **lenders and CA firms** as named industry verticals. They process 55M+ transactions, 650K+ statements, and integrate with 850+ banks (1,200+ formats). AA integration is offered as one of multiple ingest paths alongside PDF upload and direct bank fetch. Pricing is **publicly transparent**: ₹100/account on pay-per-use, ₹14,000 prepaid for 200 accounts/year, with custom enterprise tiers. They report 2.3-second average AA fetch latency across 50,000+ AA fetches. Customers named: Drip Capital, FtCash, UC Inclusive, DGGI (govt). **Precisa is best understood as a "bank-statement intelligence" layer sold to CAs as a tool, not as workflow software for CA firms.** It plugs into the CA's existing process rather than restructuring it.

### AuditCircle (auditcircle.co)
A Mumbai-incorporated CA-tech startup (CIN U72900MH2021PTC359034, incorporated 2021), founded by **CA Hitesh Bohra (ex-PwC)** with Vimla Bohra as co-director. PitchBook lists them as accelerator-backed but no disclosed funding or revenue traction. **AA integration is real but stated only at the framework level**, not as quantified live volumes. Their core wedge is **balance confirmation automation** for statutory audit: pulling debtor/creditor/bank balances via API, with AA as one data source alongside GST, MCA, ICAI, and Income Tax portals. No named customers publicly. Pricing not disclosed. Realistic read: AuditCircle is the closest competitor to a hypothetical AA-native CA-tooling startup, but their wedge is audit-balance-confirmation, not end-to-end bookkeeping; the SAM is the ~80,000 Indian audit firms doing statutory audits, not the ~600,000+ proprietorship-bookkeeping firms.

### FinBox
Pure lender-tool. The "BankConnect" product wraps AA for lender underwriting; their case studies are all NBFC/lender. No CA crossover; product surface area is wrong for CA firms.

### Bridge Money
Consumer-side neobank / PFM app; not a B2B CA-tooling play. Not relevant to this thesis.

### Inkle (inkle.ai)
US-India cross-border CA-tech. Partners with "dozens of Indian CA/CS firms" for incorporation work. AA usage is **incidental, not central** — they pull bank statements for cross-border bookkeeping but their Indian client AA depth isn't featured. Strategically: Inkle's cross-border angle is orthogonal to the domestic India CA-firm wedge.

### AI Accountant / KoreFi (aiaccountant.com)
Spun out from the **Karbon Card team**. Positions as "India's first AI-powered bookkeeping partner" with explicit AA bank-feed product. 3,000+ businesses supported; 30+ crore transactions processed; "100+ companies switched" claim. Notable: the platform "functions as a registered Financial Information User within India's AA framework" per their content, though they do not publicly state which AA partner or TSP they use. Customer narrative is anonymized (Bangalore CA firm with 50+ SMB clients; Chennai textile business; Mumbai manufacturing SMB). **AI Accountant is the most credible existing example of an AA-native CA-tooling product in India.** They are likely the closest competitor in 2026.

### Vyapar TaxOne (formerly Suvit)
Acquired by Vyapar; ICAI-recognised; CA-targeted. **Notably does NOT use AA** — their bank-feed path is PDF/Excel/image extraction via "intelligent OCR" pushed into Tally. This is a strategic tell: the largest ICAI-recognised CA-tech platform decided AA was not worth the integration cost in 2025-2026.

### Newer entrants
The CASParser product is mostly a bank-statement parser, GSTN-via-AA is referenced but not its core wedge. **Karbon, Khatabook, OkCredit, Refrens** — all have AA-adjacent or no-AA bookkeeping products targeting micro-merchants rather than CA firms.

**Verdict on the competitive layer:** the AA-native CA-tooling category in 2026 has exactly two credible domestic incumbents — Precisa (bank-statement intelligence) and AI Accountant (bookkeeping with AA feeds). Neither has captured the CA-firm workflow shell. AuditCircle is a niche audit-confirmation player. There is whitespace, but it is contested whitespace.

---

## 3. The FIU Registration Path — The Brutal Truth for a SaaS Founder

This is the most important section. Sahamati's own FAQ states explicitly: **"No, you cannot be an FIU or FIP if you are not a regulated entity"** (sahamati.org.in/faq). The four eligible regulators are **RBI, SEBI, IRDAI, PFRDA**. A pure-SaaS CA-tooling startup is none of these.

### The four paths a SaaS founder has:

**Path A — Become an NBFC-AA yourself.**
Not realistic. ₹2 crore minimum Net Owned Fund (NOF). 12-month RBI in-principle-to-CoR cycle. You become the data pipe, not the application layer. This is a wrong product strategy — it puts you in competition with Anumati/OneMoney rather than serving CA firms.

**Path B — Get a SEBI-RIA license** (Investment Adviser).
RIAs are legitimate FIUs. Cost: ~₹1L SEBI fee + NISM Series-X exams. Timeline: 4-6 months. **But:** the use case is constrained to "investment advisory" — you cannot legally use the AA data for general bookkeeping or audit assistance. This is a narrow door.

**Path C — Partner with a TSP that fronts as the regulated entity.**
This is the realistic path. TSPs are explicitly the "only unregulated participants in the AA ecosystem" (Sahamati FAQ). 35+ certified TSPs exist as of March 2026, including **Setu, Perfios, Karza, Cygnet, Signzy, Lentra, Finarkein, Juspay, TransUnion, TCS, Digio, Finacus, FSS**. A TSP can offer your SaaS the AA gateway under a commercial agreement, but you still need a **regulated FIU as the legal data fiduciary** for each consent. Models in market:
- **Setu's gateway model:** ₹10-₹25 per successful fetch; you must have agreements with both Setu and each supported AA. Setu handles certification complexity "on behalf of the FIU" but the FIU must still be a regulated entity.
- **Perfios's TSP model:** wraps Anumati AA (which they own); white-label option to a regulated fronting partner. Pricing on enterprise-quote basis (typical industry rumour: ₹8-₹20 per consent + setup fees).
- **Cygnet's TSP model:** three-module stack (Data Standards / UX / Analytics); enterprise-quote pricing.

**Path D — Partner with a regulated FIU as a sub-processor.**
Find a regulated NBFC/RIA/insurer/payment-bank that uses AA, get listed as their TSP/sub-processor, deliver the CA-tooling product under their FIU legal umbrella. This is how many fintech-adjacent products quietly access AA data today. The regulatory burden moves to the partner; you pay them per-consent and lose pricing freedom.

### Realistic cost & timeline ranges for AA-enablement (TSP path):

- **TSP setup fees:** ₹3-15 lakh (one-time, varies by TSP)
- **TSP per-consent transaction fee:** ₹8-₹25 (volume tiers; CASParser estimates ₹10-₹25 mid-market)
- **Sahamati annual membership (TSP rolls this up or you pay separately):** scale-based, undisclosed publicly but estimated ₹2-10L for SaaS-tier
- **Sahamati-empanelled certification audit:** ~₹3-8L one-time + ₹2-5L biennial
- **SOC 2 Type 2 + ISO 27001 (table stakes for TSP-routed integration):** ₹15-40L first-year, ₹8-15L ongoing
- **Total first-year cost (TSP-routed FIU partnership):** ₹40 lakh - ₹1.2 crore
- **Total first-year cost (direct FIU, where you become regulated):** ₹2-5 crore (because of the NOF and dedicated compliance team)

CASParser's published estimate of "₹5-25 lakh+ for first-year FIU setup" is the optimistic floor and assumes you already hold a regulator license. **Realistic 6-month path:** TSP partnership + fronting FIU + Sahamati cert audit + SOC 2 prep started in parallel. **Realistic 12-month path:** add your own SEBI-RIA license to escape fronting dependency; production-grade SOC 2 Type 2 completion; volume-tier renegotiation with TSP. The 6-month path is achievable for a single technical founder + one part-time compliance hire. The 12-month path requires a second hire.

---

## 4. AA Consent Flows for SMB Clients — The Real UX Problem

The founder's hypothetical: a 60-year-old proprietor on SBI's iMobile app, giving consent to share statements with his CA. **This is the make-or-break UX question.**

### Available consent flow drop-off data (May 2026):

The published numbers are thin but consistent in direction:
- **Precisa benchmark:** only **38% of Indian borrowers have AA-enabled bank accounts**; 62% require PDF fallback. (Precisa "AA for Lenders 2026 Guide")
- **Precisa case study:** AA-only lenders see **56% customer drop-off when informed "your bank isn't supported,"** vs 18% baseline drop-off. One named case showed 38% revenue decline.
- **Fibe (lender) case study via Setu:** **+28% AA consent conversion** by switching to a multi-AA gateway with intelligent routing.
- **Sahamati ecosystem dashboard:** 22.3M consents fulfilled vs 12.1M new account linkages in March 2026 — a ~1.8x consent-to-linkage ratio that implies steady but not explosive depth-of-use, with no published end-to-end success rate.
- **Setu's own framing ("AA Consent Conversion Crisis"):** ecosystem-wide consent completion is acknowledged as too low for digital-first lenders, with no published number.

**Implication for CA firms:** the proprietor consent flow is hostile. The 60-year-old proprietor must (a) have an AA-supported bank, (b) install or have an AA app, (c) understand the consent message in his preferred language, (d) approve at the FIP (SBI) side via the FIP's own redirect (which throws him out of the CA's app entirely), (e) return to complete. Each step has 15-40% drop-off in lender benchmarks; compounded, end-to-end success for first-time AA users is plausibly in the **30-55% range**. This is significantly better than chasing PDFs over WhatsApp for low-friction clients but worse than the founder might intuit.

### The consent revocation gotcha:

Consents are revocable at any time by the client via the AA app. This is a real risk for the CA-tooling business model: a client can pull consent mid-engagement, breaking the data pipe silently. The CA discovers it at the next reconciliation cycle. There is no standardised pattern in 2026 for "consent renewal reminders." Setu's gateway and Perfios's Anumati flow now ship periodic-consent products (multi-month consents with auto-renewal hooks), but renewal still requires active client approval, and CA-side messaging UX has to handle the revocation event gracefully.

### Comparison to the "WhatsApp-send-me-your-PDF" baseline:

The WhatsApp baseline is what AA must displace. It has near-100% reach (every proprietor uses WhatsApp), trivial friction for the client (forward a bank statement PDF), but it costs the CA firm 2-6 hours per client per month in manual ingestion, parsing errors, follow-ups, and incomplete months. The breakeven calculation: if AA gets to ~55% completion and saves ~3 hours per client per month, it's a win for CA firms managing 50+ clients. **The wedge is not "replace WhatsApp 100%," it's "automate the 55% of clients who will consent, fall back to PDF for the rest."** This matches Precisa's "hybrid AA + PDF" prescription.

---

## 5. GSTN as FIP — Live, but Shallower than the GSP Path

**Status:** GSTN was notified as an FIP in November 2022 (RBI Master Direction amendment). As of March 2026, GSTN is **live and connected to 13 of the 17 AAs**, per CASParser's ecosystem audit. This is real production traffic, not a sandbox.

**Data available from GSTN via AA:**
- **GSTR-1** (outward supplies) — monthly or quarterly
- **GSTR-3B** (summary self-declaration) — monthly or quarterly
- Basic GSTIN profile
- **18 months of historical filings** available per consent

**Data NOT available via AA from GSTN:**
- GSTR-2A/2B (auto-populated inward supplies) — the most CA-relevant reconciliation dataset
- GSTR-9 (annual return)
- Invoice-level detail beyond the summarised return
- E-invoice IRP data
- E-way bill data
- ITC ledger details, cash ledger details

### AA-from-GSTN vs GSP-API-from-GSTN — the comparison CA firms care about:

| Dimension | AA path | GSP path |
|---|---|---|
| Consent model | Per-client explicit consent via AA app | OTP-based auth at GSTN; CA can use bulk auth tokens |
| Data depth | GSTR-1, 3B only | Full GSTN dataset including 2A/2B, 9, IRP, e-way |
| History | 18 months capped | 5+ years available |
| Real-time | Returns-as-filed only | Returns + invoices as posted |
| Cost | ₹8-25 per fetch via TSP | GSP licence + per-API call charges (varies by GSP) |
| Reach | ~13 AAs but full GSTN base | Universal — every GST-registered taxpayer |
| CA workflow fit | Poor — too shallow for reconciliation | Strong — built for tax compliance flows |

**Honest take:** For CA-firm GST workflows, **GSP-API is materially superior to AA-from-GSTN in 2026.** AA-GSTN is useful for lender underwriting (where "filed returns" are enough) but inadequate for CA-side ITC reconciliation, GSTR-9 prep, or e-invoice/e-way work. The CA-tooling startup should use **AA for bank statements + GSP for GST data + Income Tax e-filing API for TDS/ITR data + MCA21 for entity master**. Treating AA as the universal data spine is incorrect.

---

## 6. The 3-Year Market View

### Is the AA layer ready for production CA-firm workloads today (May 2026)?

**Bank-statement data: yes, conditionally.** 38% AA-enabled coverage among MSMB owners means the AA-native flow works for roughly half your addressable book; the other half needs PDF/WhatsApp fallback. Top 4 banks (SBI, HDFC, ICICI, Axis) plus the next-tier 6-8 (Kotak, Yes, IDFC First, IndusInd, BoB, PNB, Canara, Union) are all live FIPs. Latency is 2-5 seconds. Success rates after consent grant are >90% per Precisa data. The data pipe works.

**Current accounts for sole proprietors: patchy.** CASParser reports current accounts (sole prop) are live on ~65 of 72 banks; joint accounts are not supported by any bank. For LLP/PLC/Pvt Ltd current accounts, coverage is more uneven and depends on the bank's KYC trail attribution.

**GST data via AA: too shallow for CA work.** Use GSP path.

**Other data sources (ITR, MCA, e-way, e-invoice): not in AA.** Must integrate separately.

### The realistic 2026 wedge using AA — what could a CA-tooling startup ship today?

1. **AA-enabled bank reconciliation product for CA firms managing 50-500 SMB clients.** Sell on time-saved-per-client (~3 hours/month). Hybrid AA + PDF fallback. Per-firm pricing ₹3-8K/month. This is what AI Accountant already sells; the founder must differentiate on either (a) workflow integration depth with Tally/Zoho/QB or (b) CA-firm-specific practice management.
2. **Audit-balance-confirmation workflow** using AA for bank-side balance pulls + GSTN-via-AA for sales/purchase confirmation triangulation. This is AuditCircle's wedge; opportunity to enter via a different geography or audit-firm tier.
3. **Cash-flow advisory product** for CA firms to upsell to their bookkeeping clients, using AA-fed real-time bank data and GST-filed returns to produce monthly cash-flow dashboards. Repositions the CA from "bookkeeper" to "advisor." This is Sahamati's published "RIA / PFM-adjacent" use case translated to the CA channel.

### The 2028 wedge — what becomes possible when AA matures

By 2027-2028, expect:
- GSTN-FIP to expand to include 2A/2B and possibly invoice-level detail (currently a Sahamati lobby item)
- Income Tax Department to become an FIP for ITR/26AS data (RBI/CBDT discussions are public but not yet in master direction)
- MCA21 corporate-master data via AA (under discussion in DPI roadmap)
- Insurance and pension FIPs to broaden, opening CA workflows for individual tax planning
- Consent UX standardisation (Sahamati's "consent template" project) potentially raising completion rates to 70%+
- TSP per-consent pricing falling to ₹3-8 as volumes scale

When those four expansions happen, AA becomes the single coherent data spine for an Indian CA-firm operating system. **That is the 2028 wedge** — and a 2026 entrant who has shipped an AA-enabled bank-reconciliation product and built customer trust is well positioned to ride the data-depth wave.

### The dependency chain

For a bootstrapped CA-tooling founder, the realistic timeline:
1. **Months 0-2:** Pick TSP partner (Setu or Perfios). Pick fronting FIU partner (a small NBFC or RIA who'll let you ride their licence in exchange for per-consent revenue share). Begin SOC 2 readiness.
2. **Months 2-5:** Build product against TSP sandbox; pilot with 2-3 friendly CA firms using their own client AAs. Hybrid PDF fallback baked in from day 1.
3. **Months 5-8:** Sahamati certification audit. Production go-live on TSP-fronted FIU. SOC 2 Type 1 closed. First 10 paying CA firms.
4. **Months 8-12:** Scale to 50-100 CA firms. Apply for own SEBI-RIA registration to escape fronting dependency. SOC 2 Type 2.
5. **Year 2:** Build out GSP-API, MCA21, IT-department data integrations. Layer CA-firm practice-management features.
6. **Year 3:** Position for the 2028 expansion of AA data depth.

---

## Sources

- Sahamati certified entities, faq, ecosystem dashboard, March 2026 Varta newsletter, RIA advisory article (sahamati.org.in)
- CASParser, "State of Account Aggregator in 2026" (casparser.in/blog/state-of-account-aggregator-2026/)
- Precisa, "AA for Lenders Complete 2026 Guide" (precisa.in/blog/account-aggregator-lenders-guide-2026/)
- Setu, "AA Consent Conversion Crisis" blog and developer docs (blog.setu.co, docs.setu.co)
- Perfios, "TSP with an Advantage" (perfios.ai)
- Anumati, How-it-Works (anumati.co.in)
- AuditCircle company page; ZaubaCorp filing (auditcircle.co)
- AI Accountant, About + AA Bank Feeds blog (aiaccountant.com)
- Vyapar TaxOne, Tally automation post (taxone.vyapar.com)
- Business Standard, "AA ecosystem consent processing up 78% in FY25"
- TaxGuru, "AA Framework Application-to-Compliance Guide for Fintech Founders"
- Cygnet AA-TSP product page (cygnet.one)
- Sahamati TSP registry (sahamati.org.in/tsp)
- RBI Master Direction NBFC-AA, ReBIT GSTN data schema (sahamati.org.in/rebit-publishes-gstn-data-schema)
- A2Z Taxcorp on GSTN-as-FIP (a2ztaxcorp.com)
- HyperVerge AA selection guide (hyperverge.co/blog/best-account-aggregators)
