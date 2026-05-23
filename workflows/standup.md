# Standup workflow (team-initiated)

Founders initiate standup themselves — no scheduler. Decision 2026-05-23.

## Triggers

Any of these from a founder in a Claude Code session:
- `standup` or `/standup` — morning standup
- `eod` or `end of day` — end-of-day check
- `retro` — weekly Sunday retro
- Or Claude proactively suggests it: when a session opens and today's `standup/YYYY-MM-DD.md` is missing.

## Morning standup

1. Compute today's date in IST. Check if `standup/YYYY-MM-DD.md` exists. If yes, ask whether to update it or treat as already done. If no, continue.
2. Read **yesterday's** standup file (if present). Note what each founder committed to.
3. Read any new extraction files in `Imp-Meet-Transcripts/` since yesterday's standup. Pull patterns, hypothesis updates, follow-up actions.
4. Copy `standup/_template.md` to `standup/YYYY-MM-DD.md`. Replace `YYYY-MM-DD` placeholder.
5. Ask the founder at the keyboard for (for each of Krishna, Piush, Dhruv):
   - Yesterday's shipped output (verifiable artifact, not effort)
   - Today's commitment (ONE specific thing, EOD-verifiable)
   - Outreach numbers since last standup: India sent / US sent / replies / booked / completed
   - Any blockers needing the team's input
6. Push back on vague commitments. "Work on outreach" is not a commit. "Send 15 US LinkedIn DMs to firm owners by 6pm IST" is.
7. Fill the standup file. Fill the "Central intelligence flags" section with patterns + follow-ups from step 3.
8. Update `memory/phase_metrics_may_2026.md` running count (cumulative owner conversations toward weekly target of 9).
9. End with a one-line summary: "Today's three commitments. Week tally so far. Next forcing question."

## End-of-day check

1. Open today's `standup/YYYY-MM-DD.md`. If missing, ask whether to do morning standup retroactively or skip to EOD.
2. Ask, per founder: what shipped today? If commitment didn't ship, why?
3. Fill the EOD section of today's file.
4. Update outreach numbers if changed.
5. Surface variance to the next morning's standup ("Central intelligence flags").

## Weekly Sunday retro

1. Read all standup files from the past 7 days.
2. Read all extraction files from the past 7 days.
3. Produce in `standup/retro-YYYY-WW.md`:
   - Total owner conversations this week vs. target
   - Conversion funnel (outreach sent → replies → booked → completed)
   - Per-founder shipped output count
   - Hypothesis changes (what we learned, what got contradicted, what got confirmed)
   - Next week's metric target and per-founder commitments
4. Update `memory/phase_metrics_may_2026.md` weekly target for the coming week.

## Proactive behavior between standups

- When a session opens and today's standup is missing, prompt.
- When a transcript lands without an extraction file, run extraction unprompted.
- When an outreach reply lands, suggest a draft response.
- When week-to-date numbers drift more than 30% below pace for the weekly target, surface it explicitly in the next standup.
