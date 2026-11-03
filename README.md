# Yalta 1945 · At the table

A single-file, offline discussion game for 4–5 students sharing one Roosevelt. This is the **party-style gameplay redesign**, developed on `redesign/party-style`.

## Preserved version

The original game is preserved on `main` and the annotated tag `pre-party-redesign`, at commit `450f623838b5ddecec7c2e1d5d985914d9924afc`. This branch does not change that website or its publishing settings. Switching branches in GitHub shows the alternative files; it does not automatically create a second live website.

## Play

Open `index.html` in a browser. Everything is inline: historical text, simulation content, character SVG illustrations, CSS and vanilla JavaScript. No build, accounts, external fonts or requests.

For a browser that blocks local files:

```sh
cd /workspace/yalta
python3 -m http.server 8000 --bind 127.0.0.1
```

Open the local server in your browser. Use the existing checkout; a separate Git worktree is unnecessary.

## What's different

- A green-felt card table, cream playing-card dossiers, chunky controls and exaggerated original character illustrations. Churchill has a bowler and bow tie, Stalin a broad moustache and uniform, Roosevelt round glasses. Gentle blinking and idle motion respect reduced-motion preferences.
- Selecting a proposal reveals only Send proposal. Sending opens a separate page with two restrained reactions from leaders or a fictional adviser. Stand by the proposal to commit, or Reconsider for free. Explicit reflection questions are reserved for optional facilitator notes.
- Historical agreements and simulated counteroffers replace compulsory dead-end retries.
- Failed rolls create choices, not an automatic lost day.
- Visible relationships affect rolls, access to the UN and the cost of further bargaining.
- Each settled decision receives one hidden integer score, −1 to +2. The ending reveals its rationale. Scores are pedagogical judgments, not historical grades.
- Players may deliberately leave an issue unresolved, preserving time for other priorities.
- Original history and dramatised reactions are preserved. Alternative settlements are labelled as teaching simulations.

## Controls and saves

**1–3** select or switch a proposal before sending. **Tab** moves focus and **Enter/Space** activates buttons. **Enter/Space** on the page advances Continue screens, but does not automatically send or confirm a proposal. **Escape** on the reaction page reconsiders and returns focus to the option. **F** toggles facilitator notes. **U** undoes the last game action, including tentative sends, confirmations, rolls and settlements. Use **Physical die** to enter a real result.

The redesign uses `yalta-party-v2` localStorage. It leaves the original `yalta-1945-v1` save untouched and starts a separate game. Save failures never block play. Restart is confirmed and reversible with Undo. No sound is used. Reduced-motion preferences suppress transitions and shorten the die animation.

The scores are hidden in the normal interface until the ending, not protected secrets: this is an offline educational game and its source contains the rubric.

## Guides

- [Game guide](GAME_GUIDE.md)
- [Terms and scoring](GAME_TERMS.md)
- [Detailed walkthrough](GAME_WALKTHROUGH.md)
- [Facilitator scoring reference — spoilers](SCORING.md)
- [Acceptance report](ACCEPTANCE.md)

## Validation

The optional test harness requires Node.js, Playwright and Chromium. Visitors only need a browser.

```sh
node tests/acceptance.cjs
```

Set `CHROMIUM_PATH` if Chromium is not `/usr/bin/chromium`, and `NODE_PATH` if Playwright is installed outside Node's normal module lookup. The suite starts its own temporary HTTP server, checks all proposal branches and full playthroughs, then closes the server. Results are saved to `acceptance-results.json`; screenshots and a sample PDF go to `/tmp`.

The original Section 11 acceptance rules are superseded where the approved redesign deliberately changes dead ends, dice penalties and completion. The new report names the behaviours tested rather than claiming the old rules still apply.

## Visual direction

The redesign uses an original arcade card-table aesthetic: warm paper, deep green felt, purple and gold accents, thick outlines, offset shadows and fast tactile button feedback. Artwork is inline SVG, with no copied game assets, remote fonts or downloads. The style draws on approachable party-game presentation and card-game readability without adding gambling mechanics. No sound or flashing effects are used.

Reaction portraits use the same neutral pose for a speaker across proposals and relationship values; their idle motion is cosmetic. Hidden scores and future acceptance cannot be inferred from a new approval/disapproval animation. Relationships remain explicit in the HUD. Longer dialogue and records scroll vertically on smaller displays.
