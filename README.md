# Jam Timer

Single-screen roller derby jam timer. One HTML file, no build step, no dependencies, no network.

## What it does

- **Period clock** — 30:00 per period, two periods.
- **Jam clock** — 2:00 per jam, then counts into negative (red) until you press END JAM.
- **Lineup** — 0:30 countdown starts when a jam ends, then counts into negative (red) until START JAM.
- **Lineup cues** — at the configurable five-second call (default 5 s; set it to 0 to turn it off) a 1.1 s haptic, a quiet tick and a clock pulse; at 0:00 the chime + haptic alert.
- **Cue settings** — the gear button opens a small panel with Sound and Haptics switches for jam end, lineup warning, and lineup end. Choices are saved on the device; the panel's test buttons always fire both.
- **Timeout** — 1:00 countdown; stops the period clock. Available between jams or to end a jam.
- **START JAM / END JAM** — one big context-sensitive button. The jam does not auto-end and the lineup does not freeze: both clocks run past 0:00 so you can see how late you are, and the overrun is shown as `-0:01` plus “0:01 over”.
- **End-of-jam alert** — a quiet two-note chime plus a vibration when the jam clock reaches 0:00. It's for the phone holder, not the players: low gain, no whistle. Keep the phone volume low or use an earbud. The settings panel's **Test sound** / **Test haptics** buttons fire it on demand; a manual END JAM stays silent. The same chime + haptic fires when the lineup reaches 0:00.
- **Two-tap RESET** — tap once and the button arms (`SURE?`), tap again to reset the bout.
- **Every time is editable in place** — tap the period clock, the big jam/lineup/timeout clock, or the small `JAM`/`LINEUP`/`TIMEOUT`/`WARN` values under it. Nudge with −10s/−1s/+1s/+10s (applies live) or type minutes and seconds, then SET. Changes are remembered on the device.
- **Light / dark theme** — the header button cycles AUTO → LIGHT → DARK. AUTO is the default and follows the device preference; the choice is remembered.
- The period clock runs through lineup time, stops during timeouts, and stops when it hits 0:00. If it expires mid-jam, the jam plays out and the period ends with it.
- After period 1 the button becomes **START PERIOD 2**; after period 2 it becomes **NEW BOUT**.

Defaults are WFTDA: 2×30:00 periods, 2:00 jams, 0:30 lineup, 1:00 timeout. The four times and the theme choice are saved in `localStorage`; the bout itself is not, so reloading starts a fresh bout with your saved times.

Phone notes: iOS has no Vibration API at all — the Test haptics button will say “No vibration API on this browser” — and the ringer switch mutes Web Audio. Android supports both, but Silent/DND mode and the system vibration settings can suppress it; if it says “Vibration blocked by the browser”, check those, and if it says “Vibration sent” but you feel nothing, the device is suppressing haptics. Audio needs a tap to unlock (the first button press does that).

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
