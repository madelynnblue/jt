# Jam Timer

Single-screen roller derby jam timer. One HTML file, no build step, no dependencies, no network.

## What it does

- **Period clock** — 30:00 per period, two periods.
- **Jam clock** — 2:00 per jam.
- **Lineup** — 0:30 countdown starts automatically when a jam ends.
- **Timeout** — 1:00 countdown; stops the period clock. Available between jams or to end a jam.
- **START JAM / END JAM** — one big context-sensitive button.
- **End-of-jam alert** — a quiet two-note chime plus a vibration when the jam clock reaches 0:00. It's for the phone holder, not the players: low gain, no whistle. Keep the phone volume low or use an earbud. **TEST** fires it on demand; a manual END JAM stays silent.
- **Two-tap RESET** — tap once and the button arms (`SURE?`), tap again to reset the bout.
- **Every time is editable in place** — tap the period clock, the big jam/lineup/timeout clock, or the small `JAM`/`LINEUP`/`TIMEOUT` values under it. Type `m:ss` (or plain seconds) and press SET. Changes apply immediately and are remembered on the device.
- **Light / dark theme** — the header button cycles AUTO → LIGHT → DARK. AUTO is the default and follows the device preference; the choice is remembered.
- The period clock runs through lineup time, stops during timeouts, and stops when it hits 0:00. If it expires mid-jam, the jam plays out and the period ends with it.
- After period 1 the button becomes **START PERIOD 2**; after period 2 it becomes **NEW BOUT**.

Defaults are WFTDA: 2×30:00 periods, 2:00 jams, 0:30 lineup, 1:00 timeout. The four times and the theme choice are saved in `localStorage`; the bout itself is not, so reloading starts a fresh bout with your saved times.

Phone notes: iOS has no Vibration API at all — TEST will say “No vibration API on this browser” — and the ringer switch mutes Web Audio. Android supports both; if TEST says “Vibration blocked by the browser”, check the device/browser vibration settings. Audio needs a tap to unlock (the first button press does that).

## Run

Open `index.html` directly, or serve it:

```sh
python3 -m http.server 8000
```

## Deploy

`.github/workflows/pages.yml` publishes `index.html` and `CNAME` to GitHub Pages. With the custom domain attached, the site is served at **https://jt.madelynn.blue/**.

## Files

```
index.html                     the whole app
CNAME                          custom domain for GitHub Pages
.github/workflows/pages.yml    Pages deployment
```
