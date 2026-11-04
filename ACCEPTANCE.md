# Redesign acceptance report

Validated on 4 November 2026 in headless Chromium. **37 checks passed.** See `acceptance-results.json` and `tests/acceptance.cjs` for the recorded results and repeatable suite. Safari and Edge have not been directly tested.

This report covers the approved redesign. It supersedes the original forced-dead-end, automatic extra-day and historical-main-line scoring assumptions. The original game and its earlier reports remain at `pre-party-redesign`.

| Behaviour | Result | Evidence |
| --- | --- | --- |
| Tentative proposal and reactions | PASS | All 24 options send to two mild reaction bubbles. The selection offers only Send; the next page offers Stand by or Reconsider. Neither tentative send nor reconsider changes game resources. |
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
| Responsive layouts | PASS | All 17 screens at 375, 1280 and 1920 pixels, with facilitator notes on/off, have no horizontal overflow. |
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

## Revised reaction flow

The latest interaction supersedes the inline adviser-question panel. Selecting a proposal shows only Send proposal. Sending opens a separate Read the room page with two restrained, dramatised reactions from leaders or a fictional adviser. No scores, numerical relationship effects, final acceptance or final refusal appear at this stage. Explicit reflection questions are optional facilitator notes only.

The four flow tests cover all 24 reaction pairs, absence of pre-send reconsideration, no resource changes until Stand by this proposal, no double charge, reconsideration and Escape, Undo, save/refresh and withheld score information. The full suite has 22 passing checks. Desktop and mobile reaction screens were visually inspected. Whether reactions are appropriately subtle for a classroom remains a facilitation judgment, not something the automated checks establish.

## Card-table visual refresh

Added original exaggerated SVG portraits, cosmetic idle/head and blink animation, felt table, playing-card issue artwork, tactile controls and refreshed HUD styling. Two added tests verify all illustrations are self-contained, preview portraits are identical across relationship values, and reduced-motion preferences disable portrait animation. All 24 checks pass. Desktop title, table and reaction screenshots and a 375px reaction screen were visually inspected. All GAME_DATA content and scoring are byte-equivalent as parsed JSON to the preceding version. No gameplay or historical-content changes were made.

## Theatrical conference room

Preserved the preceding card-table design in the pushed `pre-theatrical-table` tag at `172e38e`. Negotiations now share a persistent room with larger leader portraits, warm lamps, cool shadows, a felt table, a desktop sidebar and Roosevelt’s place in the foreground. Sent proposals slide onto the table, settled outcomes receive a stamp, and final scores enter in sequence. Reduced-motion preferences disable these animations. Reactions remain restrained and appear beside their speakers.

Two additional checks verify room continuity, speaker-attached reaction bubbles, unchanged resources on tentative send, and desktop/mobile HUD placement. **All 26 checks pass**, including both complete playthroughs, adverse paths, saving, keyboard interaction and all 17 screens at three viewport widths. Desktop table and reaction screenshots and the 375px reaction layout were visually inspected. Parsed GAME_DATA is identical to the preserved version: this update changes presentation, not decisions, scoring or historical content.

## Pre-send discussion and guided reading

The latest flow adds a discussion panel before Send: two proposal-specific questions, decision-level guidance, and a named section reference to the supplied case study. All 24 proposals were checked for their matching questions and guide, absence of score/effect spoilers, and unchanged resources before commitment. Two added tests cover switching, Undo, collapse, keyboard selection and refresh, plus numbered briefing rules and an optional scoring rubric. **All 28 checks pass in Chromium**, including the existing full playthroughs and responsive checks. Desktop proposal/briefing and mobile discussion screenshots were visually reviewed.

The previous presentation is preserved at `pre-discussion-guides` (`ea079ee`). Existing GAME_DATA fields are unchanged; only discussionGuides was added. The case study’s wording is preserved apart from Markdown formatting. CASE_STUDY_ALIGNMENT.md maps all eight decisions and separates additional option context from the supplied narrative. This checks coverage, not the accuracy of its unsupplied bibliography.

## Integrated hand swipe

The approved animation is now part of the full game, preserving the existing save key and all GAME_DATA fields. Middle selections place two hands on adjacent cards; end selections use one forearm. The chosen card stays in place until the other cards clear. Issue opening is recorded exactly once after the transition and costs no game time. Escape or U cancels before opening, and reloads cannot resume a stale transition. Reduced motion, blocked UN, exhaustion and missing animation support take the immediate path.

Four additional acceptance checks cover neighbouring-card contact, single-arm versus two-hand motion, repeated selection, cancellation, refresh, fallback and live phone/tablet completion. **All 32 checks pass in Chromium.** The full suite was followed by a focused rerun of the four animation checks and runtime check after correcting the cancellation test to press Escape during, rather than after awaiting, the asynchronous animation. No game code changed between these runs. The preceding full game is preserved as `pre-integrated-swipe` (`80d88cd`).

## Visible 3D dice

The digital die now enters from below/right, turns twice and slows to rest on the table, settles on its actual value and waits for Continue. The cream/gold die and dark green pips use the existing palette. All 37 checks pass, including six-face orientation/pip checks, the existing game routes, settled-result save/refresh, exact Undo, unsupported-animation fallback and phone overflow. The settled result cannot be rerolled. Physical entry retains its direct resolution. After adjusting result-page scrolling, a focused browser check also confirmed that the die and Continue are both visible at 1280 × 800, 1366 × 768 and 375 × 812.

## Seated dialogue

Counteroffers and historical agreement reactions use speech bubbles beside the seated speaker. Duplicate table portraits and dialogue boxes are removed. Desktop and phone previews were inspected; all eight counteroffer speakers and agreement dialogue passed browser checks at both widths.

## Two-page introduction

The mission and five concise play rules are separate pages using a consistent cream and green palette. Scoring details remain optional. Navigation, Back, refresh on the rules page, unchanged starting resources, keyboard playthrough and narrow-screen layout are covered by browser checks.

## Local soundtrack

The full Dark Times track loops locally at 20% initial volume. Browser checks cover interaction-triggered playback, uninterrupted navigation, saved volume and mute preferences, home-page stop/rewind and missing-file fallback. A separate check confirmed playback from file:// and usable phone controls. All 37 checks pass.
