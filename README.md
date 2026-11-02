# Yalta 1945: The Roosevelt Game

An offline negotiation game for UTC2107, NUS Tembusu College. A group of 4–5 players shares one Roosevelt; allow about 30 minutes.

## Play

Open `index.html` in a current browser. The file contains all HTML, styling, JavaScript and content. No installation, build, server, fonts, accounts or network access is required. Copy just this file to the facilitator's laptop.

If your managed browser blocks local files, serve the folder instead:

```sh
cd /workspace/yalta
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

## Content and rules

Edit `GAME_DATA`, at the beginning of the inline script, to change the supplied historical content. Historical text and dramatised reactions are preserved verbatim from the build prompt. Every reaction carries the required dramatisation label.

An issue must be completed in order. A failed die roll is resolved against Stalin's score before the card's relationship changes. X1 charges the extra day before applying the agreement. When a cost cannot be paid, X3 ends play without completing that agreement. Zero days prevents starting another decision, including G2 even though its successful option costs zero. Completing the eighth decision takes priority over the zero-day check. UN locking is checked when opening the issue; it does not eject a group already negotiating it.

## Validation

See `ACCEPTANCE.md` and the recorded `acceptance-results.json`. The optional test harness is separate from the standalone game and needs Node.js, Playwright and Chromium:

```sh
node tests/acceptance.cjs
```

Set `CHROMIUM_PATH` if Chromium is not at `/usr/bin/chromium`. The harness starts and closes its own temporary local HTTP server. It runs rule boundary fixtures and full UI playthroughs, including a keyboard-only complete game and the requested adverse route. It also verifies layouts, storage denial, refresh, print visibility and absence of external requests.

This cloud environment already has the test tools installed. Use the existing checkout; each cloud task is isolated and needs no additional Git worktree.

## Publish with GitHub Pages

In this repository's **Settings → Pages**, set **Source** to **Deploy from a branch**, select **main** and **/ (root)**, then click **Save**. GitHub will show the published site URL when deployment finishes. The expected address is `https://domlim2004-create.github.io/yalta/`.

The root `.nojekyll` file tells Pages to serve the standalone game directly. Subsequent pushes to `main` update the site once branch publishing is enabled.
