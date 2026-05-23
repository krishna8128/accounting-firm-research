# After-call extraction workflow

Run this immediately after any customer / discovery conversation. Goal: convert the call from ephemeral conversation into queryable structured signal that feeds the company brain.

Triggered automatically by Claude when a new transcript lands in `Imp-Meet-Transcripts/`. Do not wait to be asked. (See `memory/feedback_proactive_cofounder.md`.)

## Step 1 — capture raw transcript

Drop the raw transcript into:
```
Imp-Meet-Transcripts/YYYY-MM-DD-<firm-slug>-<participant-slug>.txt
```

Example: `2026-05-25-rajesh-singh-and-co-managing-partner.txt`.

If the source is audio/video, transcribe first (use `transcribe-youtube` skill for YouTube; Whisper for local audio).

## Step 2 — Claude extracts structured signal

Output saved to `Imp-Meet-Transcripts/<same-stem>-extraction.md`.

### Extraction schema (10 sections)

1. **Firm profile.** Size (revenue, headcount), tier (Big 4 / mid / small / sole prop), services mix, geography, age of firm, owner background.
2. **Problems mentioned, ranked by visible pain.** For each: exact words used, frequency of mention, emotional intensity (annoyance / resignation / frustration / urgency), current workaround, cost (time / money / lost business / owner sanity).
3. **AI experiments / tools they've tried.** What worked, what didn't, specific tool names.
4. **Buying signals.** Did they ask about pricing? Timeline? Offer to be a design partner? Introduce us to peers? Say "send me whatever you build"?
5. **Anti-buying signals.** "No budget for that." "Staff would never use it." "We tried something similar and it failed." Skepticism patterns.
6. **Contradictions to our current hypothesis.** What conflicts with `memory/product_wedge_candidates_may_2026.md`, `memory/india_labor_cost_hypothesis.md`, `memory/india_ca_firm_market_may_2026.md`? List each contradiction explicitly.
7. **Confirmations of our current hypothesis.** Same, but for supporting evidence.
8. **ICP signals.** Does this firm match our working ICP? If yes, why. If no, what's different.
9. **Follow-ups.** Who they offered to introduce. What they want us to send. Preferred contact method going forward.
10. **Quotes worth keeping.** 3–5 sentences in their exact words that capture the conversation. Use later in landing pages, pitches, team alignment.

After extraction, propose updates to relevant memory files. **Do not silently update.** List proposed changes; the team confirms.

## Step 3 — update phase metrics

- Increment `# owners talked to` in `memory/phase_metrics_may_2026.md` only if this was an owner (not a staff CA).
- Append to `outreach/log.md`: which outreach message led to this conversation, time-from-send to call.

## Step 4 — propose memory updates after every 3rd extraction

Scan accumulated extraction files for patterns:
- Same problem mentioned 3+ times across calls = real pattern; promote to project memory.
- Same anti-buying signal 3+ times = ICP narrowing.
- Contradictions accumulating against a stored hypothesis = candidate to retire that hypothesis.

## Step 5 — surface to next standup

Add to next morning's `standup/YYYY-MM-DD.md` under "Central intelligence flags":
- New patterns this call revealed.
- Hypothesis status changes.
- Concrete follow-up actions needed with named owner (e.g., "Krishna: send Rajesh the GST e-invoicing primer by EOD Tuesday").

## Convention: what counts as a "real" extraction

- Conversation length ≥ 15 min OR clear strategic intent expressed.
- Owner / partner level participant (not staff / article CA).
- Recorded with consent (or written notes if no recording).

Calls that don't meet this bar: still keep notes in `Imp-Meet-Transcripts/light/<filename>.md` for completeness but don't fire the full extraction.
