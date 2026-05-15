# Indian CA Firm Compliance Workflows — Process Maps for an AI Founder

**Date:** 2026-05-16
**Audience:** Tech founder with no accounting background, building an AI product for Indian CA firms.
**Scope:** Detailed step-by-step process maps for the 12 most fee-bearing compliance workflows. Each is broken into who, when, inputs, steps with time estimates, outputs, common errors, AI feasibility per step, and 3-5 candidate AI wedges. Read this as the "process anatomy" companion to `01-operations-workflows.md` (hierarchy & lexicon), `02-software-stack.md` (tooling), `04-pain-points.md` (CA verbatim), and `05-economics-billing.md` (fees & WTP).

**Convention used throughout:** "Article" = articled assistant (CA student in training); "Manager" = qualified CA, 3-7 yrs; "Partner" = signing CA. Times are *per client per cycle* for a small/mid-tier firm (5-50 people), unless stated. AI Automation Potential is rated **Full** (LLM/RPA can do end-to-end with sign-off check), **Partial** (cuts 50%+ of human time but needs human in loop), or **Not feasible** (requires professional judgement, legal sign-off, or relationship work).

---

## 0. The Big Picture Before You Read 12 Workflows

The Indian compliance year repeats roughly the same 12 things on roughly the same dates. **The cycle is non-negotiable** — the deadlines are statutory, the formats are GSTN/IT/MCA-imposed, and the work has to flow through human CA sign-off because DSC tokens and ICAI professional ethics require it. For each workflow there are usually 3 phases:

1. **Data collection from client** (always the longest pole).
2. **Preparation + reconciliation** (where articles live).
3. **Review + sign-off + filing** (where partners bottleneck).

Existing software (Tally, ClearTax, Winman, Computax, KDK Spectrum) handles **format conversion and portal submission** well. Almost no tool handles **phase 1** (collection) and almost no tool deeply automates **phase 2** (reconciliation) — they only display the mismatches and leave the matching to a human eyeball. This is exactly the AI insertion zone.

---

## 1. GST Monthly Returns — GSTR-1 + GSTR-3B + IMS

