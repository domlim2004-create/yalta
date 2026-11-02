# Acceptance report

Validated on 3 November 2026 in headless Chromium after the briefing-room presentation rebuild. **All 31 automated checks pass.** Results are recorded in `acceptance-results.json`. The original 16 checks also passed before the rebuild.

Safari and Edge were not available for direct validation. These results do not represent an in-person showcase rehearsal.

## Rules and state

| Check | Result | Evidence |
| --- | --- | --- |
| Main-line costs and completion | PASS | All eight agreements exercised; seven cost one day, G2a costs zero. |
| Dead ends and retry | PASS | All 16 dead ends cost one day, apply their specified changes and return to the same decision without reshuffling. |
| Rolls and effect order | PASS | All three roll-dependent agreements checked at Stalin 3, with rolls 3 and 4. Every relationship score also checked on both sides of its threshold. Changes apply after resolution. |
| Relationship bounds | PASS | Tracks remain between 1 and 5. |
| UN lock and repair | PASS | Either leader at 1 blocks entry without cost; toasting to 2 permits entry. A relationship falling to 1 during UN talks does not eject the group. |
| Exhaustion and completion boundaries | PASS | Unpayable base or extra costs end play. An affordable final-day agreement completes. Completing all eight decisions at zero days receives the completed ending. Zero days prevents starting G2. |
| Toasts | PASS | Cancellation spends nothing; a relationship at 5 cannot be increased. Spending the final day is explained before confirmation. |
| Shuffle and Undo | PASS | Restart changes option order; retry preserves it. Undo restores exact state after rolls and continuations and cancels pending die animation. |
| Saving and storage denial | PASS | Refresh restores the saved state. Play continues when localStorage access throws. |
| Content preservation | PASS | A SHA-256 comparison confirms the complete historical content and rule data match the pre-rebuild version. All facilitator prompts and debrief questions render. |

## Complete playthroughs

- **Keyboard only:** Japan → UN → Germany → Poland, with successful physical-die entries. All eight decisions complete, followed by four separate historical reveals and the debrief.
- **Adverse route:** J1b → J1a → failed J2a roll → G1c twice → G1a → G2a → locked UN → final-day toast. X3 appears, with Poland and the UN unresolved.
- **Direct offline file:** A complete game opened through `file://`, followed by saved refresh, historical reveals, debrief and print-to-PDF. No external network requests or JavaScript errors occurred.

## Presentation and accessibility

- All 15 screen states, with facilitator notes on and off, checked at 375, 1280 and 1920 pixels without horizontal overflow.
- At 1366 × 768 with notes off, all four issue cards and all three proposals on each of the eight decision screens fit within the viewport. The opening button also fits.
- Body text remains 20px at a 1280px viewport. Long briefings and historical comparisons can scroll.
- Facilitator notes are hidden by default; F toggles them. An explicit note explains that everyone viewing the screen can see them.
- Keyboard-only navigation, physical-die entry and reduced-motion support checked.
- Laptop opening, table and decision layouts, notes, and phone layouts visually inspected.
- Print media hides game controls and shows debrief questions, final resources, issue status, completed decisions and the complete choice/card/roll log. Generated PDF text checked; the group record begins on a new page.

## Selection and envelope animations

Eight additional checks exercise motion with reduced motion disabled: dossier/proposal transitions commit once and retain keyboard focus, with a visible inline-SVG forearm and sleeve and exactly one chosen dossier during the folder sweep; envelope opening ignores repeated input, allows extraction to finish before the transition ends and lifts the extracted paper above both pocket and flap in a flat stacking context; Undo cancels every transition and restores the exact preceding state; reduced-motion preference skips or cancels effects; and refreshing mid-animation restores the committed state without replaying it. Mid-animation folder and envelope frames, the closed envelope and its phone layout were also visually inspected. The main rules suite uses reduced motion for deterministic interactions.

The three-stage motion is also checked at fixed timeline points for all four corners: two opposite-column files leave first, the remaining file is cleared vertically, and the selected dossier stays stationary until pickup. The elbow also travels sideways during the fan and vertically during the second sweep; both translations are asserted for all four corners. Undo restores the table from these intermediate poses. The fan, downward clear and pickup were visually compared with the supplied `ArmMotion.mp4`.

Opening/briefing and Continue transitions are checked with motion enabled, including staggered rules and dossiers, exact Undo, a separate historical-row reveal and no horizontal overflow during a phone-sized page transition. Initial title entrance is also visually inspected.

## Reproduce

Run `node tests/acceptance.cjs` with Playwright and Chromium available. Set `NODE_PATH` if Playwright is installed outside this checkout, and `CHROMIUM_PATH` if needed. The harness owns its temporary local server and writes the machine-readable report here. Screenshots and the sample summary PDF are written to `/tmp`.
