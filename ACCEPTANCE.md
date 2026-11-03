# Redesign acceptance report

Validated on 4 November 2026 in headless Chromium. **19 checks passed.** See `acceptance-results.json` and `tests/acceptance.cjs` for the recorded results and repeatable suite. Safari and Edge have not been directly tested.

This report covers the approved redesign. It supersedes the original forced-dead-end, automatic extra-day and historical-main-line scoring assumptions. The original game and its earlier reports remain at `pre-party-redesign`.

| Behaviour | Result | Evidence |
| --- | --- | --- |
| Reflection before commitment | PASS | All 24 options have two prompts; selecting/reconsidering spends no time, changes no relationships and retains option order. |
| Historical outcomes | PASS | All eight historical agreements resolve with their specified cost; G2a remains free. Each decision scores once. |
| Alternative negotiation branches | PASS | All 16 alternative proposals resolve through acceptance, further bargaining and walkaway: 48 branch fixtures. |
| Forward progression | PASS | Accepting a counteroffer advances to the next decision instead of forcing another guess. |
| Dice | PASS | Stalin 3 requires 4+. Roll 3 creates a counteroffer without automatic extra-day cost; agreement effects follow resolution. |
| Relationships | PASS | Goodwill reduces bargaining cost; tracks clamp to 1–5. |
| UN lock and repair | PASS | Each leader independently at 1 blocks entry for free; a toast to 2 permits entry. |
| Walkaway | PASS | Closes the issue, leaves its remaining decision unattempted and permits another priority; does not count as an agreement. |
| Deliberate deferral | PASS | Explicit confirmation; zero day cost; reversible. |
| Exhaustion | PASS | Free counteroffer resolution remains available at zero days; further unaffordable bargaining is disabled; new decisions cannot begin. |
| Hidden scores | PASS | Live result/log do not reveal point values or reasons. Ending reveals each settled score and rationale. |
| Undo | PASS | Exact state restoration after proposal send, roll, settlement and restart, including scored outcomes and logs. |
| Complete keyboard game | PASS | Japan → UN → Germany → Poland; eight agreements, one day remaining, 11 points; historical rows and ten debrief questions reached. Print-to-PDF exercised. |
| Adverse full playthrough | PASS | Alternative demand, further bargaining, Stalin at 1, blocked UN, repair toast, failed rolls, conditional settlements and exhaustion on final toast. |
| Responsive layouts | PASS | All 16 screens at 375, 1280 and 1920 pixels, with facilitator notes on/off, have no horizontal overflow. |
| Animated die | PASS | Actual timed roll resolves and Undo cancels a pending callback; reduced-motion rendering used throughout other fixtures. |
| Persistence and compatibility | PASS | Save/refresh round-trip; original-version save preserved in its separate key. |
| Unavailable storage | PASS | Gameplay with throwing storage accessor; corrupt save fallback. |
| Facilitator and runtime | PASS | Notes hidden by default and toggleable; no captured JavaScript errors or external requests. |

## Content integrity

Compared the redesign's historical history rows, introduction, closing paragraph, card texts, dramatised reactions, briefing and ten debrief questions against the preserved version. They are unchanged. Verified 48 new reflection prompts across 24 proposals. Counteroffers, alternative outcomes and scores are explicitly teaching simulations.

## Visual review and limits

Inspected desktop conference-table and mobile reflection screenshots. The interface uses inline SVG characters, speech bubbles, coloured issue cards and large controls; all assets remain in the single offline HTML file. Long discussions and outcome records scroll vertically.

Browser tests combine isolated boundary fixtures with full UI playthroughs. They verify implementation, not classroom engagement or the objective merit of the scoring rubric. The eight-day budget is an initial balance: the historical route leaves one spare day; bargaining consumes time unless the responding leader is warm. Classroom testing should assess pacing and whether the score explanations support useful discussion.

The score is hidden from normal play, not encrypted. No public deployment of this branch was performed.
