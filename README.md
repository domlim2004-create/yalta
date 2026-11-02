# Yalta 1945: The Roosevelt Game

An offline negotiation game for UTC2107, NUS Tembusu College. A group of 4–5 players shares one Roosevelt; allow about 30 minutes.

## Play

Open `index.html` in a current browser. The file contains all HTML, styling, JavaScript and content. No installation, build, server, fonts, accounts or network access is required. Copy just this file to the facilitator's laptop.

If your managed browser blocks local files, serve the folder instead:

```sh
cd yalta
python3 -m http.server 8000 --bind 127.0.0.1
```

Open the local server in your browser. The game itself makes no external requests.

- **1 / 2 / 3:** choose the corresponding decision option.
- **Enter / Space:** advance the current screen. Use Tab and Enter/Space for issue cards, toast targets, physical die results and other buttons.
- **F:** toggle facilitator notes (hidden by default).
- **U:** undo the most recent game action, including a roll.
- **Use physical die:** enter a real die result using buttons 1–6. Off by default.
- **Restart:** confirm a new game with newly shuffled options. Undo can restore the previous game.

Progress and its Undo history are saved locally when browser storage is available. Storage errors do not prevent play. Facilitator visibility is not persisted. For a fresh seminar session, use Restart and leave facilitator notes off until needed.

At the debrief, **Print group summary** prints the questions, final outcome and complete choice/card/roll log.

## Showcase presentation

The interface is a wartime briefing room: a presidential briefing, four issue dossiers, sealed telegrams and a historical record. It is designed for one shared laptop. At 1366 × 768, all four issue cards and all three proposals on each decision screen fit within the viewport with facilitator notes off. Longer briefings, historical comparisons and notes can be scrolled.

Days, relationships and completed decisions remain visible during negotiations. The opening and briefing hide that panel to keep attention on the introduction. The decision log appears after the first recorded action. Facilitator notes include a reminder that everyone viewing the screen can see them.

Choosing a dossier plays a three-stage gesture based on `ArmMotion.mp4`: a nearly upright forearm pivots while sliding sideways to fan the opposite column aside, returns and moves vertically while turning to brush the other file in the chosen column down (or up when choosing a bottom-row file), then returns to grip and lift the selected dossier. The selected file stays in place until the pickup. The gesture mirrors for right-column choices. Choosing a proposal similarly clears the other options. Opening a telegram breaks the seal, lifts the flap and slides out the letter. The three-stage sweep and pickup take about 3.3 seconds; the envelope uses its own adjustable extraction/fade timings, and proposal selection takes about half a second. The paper lifts in front of the pocket and flap during extraction. Repeated input is ignored while it runs. Press **U** to undo and cancel the animation. System reduced-motion preferences skip these effects. Refresh retains the committed action without replaying its animation.

The title fades onto the desk on first opening. Begin and Continue turn the current sheet away and slide the next page into place, with brief staggered entrances for rules, dossiers and decision options. Individual historical rows reveal separately. These navigation transitions take around half a second and follow the same reduced-motion and Undo behaviour.

The presentation rebuild preserves the original content, rules, option shuffling and saved-game format. Inline SVG illustrations, CSS and system fonts require no external assets.

## Content and rules

Edit `GAME_DATA`, at the beginning of the inline script, to change the supplied historical content. Historical text and dramatised reactions are preserved verbatim from the build prompt. Every reaction carries the required dramatisation label.

An issue must be completed in order. A failed die roll is resolved against Stalin's score before the card's relationship changes. X1 charges the extra day before applying the agreement. When a cost cannot be paid, X3 ends play without completing that agreement. Zero days prevents starting another decision, including G2 even though its successful option costs zero. Completing the eighth decision takes priority over the zero-day check. UN locking is checked when opening the issue; it does not eject a group already negotiating it.

## Validation

See `ACCEPTANCE.md` and the recorded `acceptance-results.json`. The optional test harness is separate from the standalone game and needs Node.js, Playwright and Chromium:

```sh
node tests/acceptance.cjs
```

Set `CHROMIUM_PATH` if Chromium is not at `/usr/bin/chromium`. The harness starts and closes its own temporary local HTTP server. It runs rule boundary fixtures and full UI playthroughs, including a keyboard-only complete game and the requested adverse route. It also runs a complete game directly through `file://`, verifies saved refresh and print-to-PDF, and checks layouts, storage denial and absence of external requests. It writes results to `acceptance-results.json` and screenshots and a sample summary PDF to `/tmp`.

Playwright and Chromium are development-only tools; visitors need only a browser. If Playwright is installed outside the checkout, set `NODE_PATH` to its containing `node_modules` directory when running the harness.

## Publish with GitHub Pages

In this repository's **Settings → Pages**, set **Source** to **Deploy from a branch**, select **main** and **/ (root)**, then click **Save**. GitHub will show the published site URL when deployment finishes. The expected address is `https://domlim2004-create.github.io/yalta/`.

The root `.nojekyll` file tells Pages to serve the standalone game directly. Subsequent pushes to `main` update the site once branch publishing is enabled.