### WHO
- **First-cut preparation:** Article (40% of an article's monthly hours go here in a small firm).
- **Reconciliation between books and 2B:** Article + Senior.
- **Review of computation:** Manager / paid CA.
- **Final sign-off & portal submission:** Partner (DSC or EVC).
- **Outsourced bookkeeping clients:** The CA's own paid accountant also does data entry in Tally first.

### WHEN
- **GSTR-1**: 11th of following month (monthly filers; turnover > ₹5 cr).
- **IMS actioning window**: 12th-13th of following month (window opens 14th of *current* month, finalises by 14th of next).
- **GSTR-2B auto-generation**: 14th of following month.
- **GSTR-3B**: 20th of following month (22nd/24th staggered for QRMP / smaller filers).
- **Frequency:** 12 times per year per GSTIN. Multi-state clients can have 5-15 GSTINs each.

### INPUTS
- Sales register (Tally / BUSY / SAP / Excel export).
- Purchase register (vendor invoices, often as PDFs / WhatsApp images).
- E-invoice JSONs (auto-flowing for ≥ ₹5 cr turnover clients).
- E-way bill data.
- Previous month's GSTR-3B (for carry-forwards).
- GSTR-2B (auto-populated by GSTN on 14th).
- IMS dashboard (per supplier invoice).
- Cash + credit ledger from GST portal.
- Reverse-charge (RCM) inward supplies list.
- Import IGST data (ICEGATE).
- HSN summary, B2C summary, exports/SEZ supplies, credit notes, debit notes, amendments.

### STEPS

| # | Step | Who | Time (min) | Tool used today |
|---|---|---|---|---|
| 1 | Pull sales register from client Tally / receive via WhatsApp / email | Article | 10-30 | AnyDesk, email, WhatsApp |
| 2 | Validate sales register completeness (sequence breaks, missing invoices, debit/credit notes) | Article | 15-45 | Excel pivot |
| 3 | Reconcile sales register to e-invoice IRN data (for ≥ ₹5 cr clients) | Article | 20-60 | ClearTax / Tally GST module |
| 4 | Prepare GSTR-1 JSON (B2B / B2C-L / B2C-S / Exports / Credit notes / HSN) | Article | 30-90 | Tally export → GST Offline Tool / ClearTax |
| 5 | Upload GSTR-1 to portal, fix validation errors | Article | 15-60 | gst.gov.in |
| 6 | Submit GSTR-1; capture filing acknowledgement | Article | 5 | Portal |
| 7 | **IMS actioning** — review every inward invoice flagged in IMS dashboard against purchase register; mark Accept / Reject / Pending. (Inaction = deemed acceptance after 14th.) | Article + Senior | **60-240** | GST portal IMS tab; ClearTax IMS |
| 8 | Download GSTR-2B on 14th; export to Excel | Article | 10 | Portal |
| 9 | **Reconcile GSTR-2B vs purchase register line-by-line** — match GSTIN + invoice number + date + value + tax. Identify (a) in 2B not in books, (b) in books not in 2B, (c) amount mismatches, (d) ineligible ITC (blocked credits u/s 17(5)) | Article | **120-480** | Excel VLOOKUP; ClearTax Reconcile; Suvit |
| 10 | Email/WhatsApp suppliers for missing invoices ("Please file your GSTR-1 — credit blocked"). Track responses | Article | 30-120 | WhatsApp, email |
| 11 | Classify ineligible ITC: section 17(5) blocked items (motor vehicles, club, personal use, food), exempt-supply proportionate reversal under Rule 42/43 | Senior | 30-90 | Manual classification |
| 12 | Compute net ITC = (eligible 2B ITC + RCM ITC + import IGST) - reversals | Senior | 15-30 | Excel |
| 13 | Compute output tax liability: B2B + B2C + exports (zero-rated) + RCM payable | Senior | 15-30 | Excel |
| 14 | Compute interest on late payment u/s 50, if applicable | Senior | 10-30 | Excel |
| 15 | Set off output liability against credit ledger / cash ledger; determine cash needed | Senior | 10-20 | GST portal calculator |
| 16 | Pay challan via NEFT/RTGS; capture CIN | Article | 10-30 | Bank net banking |
| 17 | Draft GSTR-3B; auto-populated values from 2B + GSTR-1 (Table 3 hard-locked since July 2025) | Article | 20-45 | Portal / ClearTax |
| 18 | **Manager review** of working: 2B-vs-books reco, ineligible ITC classification, RCM, interest calc | Manager | 30-60 | Working paper review |
| 19 | **Partner review + DSC/EVC sign and submit** | Partner | 10-20 | DSC token + Java emSigner |
| 20 | Send filing acknowledgement screenshot to client via WhatsApp; archive working paper | Article | 5-10 | WhatsApp |

**Total time per client per month (small firm, mid-complexity SME):** 7-18 hours. **Multiply by 30-80 clients** per firm. The DEV.to Mumbai case study quoted 6-8 hrs/client/month for 80+ clients = ~3 FTE-equivalents.

### OUTPUTS
- Filed GSTR-1 acknowledgement (ARN).
- Filed GSTR-3B acknowledgement (ARN).
- Tax paid challan receipts.
- IMS action log.
- 2B-vs-books reco file (audit trail for future scrutiny).
- WhatsApp ack to client.

### COMMON ERRORS / PAIN POINTS
- **Invoice number format mismatch** between supplier-filed GSTR-1 and recipient's purchase register (e.g., "INV/0123/24-25" vs "INV-0123"). Cited by CA Sahil Nagpal on CAclubindia as the recurring break in his Excel utility.
- **Supplier files late** (after 11th of month). ITC effectively frozen until next 2B. Affluence Advisory case: "Suppose ₹50 L expected ITC, 20% vendors delay = ₹10 L frozen for a month."
- **Period boundary:** Invoice dated 31 March uploaded by vendor in April. Shows in April 2B; books recorded in March. Manual override needed.
- **IMS "inaction = acceptance" trap** (new Feb 2026): If article forgets to reject an invalid invoice in the IMS window, it auto-accepts and pollutes 2B.
- **Hard-locked Table 3 (since July 2025):** Any GSTR-1 error must be amended via GSTR-1A before 3B is filed; otherwise stuck till next month's amendment cycle.
- **Hard-locked Table 4 (ITC, scheduled July 2026):** If 3B ITC > 2B ITC, portal will refuse filing. CA Kavish Chawla: *"You have to catch these mismatches before they enter GSTR-3B. Not after. Before."*
- **B2C / HSN code mismatches** cause portal validation errors.
- **GSTN portal downtime** on the 18th-20th of every month (e.g. KSCAA letter Jan 2025; Halakhandi tweet April 2026).
- **17(5) ineligible ITC classification** is judgement-heavy — articles routinely mis-classify, manager re-classifies, refile/reverse later.

### AI AUTOMATION POTENTIAL (per step)
- Steps 1, 2, 3, 4, 5, 6: **Partial → Full** (Tally export, JSON gen, portal upload — automation already partly done by ClearTax / Tally).
- Step 7 (IMS actioning): **Partial → Full** if AI can match supplier invoices against PR automatically. Big leverage point.
- Step 8: Full.
- **Step 9 (2B-vs-books reco): Partial today, Full feasible.** This is *the* canonical AI wedge — fuzzy matching of GSTIN+invoice#+date+amount across format variants, supplier-name disambiguation, period-boundary handling.
- Step 10 (supplier chase): **Partial.** AI agent can draft WhatsApp/email to suppliers and track replies; final follow-up may still need human voice call.
- Step 11 (17(5) classification): **Partial.** LLM can suggest classification with confidence score; partner reviews edge cases. Improves over time with client-specific patterns.
- Steps 12-15: Full (deterministic arithmetic).
- Step 16: Partial (banking still requires authorisation).
- Step 17: Full.
- Step 18 (Manager review): **Not feasible end-to-end** — needs professional judgement. But AI can *pre-review* and surface red flags, cutting manager time 60-80%.
- Step 19 (Partner DSC): **Not feasible** for full automation due to DSC physicality. AI can prep one-click sign queue.
- Step 20: Full.

### CANDIDATE AI WEDGES
1. **Fuzzy invoice matcher for GSTR-2B reconciliation** — multi-attribute match (GSTIN exact + invoice# fuzzy + date ± 2 days + value tolerance + supplier-name embedding similarity). Output: line-by-line match status + dollar exposure of unmatched.
2. **Auto-classify ineligible ITC** under §17(5) — LLM reads purchase register line item ("Toyota Innova insurance renewal", "company offsite hotel bill") and flags blocked credits with reasoning trace.
3. **IMS auto-action agent** — runs nightly: marks Accept on perfect matches, Pending on ambiguous, drafts Reject for orphan supplier invoices with reasoning attached for human approval.
4. **Supplier chase agent** — drafts WhatsApp/email to all suppliers with missing-in-2B invoices on the 12th of every month, with tax-impact figure baked in to incentivise vendor to file.
5. **Pre-3B sanity check** — runs all of CA Kavish Chawla's "5 sense checks" (effective ITC %, duplicates, zero-rated, large transactions, supplier compliance) and produces a pre-review report that pre-empts the manager's review.

### TYPICAL FEE & WHERE MANAGER TIME GOES
- **Fee (per GSTIN/month):** Solo/small firm ₹500-₹2,500; mid-tier ₹3,000-₹8,000; Big 4 ₹10,000-₹25,000. (Ref `05-economics-billing.md` §1.1.)
- **Avg hours per client:** 7-18 hrs/month all-in.
- **Manager time:** ~30-60 min/client/month, almost entirely on (a) checking ineligible-ITC classification, (b) RCM correctness, (c) interest computation correctness, (d) sense-check on output liability vs prior months.

---

## 2. GST Annual Return — GSTR-9 + GSTR-9C

### WHO
- **Data aggregation across 12 monthly returns:** Article + Senior.
- **Reconciliation to audited financials:** Senior / Manager.
- **GSTR-9C certification:** Partner (mandatory CA cert if turnover > ₹5 cr).

### WHEN
- **GSTR-9** (mandatory if turnover > ₹2 cr): 31 December of following FY.
- **GSTR-9C** (mandatory if turnover > ₹5 cr): 31 December of following FY.
- **Frequency:** Once per year per registration.

### INPUTS
- All 12 GSTR-1 filings of the FY.
- All 12 GSTR-3B filings.
- All 12 GSTR-2B downloads.
- Audited financial statements (must be finalised first — statutory audit must complete before 9C).
- Trial balance.
- Output tax ledger; input tax ledger; cash + credit ledger snapshots.
- E-way bill data summary.
- Fixed asset register (for capital-goods ITC).
- Reconciliation of turnover (books vs GSTR-1).
- Annexure to financial statements — related-party transactions, GST receivable, GST payable.

### STEPS

| # | Step | Who | Time (hrs) |
|---|---|---|---|
| 1 | Aggregate 12 months of GSTR-1 data (outward supplies) | Article | 2-4 |
| 2 | Aggregate 12 months of GSTR-3B data | Article | 1-2 |
| 3 | Reconcile aggregated GSTR-1 vs GSTR-3B (turnover, tax) | Senior | 4-8 |
| 4 | Reconcile aggregated turnover to *audited* P&L | Senior | 6-16 |
| 5 | Identify and document reconciling items (e.g., advance receipts, schedule III non-supplies, exempt supplies wrongly classified) | Senior | 4-12 |
| 6 | Aggregate ITC claimed vs ITC available per 2B | Senior | 4-8 |
| 7 | Reconcile ITC to books (e.g., to "GST Input Receivable" GL) | Senior | 4-12 |
| 8 | Classify ITC: inputs / input services / capital goods (Table 6) | Senior | 2-6 |
| 9 | Identify ITC reversals (Rule 37, 42, 43; ineligible 17(5)) and reclassify in Table 7 | Senior | 4-12 |
| 10 | HSN summary aggregation across 12 months | Article | 2-6 |
| 11 | Late fee / interest reconciliation | Senior | 1-3 |
| 12 | Draft GSTR-9 JSON; upload to portal | Article | 2-4 |
| 13 | For GSTR-9C: reconciliation statement Part A (turnover) + Part B (ITC) | Manager | 8-24 |
| 14 | Identify "auditor's recommendations" — additional tax payable, ITC to reverse | Manager | 2-8 |
| 15 | Partner review of 9 + 9C; certification | Partner | 2-6 |
| 16 | DSC sign + file 9 and 9C | Partner | 0.5 |
| 17 | Pay any additional liability via DRC-03 | Article | 1-2 |

**Total time per client:** 40-150 hours depending on complexity, multiple GSTINs, and condition of books.

### OUTPUTS
- Filed GSTR-9 (ARN).
- Filed GSTR-9C (ARN) with CA's UDIN-stamped certification.
- DRC-03 if differential tax paid.
- Reconciliation working paper (held for 6 years).

### COMMON ERRORS / PAIN POINTS
- **Reconciliation of audited turnover to GSTR-1** is the hardest reconciliation in the Indian compliance year. Causes of difference: schedule III non-supplies (sale of land, services by employee to employer), advances received, free samples, asset transfers, branch transfers, exempt supplies misclassified, financial-credit notes (no GST impact) vs tax credit notes.
- **ITC reconciliation across 12 months** requires re-doing every month's 2B-vs-books reco at year-end, often discovering errors that were previously "let go".
- **Late ITC** — invoices booked in March that supplier uploaded in April-Sept (within Sept 30 cutoff of next FY). These show in next FY's 2B but pertain to current FY. Section 16(4) cutoff matters.
- **Differences between books-stated turnover and Form 26AS / TDS data** raise notice risk.
- **Auditor's books finalised late.** GSTR-9C cannot be done until audited financials are signed — and many SMEs finalise books in October/November, leaving 4-8 weeks for reco.

### AI AUTOMATION POTENTIAL
- Steps 1-2: Full.
- Step 3: Partial → Full (deterministic reco, just multi-source).
- **Step 4 (turnover books vs GSTR-1): Partial.** AI can list candidate reconciling items per GL line; CA decides classification.
- Steps 5, 6, 7, 8, 9: Partial.
- Step 10: Full.
- Steps 13-14: Partial (LLM drafts narrative; CA verifies).
- Steps 15-16: Not feasible (sign-off).

### CANDIDATE AI WEDGES
1. **Books-to-GSTR-1 turnover reconciler** — ingests TB + 12-month GSTR-1 aggregate; auto-categorises reconciling items (schedule III, advances, returns, branch transfers) with confidence and audit trail.
2. **12-month ITC delta detector** — flags ITC claimed in 3B that has no supporting line in 2B at year-end (ITC at risk under §16(2)(c)).
3. **Late-ITC eligibility checker** — automatically applies the Sept 30 / next-FY-cutoff rule per §16(4) and identifies any time-barred ITC.
4. **9C narrative drafter** — for each material reconciling item, drafts the standard "auditor's comment" with regulatory reference, for partner edit.
5. **DRC-03 auto-generator** — computes residual liability and pre-fills DRC-03 challan.

### TYPICAL FEE & WHERE MANAGER TIME GOES
- **Fee:** Solo/small firm ₹5,000-₹25,000; mid-tier ₹50,000-₹2 L; Big 4 ₹2 L-₹15 L.
- **Avg hours per client:** 40-150 hrs across team.
- **Manager time:** 30-50% of total; almost entirely on reconciling items (steps 4, 5, 13).

---

## 3. E-Invoicing under GST

### WHO
- **Setup (one-time):** Manager / Senior — register on IRP, choose API/SFTP/portal, integrate with client's ERP.
- **Daily generation:** Client's accounts team (CA-firm involvement is exception-based).
- **Monthly review of IRN-vs-GSTR-1 reconciliation:** Article.

### WHEN
- **Applicability:** Aggregate turnover > ₹5 cr in any FY since 2017-18.
- **Reporting window:** 30 days from invoice date (for ≥ ₹10 cr turnover, from April 2025). Failure → IRP rejection, invoice considered invalid for GST.
- **Frequency:** Continuous; every invoice as it's raised.

### INPUTS
- Invoice JSON in e-invoice schema (INV-01 format).
- Supplier + recipient GSTIN.
- HSN/SAC codes per line item.
- Item-wise tax breakup.

### STEPS

| # | Step | Who | Time |
|---|---|---|---|
| 1 | One-time: enrol client on IRP (e-invoice portal); whitelist GSP/ASP | Manager | 1-2 hrs |
| 2 | Configure client's ERP (Tally GenWel, SAP, Zoho, custom) to push JSON to IRP | Manager + IT vendor | 4-40 hrs (one-time) |
| 3 | Per invoice: client posts invoice in ERP; ERP/middleware sends JSON to IRP | Client/ERP | <1 sec |
| 4 | IRP validates, returns IRN + signed JSON + QR code | IRP | <1 sec |
| 5 | ERP/client prints invoice with IRN + QR | Client | — |
| 6 | Monthly: reconcile IRNs generated vs invoices raised in books vs GSTR-1 | Article | 1-3 hrs/month |
| 7 | Identify invoices missed from e-invoice generation (now invalid for GST credit at buyer end) | Article + Senior | 1-2 hrs |
| 8 | Identify invoices generated but cancelled in books (need IRN cancellation within 24 hrs window — frequently missed) | Article | 1-2 hrs |
| 9 | Where 30-day window missed: advisory on re-invoicing or accepting buyer's loss of credit | Manager + Partner | 30-60 min/incident |

### OUTPUTS
- Active e-invoicing setup (integration validated).
- Monthly reco: IRN-vs-books-vs-GSTR-1 matched.
- Exception list for management.

### COMMON ERRORS / PAIN POINTS
- **30-day window breach.** Especially for back-dated invoices, sales-returns reversals booked late, debit notes.
- **IRN cancellation 24-hour rule.** Many clients cancel invoices in ERP days later but the IRN is still active on IRP — leaves a phantom invoice in GSTR-1.
- **Schema validation errors** — pin code mismatches, GSTIN-state code mismatch, HSN-rate mismatch.
- **Multi-ERP environments** (some divisions on SAP, some on Tally) — each needs its own connector.
- **Tally Prime round-off issues** — caclubindia threads document "round-off-and-rejection-in-tally-prime" recurring problem.
- **Buyer disputes:** Buyer claims ITC not flowing because e-invoice was wrong.

### AI AUTOMATION POTENTIAL
- Steps 1, 2: Not feasible end-to-end (integration project work).
- Step 6: Full.
- Step 7: Full.
- Step 8: Partial.
- Step 9: Not feasible (judgement / client advisory).

### CANDIDATE AI WEDGES
1. **IRN-vs-books drift monitor** — daily background job that flags invoices in books without an active IRN, or IRNs without a book entry.
2. **30-day expiry alert agent** — surfaces invoices approaching the 30-day cutoff (for ≥ ₹10 cr clients), so client raises before window closes.
3. **IRN-cancellation reconciler** — flags book-cancelled invoices that still have active IRN (24-hour rule violations).
4. **Schema pre-validator** — runs the IRP's validation rules locally on invoice JSON before submission to catch errors without round-tripping IRP.

### TYPICAL FEE & WHERE MANAGER TIME GOES
- **Fee:** Setup ₹15,000-₹75,000 (one-time); monthly review embedded in GST retainer.
- **Avg hours:** ~3 hrs/month after setup; 4-40 hrs one-time for ERP integration.
- **Manager time:** Almost entirely on initial integration + advisory on exceptions.

---

## 4. TDS — Monthly Deposit + Quarterly Return + Form 16/16A + 26AS/AIS Recon

### WHO
- **Monthly TDS computation + deposit:** Article + Senior.
- **Quarterly return prep (24Q/26Q/27Q/27EQ):** Article.
- **Form 16 / 16A generation:** Article (TRACES download); Senior verifies.
- **26AS/AIS recon for ITR filing:** Article + Senior.

### WHEN
- **TDS deposit:** 7th of following month (every month).
- **TDS quarterly returns:**
  - Q1 (Apr-Jun): 31 July.
  - Q2 (Jul-Sep): 31 October.
  - Q3 (Oct-Dec): 31 January.
  - Q4 (Jan-Mar): 31 May.
- **Form 16 (salary, annual):** 15 June of following FY.
- **Form 16A (non-salary, quarterly):** Within 15 days of TDS return filing.
- **Frequency:** Monthly deposit × 12 + Quarterly return × 4 + Form 16 × 1 + Form 16A × 4.

### INPUTS
- Vendor/employee invoice/payment register with TDS section coded.
- PAN of every deductee.
- TDS rate per section (194C contractor, 194J professional, 192 salary, 194I rent, 194Q purchase, 195 NR, 194H commission, etc.).
- LDC (Lower Deduction Certificate) per deductee if applicable.
- Challan history.
- TRACES login.
- E-filing login + DSC.
- Form 26AS / AIS of the deductor and deductees.

### STEPS

| # | Step | Who | Time |
|---|---|---|---|
| 1 | Receive monthly payment register from client (vendors paid, employees paid, rent, professional fees) | Article | 30 min |
| 2 | Classify each payment under correct TDS section (194C/J/H/I/Q etc.) | Article | 1-4 hrs |
| 3 | Look up PAN status for each deductee on TRACES — "PAN inoperative" → 20% TDS instead of 10% | Article | 1-2 hrs |
| 4 | Apply LDC where vendor has produced one | Senior | 30-60 min |
| 5 | Compute TDS payable, build challan calculation sheet | Senior | 30-60 min |
| 6 | Generate challan (ITNS 281); pay via net banking on or before 7th | Client/Article | 30 min |
| 7 | Capture CIN, challan number | Article | 10 min |
| 8 | At quarter end: aggregate 3 months' TDS data | Article | 1-2 hrs |
| 9 | Generate FVU file using NSDL RPU utility (deductor details + challan details + deductee details with PAN & amount per section) | Article | 2-6 hrs |
| 10 | Validate FVU; fix errors (PAN format, section mismatch, challan-deductee link) | Article | 1-3 hrs |
| 11 | Upload FVU to e-filing portal with DSC | Senior | 30 min |
| 12 | Wait 2-7 days; check TRACES for return status (Accepted / Processed with Defaults) | Article | — |
| 13 | If "Processed with Defaults": review default list (short payment / short deduction / late fee / interest u/s 201) on TRACES | Senior | 1-3 hrs |
| 14 | File correction statement; reconcile PANs and challans | Article | 2-6 hrs |
| 15 | Download Form 16A from TRACES (within 15 days of return filing) for every deductee | Article | 1-3 hrs (bulk download) |
| 16 | Distribute Form 16A to vendors via email/WhatsApp | Article | 30-60 min |
| 17 | Annually (June): download Form 16 Part A from TRACES; prepare Part B (salary breakup); digitally sign; distribute to employees | Article + Senior | 4-12 hrs |
| 18 | 26AS / AIS recon during ITR season: download 26AS + AIS of the *client* (assessee), match to books TDS receivable | Article | 2-6 hrs |
| 19 | Identify mismatches: TDS in 26AS not in books (income to add) / TDS in books not in 26AS (chase deductor) | Senior | 2-8 hrs |
| 20 | Provide AIS feedback if AIS contains wrong info | Senior | 30 min/instance |

### OUTPUTS
- Monthly challans paid.
- Quarterly return filed (Acknowledgement RRR / Token Number).
- Form 16 issued to all employees by 15 June.
- Form 16A issued to vendors quarterly.
- 26AS / AIS reconciliation working for ITR.

### COMMON ERRORS / PAIN POINTS
- **PAN inoperative** issue — Aadhaar-PAN linking failures cause 20% TDS instead of 1-10%. Vendor relationships strained.
- **Section misclassification** — 194J professional vs 194C contractor is judgement-heavy. Wrong section = "short deduction" default later.
- **TRACES "Processed with Default" rework** — almost every CA has 5-15 default notices a quarter. Default-resolution itself is a sub-workflow.
- **Late filing fee u/s 234E** — ₹200/day; can balloon.
- **Form 26AS mismatch with books** — when deductor (client's customer) files TDS return wrongly, the CA's client doesn't see the TDS credit. Forces chase. CIC noted this is "from pillar to post".
- **Form 16/16A bulk-download throttling on TRACES** — has to be done overnight in May.
- **Higher TDS u/s 206AB** for non-filers of ITR — requires checking compliance status of every vendor.
- **24Q Annexure II (salary breakdown)** is heavy in Q4 — every employee's salary breakup as per ITR-1/2 logic.

### AI AUTOMATION POTENTIAL
- Step 1: Partial (receive doc) → Full (if connected to ERP).
- **Step 2 (TDS section classification): Partial.** LLM with payee-name + invoice-description can suggest section; CA verifies edge cases.
- Step 3: Full (TRACES API for PAN status batch lookup).
- Step 5: Full.
- Step 9-10 (FVU prep + validation): Full.
- Step 13-14 (default resolution): Partial. AI can read TRACES default text and propose correction.
- Step 15-16: Full (bulk download + dispatch).
- Step 17 (Form 16 Part B prep): Full from payroll data.
- **Step 18-19 (26AS/AIS recon): Partial → Full.** Fuzzy-matching same as GSTR-2B.
- Step 20: Partial.

### CANDIDATE AI WEDGES
1. **Auto-classify TDS section** per payment voucher — LLM trained on payee descriptor + amount + recurrence; flags 194Q vs 194C vs 194J with confidence.
2. **PAN-Aadhaar compliance pre-checker** — daily batch check of all client vendors' PAN status; alert when any goes inoperative (so TDS rate updates before payment).
3. **TRACES default auto-resolver** — reads "Processed with Defaults" file, matches each default to source data, proposes correction statement.
4. **26AS-vs-books reconciler** — same engine as GSTR-2B reco, applied to 26AS/AIS TDS data. Reuses fuzzy match infrastructure.
5. **Form 16 Part B auto-prep at scale** — from payroll register, generates 100+ Form 16s with employee-specific salary breakup, ready for partner DSC sign.

### TYPICAL FEE & WHERE MANAGER TIME GOES
- **Fee:** Quarterly retainer ₹2,000-₹8,000/quarter; mid-tier ₹15,000+. (Ref `05-economics-billing.md` §1.4.)
- **Avg hours per client:** Monthly: 2-6 hrs; Quarterly return: 6-15 hrs; 26AS recon: 2-8 hrs.
- **Manager time:** Mostly on default resolution, section judgement calls, 24Q Annexure II review.

---

## 5. Income Tax Return Filing (ITR-1/2/3/4/5/6/7)

### WHO
- **ITR-1/2 (individuals salaried / cap gains):** Article preps, Senior reviews, Partner signs.
- **ITR-3/4 (individual business/presumptive):** Senior preps, Partner signs.
- **ITR-6 (companies):** Senior + Manager + Partner.
- **ITR-7 (trusts/political parties):** Manager + Partner (specialist).

### WHEN
- **31 July** — non-audit individuals (ITR-1, ITR-2 simple, ITR-4 presumptive).
- **31 October** — tax-audit-cases (ITR-3 with audit, ITR-5 LLP audited, ITR-6 companies).
- **30 November** — transfer-pricing cases (international transactions → Form 3CEB required).
- **31 December** — belated / revised ITRs (with late fee).
- **Frequency:** Once per assessee per year.

### INPUTS
- Form 16 / Form 16A from all deductors.
- Form 26AS, AIS, TIS from IT portal.
- Bank statements (interest income).
- Capital-gains statements from brokers (AIS now auto-populates these).
- P&L + BS (for ITR-3/4/5/6).
- Audited financial statements + tax audit report (ITR-3 with audit, ITR-5, ITR-6).
- Tax audit Form 3CA/3CB + 3CD (uploaded separately, linked).
- Schedules: FA (foreign assets), AL (assets-liabilities for income > ₹50L), partners/shareholders, GST turnover, depreciation per Income-tax Act.
- TDS challans, advance tax challans.
- Bank account details.
- DSC.

### STEPS (for an ITR-6 corporate — illustrative)

| # | Step | Who | Time |
|---|---|---|---|
| 1 | Receive audited financials, tax audit report, ledger details from client/auditor | Senior | 30 min |
| 2 | Pull 26AS + AIS + TIS from IT portal (using ERI access via Winman/Computax) | Article | 30 min |
| 3 | Build computation: profit from books → adjustments → MAT comparison | Senior | 4-12 hrs |
| 4 | Compute book profit u/s 115JB for MAT | Senior | 2-6 hrs |
| 5 | Apply Sec 115BAA / 115BAB (concessional regime) if elected | Senior | 1-3 hrs |
| 6 | Compute disallowances: 40A(3), 40(a)(ia) TDS non-deducted, 43B (statutory dues), 14A (exempt income expenses) | Senior | 2-8 hrs |
| 7 | Adjust depreciation Income-tax Act vs Companies Act | Senior | 1-3 hrs |
| 8 | Add deemed income items (115BBE unexplained, 56(2)(viib) share premium etc.) | Manager | 1-4 hrs |
| 9 | Compute carry-forward losses, set off in priority order (b/f losses → current → MAT credit) | Manager | 1-4 hrs |
| 10 | Build ITR-6 JSON: Schedule BP (business), Schedule CFL (losses), Schedule MAT, Schedule TDS, Schedule TCS, Schedule IT (advance tax), Schedule FA (foreign), Schedule SH (shareholders) | Senior | 4-12 hrs |
| 11 | Reconcile TDS in return vs 26AS | Article | 1-3 hrs |
| 12 | Validate JSON against schema; fix errors | Senior | 1-4 hrs |
| 13 | Partner review: computation logic, schedules, disclosure | Partner | 1-4 hrs |
| 14 | Upload + DSC sign | Partner | 30 min |
| 15 | Capture ITR-V / acknowledgement | Article | 5 min |
| 16 | Track 143(1) intimation (auto-processing, 6-12 months) | Senior | 30 min on receipt |
| 17 | If demand u/s 143(1): rectification u/s 154 or appeal | Manager | 4-20 hrs |
| 18 | If 143(2) scrutiny notice (within 3 months of FY end of filing): respond on e-Proceedings | Manager + Partner | 20-200 hrs |
| 19 | If 148 reassessment: more serious, file return + respond to reasons-recorded | Partner | 20-150 hrs |

**Note on notice burden:** ~1-3% of ITRs go to 143(2) scrutiny annually. Faceless assessment under §144B has standardised this; AI-assisted notice drafting and document upload is high-value here.

### OUTPUTS
- Filed ITR (acknowledgement).
- 143(1) intimation (auto, post-filing).
- Computation working paper.
- Any scrutiny/reassessment defence file.

### COMMON ERRORS / PAIN POINTS
- **AIS vs 26AS vs book divergence** (especially capital gains pre-filled from broker AIS data).
- **JSON schema updates breaking utility** — CA-alley reported Schema 2.2 for 3CB-3CD breaking older utilities silently in 2025.
- **MAT credit utilisation** — judgement-heavy carry-forward priority.
- **Foreign asset disclosure (Schedule FA)** — penalty u/s Black Money Act is harsh (₹10 L per default); CAs are conservative and over-include.
- **Section 115BAA election** — once made, irrevocable. CAs are nervous about advising opt-in.
- **Faceless assessment notice burden** — CA Mayank Mohanka writes that responses now require **structured PDF uploads with 15-day windows**, and adjournments are not freely granted.
- **Notice deadlines arrive while CA is mid-busy-season** (Sept-Nov is also when 143(2) notices flow for prior years).

### AI AUTOMATION POTENTIAL
- Step 1: Partial (document intake).
- Step 2: Full.
- Steps 3, 4, 5, 6, 7, 8: Partial. Computation logic is rule-based but judgement-laden; LLM + structured rules can do 80%.
- Step 9: Partial.
- Step 10: Full.
- Step 11: Partial → Full.
- Step 12: Full.
- Step 13: Not feasible end-to-end; AI as pre-review.
- Step 14: Not feasible.
- Step 17: Partial — AI drafts rectification request.
- **Step 18 (faceless scrutiny response): Partial.** Huge time saver. LLM can read notice, organise documents, draft response paragraphs with citations.
- Step 19: Partial.

### CANDIDATE AI WEDGES
1. **Auto-computation from audited TB + 3CD** — ingests trial balance and tax audit data, produces full ITR-6 computation with disallowance reasoning trace.
2. **Disclosure-completeness checker** — flags Schedule FA / AL / SH / MAT items likely missed by comparing to prior year + AIS data.
3. **Faceless scrutiny response drafter** — reads 143(2) notice + ITR + AIS + financials; drafts point-by-point response with case-law citations (verified, not hallucinated — see ITAT Bengaluru incident in `04-pain-points.md`).
4. **143(1) intimation auto-handler** — when intimation arrives, automatically reconciles disputed items; drafts rectification application if any mismatch.
5. **Schema-change monitor** — auto-tests utility against new schemas as they're released and patches templated returns.

### TYPICAL FEE & WHERE MANAGER TIME GOES
- **Fee:** ITR-1 ₹500-₹3,500; ITR-2 cap gains ₹2,500-₹20,000; ITR-3 business ₹5,000-₹25,000; ITR-6 company ₹15,000-₹2 L. (Ref `05-economics-billing.md` §1.2.)
- **Avg hours:** ITR-1: 0.5-2 hrs; ITR-6 SME: 30-100 hrs; ITR-6 mid-corp: 80-300 hrs.
- **Manager time:** Steps 8, 9, 13, 18 — disallowances, MAT, partner pre-review, notice response.

---

## 6. Statutory Audit (Companies Act 2013)

### WHO
- **Audit incharge:** Article or Senior leading fieldwork.
- **Engagement team:** 1 Partner + 1 Manager + 1-2 Seniors + 2-5 Articles.
- **Listed/PIE entities:** Additional EQR (Engagement Quality Reviewer), separate partner.

### WHEN
- **Engagement letter / planning:** Aug-Oct (for March year-end).
- **Interim fieldwork:** Oct-Jan.
- **Year-end fieldwork:** April-June (most clients are March year-end).
- **Audit report sign-off:** Before AGM (AGM by 30 Sept of following FY).
- **Frequency:** Once per FY per company. Mandatory for every company under Companies Act.

### INPUTS
- Engagement letter (signed by both parties).
- Prior-year audit file + report.
- Trial balance.
- General ledgers (all GLs).
- Bank statements (all bank accounts).
- Fixed asset register.
- Inventory records + physical count.
- Statutory registers (members, charges, contracts u/s 188 RPT).
- Board minutes + committee minutes.
- Tax computation.
- Bank confirmations / debtor-creditor confirmations.
- Loan agreements + charge registrations.
- Lease contracts (Ind AS 116).
- Revenue contracts (Ind AS 115).
- Salary register, EPF/ESI returns, gratuity actuarial.
- IT/GST/TDS return copies + reconciliations.
- Management representation letter (MRL).
- Going-concern + subsequent-events memo.

### STEPS

#### Phase A — Planning (Aug-Oct)
| # | Step | Who | Time |
|---|---|---|---|
| 1 | Engagement acceptance / continuance check (ICAI ethical, independence, peer-review status) | Partner | 1-2 hrs |
| 2 | Sign / renew engagement letter; agree fee | Partner | 1-2 hrs |
| 3 | File ADT-1 (if first year / re-appointment) within 15 days of AGM | Article | 1 hr |
| 4 | Understand business, environment, internal control (SA 315) — update audit risk memo | Manager | 4-12 hrs |
| 5 | Materiality determination (planning / performance / specific) — SA 320 | Manager | 1-3 hrs |
| 6 | Identify significant risks, fraud risks (SA 240), going-concern indicators | Manager | 2-6 hrs |
| 7 | Audit programme tailoring (controls + substantive) | Manager | 4-12 hrs |
| 8 | Resource plan: who works on what, hours budget | Manager | 2-4 hrs |
| 9 | Document the plan in audit file (SA 230) | Manager | 2-4 hrs |

#### Phase B — Internal Control + Interim Fieldwork (Oct-Jan)
| # | Step | Who | Time |
|---|---|---|---|
| 10 | Walkthrough of key processes (purchase-to-pay, order-to-cash, payroll, fixed assets) | Senior + Article | 8-24 hrs |
| 11 | Document understanding of IT general controls (ITGC) — change mgmt, access, backup | Senior | 4-12 hrs |
| 12 | Test design + operating effectiveness of key controls | Senior + Article | 16-60 hrs |
| 13 | Interim substantive testing: revenue cut-off, purchase cut-off, payroll | Senior + Article | 16-40 hrs |
| 14 | Manager review of interim work | Manager | 4-12 hrs |

#### Phase C — Year-end Fieldwork (April-June)
| # | Step | Who | Time |
|---|---|---|---|
| 15 | **Physical inventory count attendance** (31 March) — Article on-site at every "significant" location | Article + Senior | 8-32 hrs per location |
| 16 | Reconcile physical inventory to book inventory; document variances | Senior | 4-12 hrs |
| 17 | Fixed asset physical verification (on rotation basis) | Article | 8-24 hrs |
| 18 | **Vouching** — match sample of ledger entries to underlying invoices, vouchers, board resolutions | Article | 40-160 hrs (the article's bread and butter) |
| 19 | **Ledger scrutiny** — every major GL: opening + addition + deletion + closing; flag unusual entries | Article | 16-60 hrs |
| 20 | Bank reconciliation testing + bank confirmations from every bank | Article | 4-12 hrs |
| 21 | Debtor / creditor confirmations: send, follow up, alternative procedures for non-responders | Article | 8-40 hrs |
| 22 | Revenue testing (Ind AS 115): contract review, performance obligation, transaction price, allocation, recognition | Senior | 8-40 hrs |
| 23 | Lease testing (Ind AS 116): contracts, lease term, discount rate, ROU asset, lease liability | Senior | 4-16 hrs |
| 24 | Inventory valuation testing (Ind AS 2): cost method, NRV, slow-moving/obsolete provisioning | Senior | 8-24 hrs |
| 25 | Expected credit loss (ECL) provisioning on receivables (Ind AS 109) | Senior | 4-16 hrs |
| 26 | Statutory dues testing (TDS, GST, PF, ESI) — match returns to books | Senior | 4-12 hrs |
| 27 | Related party transactions per Sec 188 + Ind AS 24 — completeness check | Senior | 4-12 hrs |
| 28 | Loan covenants testing | Senior | 2-8 hrs |
| 29 | Tax provision + deferred tax + uncertain tax positions | Senior | 4-12 hrs |
| 30 | Going concern assessment (SA 570) — cash flow forecasts, debt covenants, post-balance-sheet events | Manager + Partner | 4-16 hrs |
| 31 | Subsequent events review (SA 560) — events between balance-sheet date and audit report date | Manager | 2-6 hrs |
| 32 | CARO 2020 reporting (16 clauses) — fixed assets, inventory, loans to related parties, internal control, statutory dues, fraud, default to FI, NPA, end-use of funds, internal audit, whistleblower, etc. | Senior + Manager | 8-24 hrs |
| 33 | Compile working papers per SA 230 (must be assembled within 60 days of audit report) | Article + Senior | 16-40 hrs |

#### Phase D — Reporting + Sign-off
| # | Step | Who | Time |
|---|---|---|---|
| 34 | Draft financial statements (often the auditor prepares them for SMEs even though it's management's responsibility) | Senior | 8-24 hrs |
| 35 | Draft audit report (SA 700 / 705 / 706): unmodified / qualified / adverse / disclaimer; emphasis-of-matter; KAM for listed | Manager + Partner | 4-16 hrs |
| 36 | Key Audit Matters (KAM) for listed entities — describe each KAM and audit response | Partner | 4-12 hrs |
| 37 | Manager review file + manager sign-off | Manager | 8-24 hrs |
| 38 | Partner review (entire file or sample) | Partner | 8-40 hrs |
| 39 | EQR (Engagement Quality Reviewer) review for listed/PIE | Independent partner | 8-30 hrs |
| 40 | Management representation letter signed | Partner | 1-2 hrs |
| 41 | Audit committee presentation | Partner | 2-4 hrs |
| 42 | Final partner DSC sign on report (with UDIN) | Partner | 1-2 hrs |
| 43 | File AOC-4 with signed financials + audit report | Article | 1-2 hrs |
| 44 | Archive working paper file (retain 7 years per SA 230) | Article | 4-8 hrs |

**Total audit hours, by client size (small-mid Indian firm, March year-end Pvt Ltd, mid-tier complexity):**
- Small Pvt Ltd (≤₹2 cr turnover): 60-120 hrs.
- Mid-size Pvt Ltd (₹2-25 cr): 150-400 hrs.
- Listed mid-cap: 800-3,000 hrs.
- Big 4 client: 5,000-50,000+ hrs.

### OUTPUTS
- Signed audit report (unmodified / qualified / adverse / disclaimer).
- Signed financial statements.
- CARO report.
- Management letter (deficiencies in internal control).
- Working paper file (retained 7 years).
- AOC-4 filing.

### COMMON ERRORS / PAIN POINTS
- **Vouching mechanical, low-judgement** (CAclubindia: "we have to jst click few things") — but takes 40-160 hrs per audit.
- **Excel working papers** non-reproducible across firms / engagements; copy-paste errors carry forward.
- **Document delays from client** — most audits are 30-50% over budget hours due to client information lag.
- **Bank confirmation collection physical** — many banks still want physical letter pickup; CA's article spends days at branches.
- **Inventory count travel** — Hemil Shah's quote: "1-1.5 months in rural area auditing the factory."
- **Going concern assessment** — judgement-heavy; partner anxiety.
- **CARO clauses 9 (default to FI) / 13 (RPT) / 14 (Internal audit) / 17 (fraud)** are repeatedly flagged for non-compliance in peer review.
- **Partner sign-off queue** during Sept (tax audit) + April-July (statutory audit).
- **Ind AS 115/116 first-year transitions** — disproportionate manager time.

### AI AUTOMATION POTENTIAL
- Steps 1-3: Partial (admin).
- **Step 4-6 (risk assessment, materiality):** Partial. AI can ingest prior year file + industry data and propose risk register; CA reviews.
- Steps 10-12 (control walkthrough/testing): Partial.
- **Step 18 (Vouching): Partial → Full.** Voucher → invoice → ledger match, OCR + LLM. Massive leverage.
- **Step 19 (Ledger scrutiny): Partial → Full.** LLM + anomaly detection on every GL — outliers, round-figures, week-end entries, period-end reversals, related-party links.
- Step 20: Partial.
- Step 21 (confirmations): Partial — auto-draft + chase, but human verifies signed reply.
- Steps 22-29 (Ind AS substantive): Partial.
- Step 30 (going concern): Not feasible end-to-end.
- Step 32 (CARO): Partial — clause-wise checklist auto-fillable with disclosures from books.
- Step 33 (working paper compile): **Partial → Full.** SA 230 compliant auto-indexed file from audit-execution platform.
- Step 35 (audit report): Partial.
- Steps 36-39 (KAM, manager/partner review): Not feasible end-to-end; AI as pre-review.
- Step 43 (AOC-4 file): Full.

### CANDIDATE AI WEDGES
1. **Voucher-to-ledger matcher** — OCR client's physical/PDF vouchers, LLM-classify, match to Tally/SAP ledger entry, generate vouching trail with confidence + exception list. Replaces 40-160 hrs of article work per audit.
2. **Ledger scrutiny anomaly detector** — for every GL, runs (a) round-figure detection, (b) period-end / weekend posting, (c) reversed-next-day pattern, (d) RPT classification, (e) GL-purpose-vs-entry semantic check. Generates a "review only flagged items" file for senior.
3. **CARO clause auto-filler** — ingests TB, statutory registers, board minutes; pre-fills each of 16 CARO clauses with proposed answer + cited evidence + remaining-to-verify list.
4. **Audit working paper auto-compiler (SA 230)** — every step + sample + evidence captured into structured working paper; reduces 16-40 hrs of post-audit compilation to <2.
5. **Subsequent events tracker** — between BS date and audit report date, monitors client public filings, news, related-party transactions, bank account movements; alerts partner.

### TYPICAL FEE & WHERE MANAGER TIME GOES
- **Fee:** Small Pvt Ltd ₹15,000-₹50,000; mid ₹50,000-₹15 L; listed ₹50 L-₹15 cr. (Ref `05-economics-billing.md` §1.3.)
- **Avg hours:** As above — 60 hrs (small) to 50,000+ (Big 4 listed).
- **Manager time:** Steps 4-9 (planning ~30%), step 14 + 37 (review ~40%), steps 30-32 (Ind AS / going-concern / CARO ~30%).

---

## 7. Tax Audit (Section 44AB) — Form 3CA/3CB + 3CD

### WHO
- **Prep of 3CD clauses:** Article + Senior.
- **Review:** Manager.
- **Sign-off (UDIN):** Partner.

### WHEN
- **Trigger:** Turnover > ₹1 cr (or ₹10 cr if 95% digital), or professional receipts > ₹50 L, or presumptive scheme opt-out.
- **Deadline:** **30 September** of following FY for non-TP cases (often extended to 31 October).
- **Frequency:** Once per assessee per FY. Same CA can sign max 60 tax audits per FY (ICAI cap).

### INPUTS
- Audited financial statements (3CB cases: CA does both stat + tax audit; 3CA cases: when other law has already audited e.g., banks, statutory audit firm separate).
- Trial balance.
- Books of account.
- Statutory dues registers (TDS, GST, PF, ESI).
- Loan registers.
- Fixed asset register + depreciation chart.
- Inventory valuation working.
- Cash payments > ₹10,000 register (40A(3)).
- Sec 269ST / 269SS / 269T compliance (cash loans/repayments >₹20K).
- Related party register.
- GSTR-9C / GSTR-9 (reconciliation feeds clause 44).

### STEPS

| # | Step | Who | Time |
|---|---|---|---|
| 1 | Determine 44AB applicability (turnover + digital %, presumptive opt-out) | Senior | 30 min |
| 2 | Choose Form 3CA (other law audit) or 3CB (no other law audit) | Senior | 5 min |
| 3 | Pull all 41+ clauses of Form 3CD checklist | Article | — |
| 4 | Clause 4 — registration numbers (PAN, GST, IEC, etc.) | Article | 30 min |
| 5 | Clauses 8-13 — Sec 44AB applicability, books maintained, method of accounting | Article | 1-2 hrs |
| 6 | Clause 14 — method of stock valuation, deviation | Senior | 1-3 hrs |
| 7 | Clause 16 — amounts not credited to P&L (capital receipts, deemed income, escalation) | Senior | 1-3 hrs |
| 8 | Clause 17 — properties transferred at less than stamp duty value (50C) | Senior | 30 min |
| 9 | Clause 18 — depreciation schedule per Income-tax Act (vs books) | Senior | 2-6 hrs |
| 10 | Clause 19 — amounts deductible u/s 33AB / 33ABA etc. | Senior | 30 min |
| 11 | Clauses 20-21 — bonuses, statutory dues, employee welfare 43B | Senior | 1-3 hrs |
| 12 | Clause 21 — disallowable items: personal expenses, payment exceeding cash limit, fines/penalties | Senior | 2-6 hrs |
| 13 | Clauses 22-23 — interest to non-residents, payments to specified persons u/s 40A(2) | Senior | 1-3 hrs |
| 14 | Clause 24 — deemed profits u/s 32AC, 33AB etc. | Senior | 30 min |
| 15 | Clause 25 — profits chargeable u/s 41 (remission of liability) | Senior | 30 min |
| 16 | Clauses 26-27 — Sec 43B disallowance for unpaid statutory dues; CENVAT credit | Senior | 1-3 hrs |
| 17 | Clauses 28-29 — Sec 56(2)(viia/viib) deemed gifts/share premium | Senior | 1-3 hrs |
| 18 | Clauses 30-30C — 269SS / 269ST / 269T loan-and-cash reporting | Senior | 1-3 hrs |
| 19 | Clause 31 — particulars of loans + deposits accepted/repaid | Article | 2-6 hrs |
| 20 | Clause 32 — brought forward losses + unabsorbed depreciation chart | Senior | 1-3 hrs |
| 21 | Clause 33 — deductions claimed under Chapter VIA / 80IA etc. | Senior | 30 min |
| 22 | Clause 34 — TDS / TCS particulars: section, threshold, deducted, paid, return filed | Senior | **4-12 hrs (often the heaviest single clause)** |
| 23 | Clause 35 — quantitative details of trading/manufacturing | Senior | 2-4 hrs |
| 24 | Clause 36 — dividend distribution tax (largely irrelevant post 2020) | Senior | 30 min |
| 25 | Clause 37 — cost audit conducted? (link) | Senior | 15 min |
| 26 | Clause 38 — Central Excise audit conducted? (legacy) | Senior | 15 min |
| 27 | Clause 39 — Service tax audit conducted? (legacy) | Senior | 15 min |
| 28 | Clause 40 — ratios: gross profit/turnover, net profit/turnover, stock-in-trade/turnover, material consumed/finished | Senior | 2-4 hrs |
| 29 | Clause 41 — demands raised / refunds issued under any other tax law (GST, customs, state VAT legacy) | Senior | 1-3 hrs |
| 30 | Clause 42-43 — Furnishing of statement on income; details of GST collected/paid | Senior | 1-2 hrs |
| 31 | **Clause 44 — break-up of total expenditure with GST-registered vs unregistered vendors** (the "excruciating" clause per IndiaFilings commentary; needs full purchase classification across the year) | Senior + Article | **6-30 hrs** |
| 32 | Manager review of 3CD | Manager | 4-12 hrs |
| 33 | Partner review + UDIN generation | Partner | 2-6 hrs |
| 34 | Upload 3CA/3CB-3CD JSON to portal; DSC sign | Partner | 30 min |
| 35 | Capture acknowledgement; link to ITR-6/3 | Article | 15 min |

**Total time per tax audit (small Pvt Ltd):** 30-80 hrs. **Mid-size:** 80-250 hrs.

### OUTPUTS
- Form 3CA or 3CB.
- Form 3CD (all 41+ clauses).
- UDIN.
- Filing acknowledgement (linked to ITR).

### COMMON ERRORS / PAIN POINTS
- **Clause 34 (TDS particulars) and Clause 44 (expenditure with GST registration status) are the heaviest.** Clause 44 requires every line of expenditure classified as: spent with GST-registered (composition vs regular), unregistered, or exempt vendors. Industry commentary: "excruciating pain" (IndiaFilings).
- **Clause 21 disallowables** require article to read every voucher for personal/fines/cash-limit-violation — subjective.
- **Clause 31 — loan/deposit movements** requires full sub-ledger movement schedule.
- **Schema updates** (Schema 2.2 for 3CB-3CD in 2025) reject older JSON files with cryptic errors (CA-alley reported).
- **September 30 portal collapse** — same as `04-pain-points.md`: IT portal goes down on deadline day; CAs work till midnight.
- **60 tax audits per CA per year cap** is a hard ICAI limit; firms with high client load must have many partners.

### AI AUTOMATION POTENTIAL
- Steps 4, 5, 25-27: Full.
- Step 9 (depreciation IT-Act): Full.
- Step 22 (Clause 34 TDS particulars): **Partial → Full** if TDS workflow is on the same platform; auto-populate.
- Step 31 (Clause 44 expenditure breakdown): **Partial → Full.** AI ingests purchase register + vendor GSTIN list, classifies every line by vendor GST status, produces clause-44 breakdown.
- Steps 6-21, 23-30: Partial — rule-engine + LLM.
- Steps 32-34: Not feasible end-to-end.

### CANDIDATE AI WEDGES
1. **Clause 44 auto-classifier** — every purchase line ↔ vendor GSTIN status (composition / regular / unregistered / exempt) via real-time GSTN lookup, produces the entire clause 44 table.
2. **Clause 34 TDS auto-cross-check** — pulls from TDS workflow (work 4 above), reconciles to books, flags every default.
3. **3CD inter-clause consistency checker** — e.g., 269SS loans reported in Clause 31 must reconcile with cash flow statement; 56(2) gifts in Clause 28-29 must tie to share capital movements.
4. **Schema-change auto-handler** — silently upgrades JSON template when CBDT pushes new schema.
5. **3CD "what's new this year" agent** — compares prior year 3CD to current year, flags every material delta with explanation requirement.

### TYPICAL FEE & WHERE MANAGER TIME GOES
- **Fee:** Small ₹15,000-₹50,000; mid ₹75,000-₹5 L. (Ref `05-economics-billing.md` §1.3.)
- **Avg hours:** 30-250 hrs.
- **Manager time:** Clauses 21, 22, 31, 44; final review.

---

## 8. ROC / MCA Compliance

### WHO
- **DIR-3 KYC, AOC-4, MGT-7 prep:** Article + paid accountant.
- **Board minutes drafting (often by CS):** Manager / CS.
- **Sign-off + DSC:** Partner (auditor signs AOC-4 attachment) + Director (signs ROC form).

### WHEN

| Form | Trigger | Deadline | Frequency |
|---|---|---|---|
| **ADT-1** | Auditor appointment | 15 days from AGM | Annually (5-year if reappointed under §139(2)) |
| **DIR-3 KYC** | Every DIN holder | 30 Sept | Annual |
| **AOC-4** | Filing of financial statements | 30 days from AGM (i.e., ~29-30 Oct) | Annual |
| **MGT-7** | Annual return | 60 days from AGM (~28 Nov) | Annual |
| **DPT-3** | Return of deposits | 30 June | Annual |
| **MSME-1** | Outstanding to MSME vendors | 30 Apr / 31 Oct (half-yearly) | Bi-annual |
| **BEN-2** | Significant beneficial owner change | 30 days from event | Event-based |
| **CHG-1/4/9** | Charges on assets (creation/satisfaction/modification) | 30 days | Event-based |
| **MGT-14** | Board resolutions (specific) | 30 days | Event-based |
| **AOC-2** | Related party transactions | With AOC-4 | Annual |
| **AGM** | Annual general meeting | Within 6 months of FY end (30 Sept) | Annual |

### INPUTS
- Audited financials + auditor's report + board's report.
- Shareholder register, share transfer register.
- Director & KMP details + DIN status.
- Board minute book + AGM minutes.
- DSC of director(s) + practicing CS (or CA where allowed).
- Statutory registers (charges, RPT, contracts).
- Outstanding to MSMEs (45+ days).
- Loan / deposit register (DPT-3).

### STEPS — Annual filing cycle for a typical Pvt Ltd (Oct-Nov crunch)

| # | Step | Who | Time |
|---|---|---|---|
| 1 | Reminder to client: AGM by 30 Sept | Article | 5 min |
| 2 | Coordinate AGM date; draft AGM notice + explanatory statement | Article + CS | 1-2 hrs |
| 3 | Hold AGM; record minutes; sign register | CS / director | 1-2 hrs |
| 4 | DIR-3 KYC for every DIN holder by 30 Sept | Article | 30 min/DIN |
| 5 | ADT-1 (auditor appointment) within 15 days of AGM | Article | 1 hr |
| 6 | Prepare AOC-4: attach financials, board's report, auditor's report, CSR if applicable, AOC-2 RPT details | Article + accountant | 4-12 hrs |
| 7 | Validate AOC-4: ensure auditor DSC affixed on attached audit report; director DSC on form | Article | 1-2 hrs |
| 8 | Upload AOC-4 within 30 days of AGM; pay govt fee | Article | 1-2 hrs |
| 9 | Prepare MGT-7: shareholders, shareholding pattern, directors, board meetings, indebtedness, penalties | Article + CS | 4-12 hrs |
| 10 | PCS (Practicing Company Secretary) certifies MGT-7 (required for Pvt with capital ≥ ₹10 cr or turnover ≥ ₹50 cr; else director signs MGT-7A) | CS | 1-2 hrs |
| 11 | Upload MGT-7 within 60 days of AGM | Article | 1 hr |
| 12 | DPT-3 by 30 June (loans/deposits outstanding as on 31 March) | Article | 1-3 hrs |
| 13 | MSME-1 by 30 Apr / 31 Oct (vendor dues > 45 days) | Article | 2-6 hrs |
| 14 | Event-based forms as triggered: BEN-2, CHG-1, MGT-14 | Article | 30-90 min each |

### OUTPUTS
- All ROC forms filed (each with SRN — Service Request Number).
- Government acknowledgement.
- Updated company master data on MCA21.

### COMMON ERRORS / PAIN POINTS
- **MCA21 V3 portal disasters** (per `04-pain-points.md`): "user already logged in", DSC association failure, payment failures over 30 days deactivating DIN.
- **DSC chain-of-trust issues** (Java + emSigner + browser + token).
- **AOC-4 attachment rejection** if auditor's DSC on signed PDF is missing or mismatched.
- **MGT-7 vs MGT-7A confusion** — many small CAs file wrong form.
- **MSME-1 vendor identification** — clients often don't know which vendors are MSME-registered.
- **Off-hours filing** — "many CAs file after 9 pm to avoid load."
- **Late fee:** ₹100/day for AOC-4 and MGT-7 — uncapped.
- **DIR-3 KYC default = ₹5,000 + DIN deactivation.**

### AI AUTOMATION POTENTIAL
- Steps 4, 6, 9, 12, 13: **Partial → Full.** Forms are data-template + attachments; standardised.
- Step 8, 11: Partial — upload + DSC. AI prep + human DSC.
- Step 10 (CS certification): Not feasible (statutory).
- Step 14 (event-based): Partial — needs trigger detection.

### CANDIDATE AI WEDGES
1. **Annual filing calendar agent** — auto-tracks every client's AGM date, computes all derived deadlines (ADT-1, AOC-4, MGT-7, DIR-3 KYC), nags responsible article + partner.
2. **AOC-4 / MGT-7 auto-drafter** — from prior year + updated TB + register data; produces fillable PDF for director review.
3. **MSME vendor classifier** — looks up every client vendor against Udyam database; identifies MSME-registered + their payment cycle for MSME-1 reporting.
4. **DPT-3 loan-deposit categoriser** — classifies every credit balance in books as (a) deposit, (b) loan from director, (c) trade advance — DPT-3 categories.
5. **MCA21 portal retry agent** — handles "user already logged in" and payment-failure retries automatically; queues filings for off-peak hours.

### TYPICAL FEE & WHERE MANAGER TIME GOES
- **Fee:** AOC-4 ₹3,000-₹10,000; MGT-7 ₹5,000-₹15,000; DIR-3 KYC ₹500-₹2,500; DPT-3 ₹2,000-₹7,500; MSME-1 ₹1,500-₹5,000. Online aggregators have driven the bundle to ₹1,000-₹3,000. (Ref `05-economics-billing.md` §1.5.)
- **Avg hours per Pvt Ltd:** 15-40 hrs/year.
- **Manager time:** ~10-20% — most is article + accountant + portal.

---

## 9. Transfer Pricing — Form 3CEB + Master File 3CEAA + CbCR

### WHO
- **TP study + benchmarking:** Specialist TP team (Big 4 / mid-tier) OR outsourced (small firms outsource to TP boutiques).
- **Form 3CEB certification:** Partner (signing CA).
- **Master File / CbC:** CFO / Head of Tax in-house; CA signs.

### WHEN
- **Form 3CEB:** Due **31 October** of following FY (with ITR for TP cases due 30 Nov).
- **Master File (3CEAA):** Due **30 November**.
- **3CEAB (intimation of group entity to file):** 30 days before 3CEAA due date.
- **CbC Report (3CEAD):** 12 months from end of reporting accounting year.
- **CbC notification (3CEAC):** 60 days before report due.
- **Frequency:** Once per FY, for entities with international/specified-domestic transactions.

### INPUTS
- Audited financials.
- Related-party schedule with country, transaction type, amount.
- ICAI AS 18 / Ind AS 24 RPT disclosure.
- Functions-Assets-Risks (FAR) analysis per entity.
- Industry benchmarking (Royalty databases — RoyaltyStat, ktMINE; Comparable databases — Prowess, Capitaline, Bloomberg).
- Group structure chart.
- Group consolidated financials.
- Inter-company agreements.
- For CbC: group revenue, profit, tax paid, headcount, tangible assets per country.

### STEPS

| # | Step | Who | Time |
|---|---|---|---|
| 1 | Identify all related-party transactions: tangible / intangible / financial / services | Senior + client | 4-12 hrs |
| 2 | Map each RPT to TP method: CUP / RPM / CPM / TNMM / PSM | TP specialist | 8-24 hrs |
| 3 | Conduct FAR (Functions-Assets-Risks) analysis | TP specialist | 16-60 hrs |
| 4 | Benchmarking study: extract comparables from Prowess/Capitaline, screen, accept/reject, compute arm's-length range | TP specialist | 40-160 hrs |
| 5 | Prepare TP study report (entity, industry, FAR, method, comparables, conclusion) | TP specialist | 40-120 hrs |
| 6 | Tabulate Form 3CEB: ~30 disclosure tables (international transactions, deemed international, specified domestic) | TP specialist | 12-40 hrs |
| 7 | Partner review + UDIN | Partner | 4-12 hrs |
| 8 | DSC sign + upload Form 3CEB | Partner | 30 min |
| 9 | Prepare Master File (3CEAA) Part A (basic) + Part B (only if turnover > ₹500 cr AND aggregate international RPT > ₹50 cr) | TP specialist | 40-120 hrs |
| 10 | Sign + upload Master File | Partner | 30 min |
| 11 | CbC notification (3CEAC) — if Indian parent > ₹6,400 cr group revenue | CFO | 1-2 hrs |
| 12 | CbC report (3CEAD) for Indian-headquartered MNEs (or if local filing trigger met) | CFO + TP specialist | 40-120 hrs |

### OUTPUTS
- Form 3CEB filed.
- TP study report (kept on file 8 years).
- Master File filed (if applicable).
- CbC notification + report (if applicable).

### COMMON ERRORS / PAIN POINTS
- **Benchmarking database access** is expensive (Prowess subscription ₹2-10 L+/yr) — most small firms outsource.
- **Functional analysis subjective** — leads to TP disputes.
- **Group entity coordination** for Master File / CbC — many cross-border emails.
- **3CEB is voluminous** — every related-party transaction must be reported regardless of materiality. International AE transactions: no threshold.
- **Specified Domestic Transactions** (Sec 92BA) — historically large; reduced post-2017 but still relevant for certain SEZ/tax-holiday cases.
- **TP audit + dispute cycle** is multi-year — APAs (Advance Pricing Agreements) reduce but don't eliminate.

### AI AUTOMATION POTENTIAL
- Step 1: Partial (RPT identification from books).
- Step 2: Partial.
- Step 3: Partial.
- **Step 4 (benchmarking): Partial → Full.** Database screening, comparability adjustments, statistical range — RPA + LLM.
- Step 5 (TP study report): **Partial.** LLM can draft 60-70% of the boilerplate; CA tunes industry-specific sections.
- Step 6 (3CEB tabulation): Full from books + transaction master.
- Steps 7, 8, 10: Not feasible end-to-end.
- Step 9 (Master File): Partial — drafter.
- Step 12 (CbC): Partial.

### CANDIDATE AI WEDGES
1. **Comparable screening agent** — pulls from Prowess/Capitaline; runs the 6-7 screening filters (size, geography, functions, R&D ratio, ownership, segment data, loss-making); produces rejected/accepted list with reasoning.
2. **TP study auto-drafter** — generates industry analysis, FAR write-up boilerplate, method selection rationale, comparability adjustments table; CA edits.
3. **3CEB transaction tabulator** — auto-categorises every related-party ledger entry into the 21 prescribed transaction types; produces the form-ready table.
4. **Master File / CbC consistency checker** — verifies cross-document consistency (Master File entity list vs CbC entity list vs ITR Schedule SH vs ROC filings).
5. **APA precedent matcher** — given a transaction's facts, surfaces all relevant APAs and ITAT decisions in similar industry/geography.

### TYPICAL FEE & WHERE MANAGER TIME GOES
- **Fee:** Small TP (only 3CEB + light benchmarking) ₹75,000-₹2 L; mid-tier ₹5-15 L; large MNE Master File ₹15-50 L. Big 4 ₹25 L-₹2 cr. (Ref `05-economics-billing.md` §1.3.)
- **Avg hours:** 80-1,000 hrs depending on transactions.
- **Manager / TP specialist time:** ~70% (high-skill labour, not article-leveraged like statutory audit).

---

## 10. Scrutiny / Faceless Assessment

### WHO
- **First response drafting:** Senior / Manager.
- **Critical positions, hearing if any:** Partner.
- **Document compilation:** Article.

### WHEN
- **143(1) intimation:** Auto, within 12 months of filing. CPC-generated.
- **143(2) scrutiny notice:** Within 3 months from end of FY of filing (e.g., for ITR filed FY 25-26, notice by 30 June 27 — though tightened recently).
- **142(1) inquiry notice:** Any time during assessment.
- **148 reassessment notice:** Up to 10 years for serious cases.
- **156 demand notice:** Post-order.
- **Frequency:** ~1-3% of ITRs scrutinised; 100% of high-net-worth and corporate are scrutinised periodically.

### INPUTS
- The notice itself (PDF on e-Proceedings).
- Original ITR + computation.
- Audited financials + tax audit.
- 26AS / AIS / TIS.
- All ledgers / vouchers / bank statements for the relevant year.
- Prior-year orders / appeals (precedent for the assessee).
- Case-law database (Taxmann, Taxsutra, CCHTaxOnline).
- Source documents for any specific item flagged.

### STEPS

| # | Step | Who | Time |
|---|---|---|---|
| 1 | Notice received (email + e-Proceedings) — date-stamp and log | Article | 5 min |
| 2 | Read notice; identify (a) section, (b) AY, (c) specific items/issues flagged, (d) deadline (typically 15 days) | Senior | 30-60 min |
| 3 | Pull original ITR + computation + financials + supporting | Article | 1-3 hrs |
| 4 | Research applicable provisions + case law for each flagged item | Manager | 4-20 hrs |
| 5 | Draft preliminary response paragraph-by-paragraph | Manager | 4-30 hrs |
| 6 | Compile supporting PDFs (bank statements, contracts, invoices, board resolutions) | Article | 4-16 hrs |
| 7 | Internal review with partner | Partner | 2-8 hrs |
| 8 | Upload response on e-Proceedings (PDF + structured form) with DSC | Senior | 1-2 hrs |
| 9 | Wait for next notice (further enquiry) — iterate | All | — |
| 10 | If draft assessment order with proposed addition: file objections + variation request | Manager | 8-40 hrs |
| 11 | Final order received: review for additions, demand u/s 156 | Manager | 1-4 hrs |
| 12 | If demand: pay 20% within 30 days; file rectification u/s 154 or appeal u/s 246A to CIT(A) within 30 days | Manager + Partner | 8-40 hrs |
| 13 | If CIT(A) adverse: ITAT appeal within 60 days | Partner / counsel | 40-200 hrs |

**Total time per notice cycle:** 20-200+ hrs depending on complexity. Big-ticket faceless scrutiny commonly consumes 100-300 hrs per case. nabsai.com: "4-8 hours of qualified CA time per notice."

### OUTPUTS
- Notice response (PDF + e-form).
- Compiled supporting file.
- Assessment order.
- Appeal/rectification if required.

### COMMON ERRORS / PAIN POINTS
- **15-day window is tight** — clients delay producing source docs.
- **gstnoticeai.com:** "1 in 3 CA firms have missed a notice deadline in the past year."
- **Faceless = no relationship leverage** — earlier you could request adjournment in-person; now strictly per system rules.
- **AI hallucination risk** — ITAT Bengaluru's order cited non-existent SC judgments (per `04-pain-points.md`) — CAs are nervous about LLM-drafted responses without verification.
- **Document collection at deadline** — articles spend nights at client's office.
- **Multi-year scrutiny** — same year reopens 3-7 years later under 148.
- **Demand / refund mismatch** — even after favourable order, refund takes 6-18 months.

### AI AUTOMATION POTENTIAL
- Step 2: Full (LLM reads + structures notice).
- Step 3: Full (if connected to firm's filing archive).
- **Step 4 (case-law research): Partial — LLM with verified-citation RAG.**
- **Step 5 (response drafting): Partial.** Big productivity win. With verification layer to prevent hallucinated cites.
- Step 6: Partial (auto-bundle documents).
- Step 7: Not feasible (partner judgement).
- Step 8: Partial (upload).
- Steps 10-13: Partial (drafting).

### CANDIDATE AI WEDGES
1. **Notice triager** — reads every 143/142/148 notice on receipt; extracts (a) issues flagged, (b) section, (c) deadline, (d) required documents; opens a workflow with checklist.
2. **Verified-citation response drafter** — drafts paragraph-by-paragraph response with case-law citations, where every cited case is verified against ITAT / SC databases (no hallucination).
3. **Auto-evidence bundler** — for each flagged item, pulls the relevant invoices, ledgers, bank statements, contracts from the firm's archive; produces a numbered annexure file.
4. **Cross-year defence consistency checker** — ensures position taken in current notice doesn't contradict prior year orders or returns; flags risk.
5. **Demand-vs-payment-vs-stay tracker** — automates the post-order workflow (pay 20%, file appeal, request stay, track refund) with calendar.

### TYPICAL FEE & WHERE MANAGER TIME GOES
- **Fee:** ₹10,000-₹50,000 small notice; ₹50,000-₹3 L corporate; ₹3-15 L mid-tier; ₹5L-1 cr+ for ITAT appeals at Big 4. (Ref `05-economics-billing.md` §1.1.)
- **Avg hours:** 20-300 hrs.
- **Manager time:** 60-80% — this is *the* high-skill, partner/manager-bound work that articles cannot do.

---

## 11. Internal Audit

### WHO
- **Audit team (separate from statutory auditor):** A different CA firm (or in-house team) typically appointed annually by Audit Committee.
- **Day-to-day execution:** Articles / Seniors on rotation.
- **Reporting:** Manager / Partner to Audit Committee.

### WHEN
- **Applicability** (Sec 138 Companies Act + Rule 13):
  - Every listed company.
  - Every unlisted public company with paid-up capital ≥ ₹50 cr, OR turnover ≥ ₹200 cr, OR outstanding loans/borrowings from banks/PFIs ≥ ₹100 cr, OR outstanding deposits ≥ ₹25 cr.
  - Every private company with turnover ≥ ₹200 cr OR borrowings ≥ ₹100 cr.
- **Frequency:** Continuous; reports quarterly to Audit Committee.

### INPUTS
- Risk register (organisation-wide).
- Process documentation (purchase, sales, HR, IT).
- SoX/IFC controls library (if listed / global).
- Prior internal audit reports.
- Management's risk universe.
- Audit Committee instructions.

### STEPS

| # | Step | Who | Time |
|---|---|---|---|
| 1 | Risk-based annual audit plan (cover ~20-30 processes/units over 12 months) | Manager + Audit Committee | 20-60 hrs |
| 2 | Audit Committee approval of plan | Partner | 2-4 hrs |
| 3 | Per-engagement scoping (e.g., this month: Plant 1 Procurement) | Manager | 4-12 hrs |
| 4 | Walkthrough + control documentation | Senior + Article | 8-24 hrs |
| 5 | Control testing (sample-based) | Senior + Article | 16-60 hrs |
| 6 | Substantive analytical procedures | Senior | 8-24 hrs |
| 7 | Findings discussion with process owner (management response collection) | Manager | 4-12 hrs |
| 8 | Draft internal audit report (issue → root cause → recommendation → management response) | Manager | 8-24 hrs |
| 9 | Partner review | Partner | 2-8 hrs |
| 10 | Audit Committee presentation (quarterly) | Partner | 4-8 hrs |
| 11 | Follow-up tracking on prior findings | Senior | 4-12 hrs/qtr |
| 12 | IFC (Internal Financial Controls) audit — annually, by 30 Sept of next FY | Manager + Article | 80-300 hrs |

### OUTPUTS
- Quarterly internal audit reports.
- IFC audit memo.
- Findings tracker.
- Management letter.

### COMMON ERRORS / PAIN POINTS
- **Scope creep** — management asks internal audit to "also look at X".
- **Closing prior findings** — most are not closed; carry forward.
- **Process-owner non-cooperation** during testing.
- **IFC under-tested** for listed cos.
- **No standardised IA platform** — most firms use Excel + Word.
- Pricing pressure (internal audit margins eroding).

### AI AUTOMATION POTENTIAL
- Steps 1-3: Partial.
- **Step 4 (process documentation): Partial.** AI can ingest SOPs + ERP screens + reverse-engineer process map.
- **Step 5 (control testing): Partial → Full.** Most controls are rules ("no PO above ₹5L without director sign", "all invoices > ₹1L need 3 quotes") that can be tested 100% on data instead of sample.
- Step 6: Partial.
- Step 8 (report drafting): Partial.
- Step 11 (follow-up): Full.

### CANDIDATE AI WEDGES
1. **100% population control tester** — replaces sample testing; ingests ERP transactions and tests every transaction against control rule library.
2. **Process-mining auto-discovery** — from ERP logs, builds actual process map (vs documented one) and flags deviations.
3. **IFC test-of-design + test-of-operating-effectiveness auto-tool** — runs the IFC control matrix end-to-end with sampling auto-selected.
4. **Findings auto-classifier** — risk-rates each finding (high/med/low); proposes recommendation from a library; tracks management commitments.
5. **Quarterly Audit Committee memo drafter** — assembles findings, status of prior findings, trend across quarters into the standard memo.

### TYPICAL FEE & WHERE MANAGER TIME GOES
- **Fee:** ₹50,000-₹15 L/year. (Ref `05-economics-billing.md` §1.3.)
- **Avg hours per quarter per client:** 80-400 hrs.
- **Manager time:** ~40% — scoping, report drafting, Audit Committee.

---

## 12. Certifications — 15CA/15CB, Net Worth, CMA / Project Finance

### WHO
- **15CA/CB:** Senior preps, Partner signs (Partner signs 15CB).
- **Net worth cert:** Senior preps, Partner signs.
- **CMA:** Senior + Manager (financial modelling).

### WHEN
- **15CA/CB:** Per remittance, event-based.
- **Net worth:** On client request (visa, loan, etc.).
- **CMA:** When client applies for/renews bank loan.

### INPUTS

**For 15CA/15CB:**
- Invoice from foreign party.
- Remittance amount, purpose code, beneficiary details.
- TRC (Tax Residency Certificate) + Form 10F from foreign party (if claiming DTAA).
- Declaration of no-PE.
- A2 form.
- DTAA article reference.
- Bank account details.

**For Net Worth Cert:**
- PAN, Aadhaar.
- Bank statements (FDs, savings).
- Property documents + market valuation.
- Shareholding / mutual fund statements.
- Loan statements (subtract liabilities).
- Insurance policies (surrender value).
- Gold/silver valuation.

**For CMA:**
- 2-3 years audited financials.
- Current year provisional / estimated.
- Future projections (3-5 years, monthly Y1).
- Production/sales capacity plan.
- Cost build-up, gross margin assumption.
- Working capital cycle (debtor / inventory / creditor days).
- CapEx plan with depreciation.
- Repayment schedule of existing + proposed loan.
- Industry benchmarks (TEV-study analog).

### STEPS — 15CB illustrative

| # | Step | Who | Time |
|---|---|---|---|
| 1 | Determine if 15CB applicable (remittance > ₹5 L or taxable) | Senior | 15 min |
| 2 | Check Sec 195 applicability | Senior | 30 min |
| 3 | Determine DTAA benefit if foreign party has TRC + 10F | Senior | 30-60 min |
| 4 | Identify nature of payment (royalty, FTS, business income, dividend, interest) under DTAA | Senior | 30-60 min |
| 5 | Determine if PE exists in India | Senior | 30 min |
| 6 | Determine TDS rate (DTAA vs IT Act, whichever lower) | Senior | 15 min |
| 7 | Draft 15CB | Senior | 30-60 min |
| 8 | Partner review + UDIN + DSC sign | Partner | 30 min |
| 9 | Client uses 15CB to file 15CA online | Client/Senior | 15 min |

**Total time per 15CB:** 2-5 hrs.

### STEPS — Net Worth Cert

| # | Step | Who | Time |
|---|---|---|---|
| 1 | Client provides asset-liability list | Client | — |
| 2 | Verify each asset with supporting | Senior | 1-3 hrs |
| 3 | Subtract liabilities | Senior | 30 min |
| 4 | Draft cert on letterhead with valuation date | Senior | 30 min |
| 5 | Partner UDIN + DSC sign | Partner | 15 min |

**Total time:** 2-5 hrs.

### STEPS — CMA Report

| # | Step | Who | Time |
|---|---|---|---|
| 1 | Collect prior year audited financials | Article | 1 hr |
| 2 | Build current year estimated | Senior | 2-6 hrs |
| 3 | Discussion with client on growth assumptions | Senior | 2-4 hrs |
| 4 | Build 3-5 year projections (P&L, BS, CF) in CMA template | Senior | 8-24 hrs |
| 5 | Compute MPBF (Maximum Permissible Bank Finance) per Tandon Committee method 1 or 2 | Senior | 1-3 hrs |
| 6 | Compute key ratios: CR, DSCR, ISCR, TOL/TNW, debt-equity | Senior | 1-3 hrs |
| 7 | Stress-test sensitivities | Manager | 2-6 hrs |
| 8 | Partner review | Partner | 1-3 hrs |
| 9 | Submit to bank with covering note | Senior | 1 hr |

**Total time per CMA:** 16-50 hrs.

### COMMON ERRORS / PAIN POINTS
- **15CB DTAA misinterpretation** — wrong rate applied = under-deduction = penalty for the client.
- **TRC validity** — must be for the relevant FY of remittance.
- **Net worth valuations subjective** — real-estate fair-value vs cost price; insurance surrender value.
- **CMA projections unrealistic** vs prior year actuals — banks reject.
- **Repeat business** for the same client (multiple 15CBs in a month) is high-volume, low-fee, manual.

### AI AUTOMATION POTENTIAL
- 15CB steps 1-7: **Partial → Full.** DTAA rule engine + LLM for nature-of-payment classification.
- 15CB steps 8: Not feasible.
- Net worth: Step 2 partial (OCR of bank statements). Step 5 not feasible.
- CMA steps 1, 2, 4, 5, 6: **Partial → Full.** Model + assumptions plug-in.
- CMA step 8: Not feasible.

### CANDIDATE AI WEDGES
1. **15CB rule engine** — input: invoice + counterparty country + TRC; output: applicable section + rate + DTAA article + 15CB draft. Reduces 2-5 hrs to 15 min.
2. **TRC + 10F validator** — checks Form 10F completeness, TRC validity period; chases foreign party for missing.
3. **Net worth statement auto-compiler** — ingests bank statements + Demat statements + property docs via OCR; produces draft NW with cited evidence.
4. **CMA projections generator** — from 3-year audited financials + bank's preferred template, generates baseline projections; senior adjusts assumptions.
5. **MPBF + ratio calculator** — auto-compute under Tandon / Nayak / industry-specific methods; flag covenant breaches.

### TYPICAL FEE & WHERE MANAGER TIME GOES
- **15CB fee:** ₹2,500-₹10,000/cert (small firm); ₹15K+ mid-tier.
- **Net worth fee:** ₹2,500-₹15,000.
- **CMA fee:** ₹5,000-₹15,000 small loans; ₹50K-₹3L mid-loans; ₹3-25L large project finance.
- **Avg hours:** 2-50 hrs depending on type.
- **Manager time:** Mostly on judgement calls (DTAA, real-estate valuation, projection assumptions).

---

## CROSS-WORKFLOW ANALYSIS

### Pain steps appearing in 3+ workflows

| Pain step | Workflows it appears in | Current solutions | AI wedge potential |
|---|---|---|---|
| **Document collection from client** | All 12 (GST monthly, GST annual, e-invoice, TDS, ITR, Stat Audit, Tax Audit, ROC, TP, Scrutiny, IA, Certs) | WhatsApp + email + AnyDesk | Universal — agent that monitors client share drives + WhatsApp + email and auto-indexes |
| **Reconciliation across two data sources** | GST monthly (2B↔books), GST annual (3B↔audit), TDS (26AS↔books), ITR (AIS↔books), Stat Audit (TB↔ledger), Tax Audit (3CD↔books) | Excel VLOOKUP + ClearTax Reconcile + manual | Fuzzy-match reconciliation engine (multi-attribute, period-aware) as a horizontal capability |
| **Classification / coding judgement** (HSN, TDS section, 17(5) ITC ineligible, Clause 21 disallowable, Clause 44 vendor type, expense P&L head) | GST monthly, TDS, Tax Audit, Stat Audit, ITR, Internal Audit | Manual classification by article + senior | LLM with confidence scoring; learns firm-specific patterns over time |
| **Partner sign-off / DSC bottleneck** | All except Certs (where partner is light) | Manual queue, DSC physical token | Cannot fully automate but AI pre-review compresses the queue 50-70% |
| **Portal upload + JSON validation + retry** | GST, TDS, ITR, ROC, TP, 15CA/CB | Per-portal logins + emSigner + Java | RPA / agent that handles uploads, retries, captures errors |
| **Case-law / notification interpretation** | GST notices, ITR scrutiny, IA findings, Tax Audit positions | Taxmann, CCH, Taxsutra subscriptions | RAG over verified DBs (verified-citation guarantee per ITAT hallucination concern) |
| **Working-paper documentation per SA 230** | Stat Audit, Tax Audit, IA, GST 9C, TP study | Excel + Word, firm-specific templates | Audit-execution platform that captures evidence as a byproduct of doing the work |
| **Notification / circular monitoring** | All (especially GST changes, IT schema, MCA forms) | Email subscriptions, Twitter, Taxguru | Continuous monitor + impact-mapper per client portfolio |
| **Manager pre-review of article work** | All compliance workflows | Manual back-and-forth | AI pre-review that surfaces only items needing human judgement |
| **Client communication / nudge / status report** | All | WhatsApp + email | Conversational agent on client's preferred channel |

### Where existing tools already solve a step (don't waste your wedge here)

| Step | Solved by | Quality |
|---|---|---|
| GSTR-1 / 3B JSON generation from Tally export | ClearTax, Tally GST module, Cygnet, KDK | Good, mature |
| ITR JSON generation from computation | Winman, Computax, Genius | Good, mature |
| TRACES bulk Form 16/16A download | Genius TDS, Saral, Winman | OK |
| TDS FVU file generation | NSDL RPU + every CA software | Good, but UX bad |
| Form 26AS / AIS download via ERI | Winman, Computax | Good (Type-2 ERI access) |
| Tally → Excel data export | Tally itself | Brittle but workable |
| Project management / deadline tracking | QwikCA, Practive, ERPCA, Karbon | Adequate; not dominant |
| ROC form templates (AOC-4 / MGT-7) | KDK Spectrum, MCA21 itself | Adequate |
| Audit working papers (Big 4 / large mid) | CaseWare, MindBridge | Strong at top end |
| OCR of bank statements | DocuClipper, AI Accountant, Suvit | Improving but error-prone on regional banks |
| Document collection via WhatsApp | Suvit, AI Accountant, QwikCA | Early — usable but adoption fragmented |

### Where existing tools fail (or don't exist) — the whitespace

1. **2B-vs-books deep fuzzy match** with format-variant invoice numbers + supplier-name fuzzy match + period-boundary handling. ClearTax does the basic match; the *judgement layer* (decide accept/reject/pending and chase supplier) is manual.
2. **17(5) ineligible-ITC classification** at scale across thousands of purchase lines.
3. **Form 3CD Clause 44 expenditure breakdown** — every line classified by vendor GST status. Currently 6-30 hrs per audit; could be minutes.
4. **Faceless scrutiny notice response drafting with verified citations** — currently 20-200 hrs of partner-level skill per notice.
5. **Audit ledger scrutiny anomaly detection** — currently 16-60 hrs of mechanical article work per audit.
6. **MCA21 portal retry / queue automation** — currently CAs file at 9 pm to avoid load.
7. **Case-law / notification monitor mapped to client portfolio** — currently invisible labour ("just the job").
8. **Pre-review surface for partner sign-off queue** — currently every file waits for personal review; AI could surface only the 30% that need true partner judgement.
9. **WhatsApp-native client portal that ingests docs and auto-indexes** to the right compliance workflow.
10. **Working-paper auto-compiler (SA 230)** — captures evidence as byproduct of doing the work, not as a separate compliance step.

### The 10 most promising AI insertion points — ranked by (frequency × time-saved × fee-bearing value)

**Methodology of ranking:**
- **Frequency** = monthly recurring (top score) > quarterly > annual > event-based.
- **Time-saved** per occurrence per client (hours).
- **Fee value** = either bookable as separate service or unlocks higher leverage on existing fee.

| Rank | Wedge | Workflow | Freq | Hrs saved / occurrence | Reason for rank |
|---|---|---|---|---|---|
| **1** | **GSTR-2B fuzzy reconciliation + IMS auto-action agent** | GST Monthly | 12x/yr × every client | 4-10 hrs | THE canonical pain. Felt every month, every CA, every tier. Direct mapping to DEV.to case study of 3 FTEs at one Mumbai firm. With IMS hard-locking from Feb 2026 + Table 4 ITC hard-lock targeted July 2026, the pain is intensifying. |
| **2** | **Faceless scrutiny notice response drafter with verified citations** | Income Tax Scrutiny | Event but high-value | 20-150 hrs | Highest hourly value capture. 1 in 3 firms miss deadlines (gstnoticeai.com). Partner-level work. Hallucination risk requires verified-citation layer. |
| **3** | **Audit ledger scrutiny + voucher matching for stat/tax audit** | Stat Audit + Tax Audit | Annual × every audit client | 40-160 hrs | Replaces the article's bread-and-butter work. Compresses the leverage ceiling problem. Auditing is a higher-fee, multi-week engagement so AI value here is large. |
| **4** | **3CD Clause 44 expenditure-by-vendor-GST-status auto-classifier** | Tax Audit | Annual × every audited entity | 6-30 hrs | Specific to the tax audit deadline. Saves a "excruciating" clause. High concentrated relief in Sept crunch. |
| **5** | **TDS section auto-classifier + 26AS/AIS reconciliation** | TDS Monthly + ITR Annual | 12x + 1x/yr | 3-8 hrs/month | Same fuzzy-match engine as GSTR-2B but applied to TDS. Reuses engine. Removes article work + reduces "Processed with Defaults" rework. |
| **6** | **GSTR-9 / 9C reconciler (books ↔ 12-month GSTR-1 ↔ 12-month 2B ↔ audited financials)** | GST Annual | 1x/yr × every reg | 30-100 hrs | Year-end mega-recon. Auditor's books finalised late → 4-8 week crunch. Tool that auto-reconciles 3-way + drafts 9C narrative is high-impact. |
| **7** | **Verified-citation LLM for case-law / circular / notification research** | Scrutiny + Audit + Tax positions | Continuous | 2-8 hrs/instance | Horizontal cross-workflow capability. Addresses ITAT-hallucination concern with verified-RAG. Used by managers + partners across notice replies, audit positions, opinion letters. |
| **8** | **CARO 2020 clause auto-filler + IFC test-of-controls 100% population tester** | Stat Audit + Internal Audit | Annual + quarterly | 16-50 hrs | Audit-specific. Replaces sample testing with full-population testing. Differentiates AI-native audit firm from Excel-bound competitor. |
| **9** | **Annual ROC filing calendar + AOC-4 / MGT-7 auto-drafter** | ROC | Annual × every company | 8-25 hrs | Less glamorous but huge volume across the 16+ ROC forms. MCA21 portal retry built in handles the "9 pm filing" pain. |
| **10** | **WhatsApp-native client doc collection + auto-indexer** | All 12 (horizontal) | Continuous | 5-15 hrs/client/month aggregate | Underpins everything else. If no docs, no work. Felt by every solo/small firm. Underlies the "document chasing" universal pain. |

---

## Notes for the founder

- **Where to start (positioning):** The single highest-leverage MVP is **Wedge #1 (2B + IMS) plus Wedge #5 (TDS/26AS reco)** because they share the same fuzzy-match engine and the same client base, run on the highest-frequency cycle (monthly), and address the most directly admitted pain. Customers will pay for monthly relief because monthly relief compounds.
- **Where Big 4 will eat you alive:** TP (high-end), Big-listed audit, complex notice litigation. Don't go upmarket on day 1.
- **Where you'll meet ClearTax head-on:** GST module-level features. Win by going *deeper* (judgement layer — accept/reject/chase) rather than wider (format conversion).
- **Where you'll meet Tally head-on:** Books data. Don't try to replace Tally — integrate as a *layer above* via TDL + XML over port 9000.
- **Where you'll meet Winman / Computax head-on:** ITR computation and bulk filing. They're entrenched and good enough; don't compete here — focus on what comes *before* (reconciliation, classification) and *after* (notice handling, working-paper docs).
- **The DSC + partner sign-off is the natural boundary for "automation" — AI prep, human sign.** Build assuming the partner stays in the loop on every attest engagement; the win is compressing the queue and shortening review time, not eliminating sign-off.
- **The 60-tax-audit cap per CA** is a hard ICAI rule. Tools that let one CA handle the prep of more audits (since the sign cap is per partner, not per firm) increase firm leverage.

---

## Sources & references (compliance workflows)

- ClearTax, *Invoice Management System (IMS) under GST* — https://cleartax.in/s/invoice-management-system-ims-under-gst
- ClearTax, *Hard-Locking of Auto-Populated in GSTR-3B* — https://cleartax.in/s/hard-locking-in-gstr-3b
- ClearTax, *Is IMS Mandatory Under GST?* — https://cleartax.in/s/is-ims-mandatory-in-gst
- ClearTaxAdvisors, *GSTR-3B Hard Locking + IMS: The New GST Compliance Reality (2025-26)* — https://cleartaxadvisors.in/gstr-3b-hard-locking-ims-guide/
- CAclubindia, CA Kavish Chawla, *The Portal Will Block You — Survival Guide to ITC Reconciliation after GSTR-3B Hard-Locking* — https://www.caclubindia.com/articles/the-portal-will-block-you-a-ca-s-survival-guide-to-itc-reconciliation-after-gstr-3b-hard-locking-54858.asp
- CAclubindia, *GSTN Rolls Out New IMS Tab to Track Rejected Notes for GSTR-3B (Feb 2026)* — https://www.caclubindia.com/news/gstn-rolls-out-new-ims-tab-to-track-rejected-notes-for-gstr-3b-26223.asp
- ClearTax, *What is e-Invoicing Under GST? Applicability, Limit, Rules, Process* — https://cleartax.in/s/e-invoicing-gst
- Binary Semantics, *30-Day E-Invoice Generation Time Limit: Latest Update* — https://www.binarysemantics.com/blogs/understanding-the-e-invoice-generation-time-limit-basic-rules-and-latest-updates/
- AI Accountant, *GSTR-9 Preparation Checklist* — https://www.aiaccountant.com/blog/gstr-9-preparation-checklist
- AccountX, *GSTR-9 & 9C Reconciliation Checklist for GST Audits* — https://accountx.in/gstr-9-9c-reconciliation-checklist/
- ICAI, *Technical Guide on GST Reconciliation Statement (Form GSTR-9C)* — https://d23z1tp9il9etb.cloudfront.net/download/pdf25/TG%20on%20Annual%20Reco%20Statement-%20Form%20GSTR%209C.pdf
- Patron Accounting, *CA-Assisted TDS Filing 24Q & Form 16* — https://www.patronaccounting.com/blog/tds-return-filing-24q-form-16-ca-assisted-process
- TaxFetch, *TRACES 2.0 Portal: File TDS Returns Online 2026 Guide* — https://taxfetchindia.com/blog/taxation-time/traces-2-portal-file-tds-returns-online
- Unpaper, *How to Handle Notices for Mismatch in Form 26AS and AIS* — https://unpaper.com/blog/how-to-handle-notices-for-mismatch-in-form-26as-and-ais-(annual-information-statement)
- ClearTax, *Resolving Mismatches Between the TDS Statement and Form 26AS* — https://cleartax.in/s/tds-mismatch-rectification
- Patron Accounting, *ITR-6 Filing Guide for Companies 2026* — https://www.patronaccounting.com/blog/itr-6-filing
- SAG Infotech, *Step-by-Step Guide to File ITR 6 Online AY 2026-27* — https://blog.saginfotech.com/file-itr-6-online
- CleartTax, *Tax Audit Forms 3CA / 3CB / 3CD / 3CE* — https://cleartax.in/s/tax-audit-form-3ca-3cb-3cd-3ce
- CleartTax, *Form 3CD: Applicability, Format and Key Tax Audit Clauses* — https://cleartax.in/s/form-3cd
- ICAI, *Guidance Note on Tax Audit under Section 44AB (Revised 2025)* — https://a2ztaxcorp.net/wp-content/uploads/2025/07/Guidance-Note-on-Tax-Audit-under-Section-44AB-of-the-Income-tax-Act-1961-Revised-2025.pdf
- Taxmann, *Tax Audit Checklist on Clauses 41 to 44 of Form 3CD* — https://www.taxmann.com/post/blog/tax-audit-checklist-on-clauses-41-to-44-of-form-3cd-under-the-income-tax-act
- IndiaFilings, *Analyzing Clause 44 of Form 3CD* — https://www.indiafilings.com/learn/analyzing-clause-44-of-form-3cd/
- CA Tushar Makkar, *How to Do Statutory Audit — Step-by-Step Process* — https://www.catusharmakkar.com/blog/how-to-do-statutory-audit
- ICAI, *SA 230 Audit Documentation* — http://kb.icai.org/pdfs/PDFFile5b3b4ec0607a15.03386623.pdf
- ICAI, *SA 220 Quality Control for an Audit* — https://kb.icai.org/pdfs/PDFFile5b3b4c2a41d107.18791569.pdf
- ICAI, *SA 700 (Revised) Forming an Opinion and Reporting on Financial Statements* — https://kb.icai.org/pdfs/PDFFile5b3b47cc680bc3.58124333.pdf
- ClearlyComply, *ROC Annual Filing for Private Limited Company — AOC-4, MGT-7 & Complete Guide 2026* — https://clearlycomply.org/blog/roc-annual-filing-private-limited-company/
- SAG Infotech, *All Due Dates of ROC Annual Return Filing FY 2025-26* — https://blog.saginfotech.com/due-dates-filing-roc-annual-return
- IndiaFilings, *Transfer Pricing Compliance for FY 2024-25 in India* — https://www.indiafilings.com/learn/transfer-pricing-compliance-chart
- ClearTax, *Form 3CEAA — Due Date, Applicability, Filing* — https://cleartax.in/s/form-3ceaa
- ICMAI, *Compliance Management under Indian Transfer Pricing* — https://icmai.in/TaxationPortal/Publication/Practical_Guide_Booklets/Compliance_Management.pdf
- Patron Accounting, *Faceless Assessment India: NFAC Guide* — https://www.patronaccounting.com/blog/faceless-assessment-in-india-complete-guide-to-nfac-and-how-to-respond
- KMGCO LLP, *Section 144B of the Income Tax Act: Faceless Assessment* — https://kmgcollp.com/section-144b-of-income-tax-act/
- TaxGuru, *How to Handle Faceless Income Tax Scrutiny Assessments* — https://taxguru.in/income-tax/handle-faceless-income-tax-scrutiny-assessments.html
- DisyTax, *Section 143(2) Scrutiny Assessment Notice* — https://disytax.com/section-143-2-scrutiny-assessment-notice/
- PKC India, *Internal Audit for Public Companies in India* — https://www.pkcindia.com/blogs/internal-audit-for-public-companies/
- IndiaFilings, *Internal Audit Applicability Under Companies Act 2013* — https://www.indiafilings.com/learn/internal-audit-applicability
- CAclubindia, *Form 15CA & CB — CA Certificate, Foreign Remittance* — https://www.caclubindia.com/articles/form-15ca-cb-ca-certificate-foreign-remittance-45387.asp
- Income Tax Department, *Form 15CA FAQs* — https://www.incometax.gov.in/iec/foportal/help/statutory-forms/popular-forms/form-15ca-faq
- FinLine, *CMA Report for Bank Loans — Simple Format and Steps* — https://www.finline.in/resource/how-to-prepare-a-cma-report-for-bank-loan/
- KMGCO LLP, *Net Worth Certificate for Visa Application* — https://kmgcollp.com/net-worth-certificate-for-visa-application/
- nabsai.com, *Complete Guide to Replying to GST Notices in India 2025* — https://nabsai.com/blog/complete-guide-to-replying-to-gst-notices-in-india/

(Also draws on `01-operations-workflows.md`, `02-software-stack.md`, `04-pain-points.md`, and `05-economics-billing.md` for hierarchy, tooling, verbatim pain quotes, and fee benchmarks already compiled in this research stream.)
