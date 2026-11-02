# Acceptance report

Tested on 2 November 2026 in headless Chromium using the real page and browser controls. All 10 Section 11 checks pass. Safari and Edge were not available for direct validation; no claim of direct testing in those browsers is made.

| Section 11 check | Result | Evidence |
| --- | --- | --- |
| 1. Main-line costs and completion | PASS | All eight choices exercised; seven cost one day, G2a costs zero. |
| 2. Dead-end cost, damage and retry | PASS | All 16 dead ends exercised; each costs one day, applies its specified damage, retains the option order and returns to the same decision. |
| 3. Stalin 3 die thresholds and effect order | PASS | J2a, U1a and U2a tested at rolls 3 and 4. Roll 3 shows X1 and spends an extra day; roll 4 succeeds. Track effects occur after the roll. |
| 4. Track bounds | PASS | Negative changes at 1 and positive changes at 5 remain clamped. |
| 5. UN lock and toast | PASS | Each leader independently tested at 1. X2 costs nothing; a toast to 2 permits opening the UN. |
| 6. Exhaustion and unresolved ending | PASS | Unpayable base/extra cost and zero-day next decision show X3. Ending identifies unresolved decisions. |
| 7. Shuffle stability | PASS | Restart changes option ordering; dead-end retries retain it. |
| 8. Exact Undo | PASS | Full state equality checked after undoing a roll and a continuation: days, tracks, log, card and order restored. |
| 9. Facilitator hidden by default | PASS | Hidden until F; F hides it again. |
| 10. Layout and keyboard | PASS | All 15 screen states, notes on/off, at 375, 1280 and 1920px: no horizontal overflow. Entire successful game, history and debrief completed with keyboard. Body text is 20px at 1280px. |

## Full playthroughs

**Successful, keyboard only:** Japan → UN → Germany → Poland, choosing each agreement and entering successful physical rolls. All eight decisions completed; the completion line appears. Each historical row reveals separately, followed by the closing paragraph and debrief.

**Requested adverse route:** Japan J1b (dead end) → J1a → J2a with roll 3 (X1; extra day paid) → Germany G1c twice → G1a → G2a. Stalin is now 1 and one day remains. Attempt UN: X2, no day charged. Toast Stalin to 2: the final day is spent and X3 appears. Ending lists Poland and UN unresolved.

## Additional checks

- Animated roll finishes with a result in 1–6; Undo during animation cancels its delayed result.
- Refresh restores the exact saved game state.
- Gameplay works when every localStorage access throws.
- Print media exposes the group's outcome and decision log.
- Reduced-motion preference is supported by animation CSS and the die timer.
- No JavaScript errors or external HTTP requests during the suite.
- 8 questions, 24 option cards, 3 general cards, 10 reactions, 4 history rows and 10 debrief questions checked against the supplied content data.
- Desktop and phone screenshots visually inspected.

The harness uses isolated state fixtures for rule boundaries and real UI interactions from the title screen for both full playthroughs. It does not represent an in-person seminar or direct Safari/Edge testing.
