---
name: verify
description: How to run and drive this app to verify changes end-to-end in a headless browser.
---

# Verifying workout-tracker changes

Single-file vanilla-JS PWA (`index.html`), no build step, data in IndexedDB.

## Launch

```bash
python3 -m http.server 8123 &   # any static server works
```

Drive with Playwright (`chromium` at `/opt/pw-browsers/chromium` on remote runners; `npm install playwright` in a scratch dir, no browser download needed).

## Gotchas

- **A fresh browser profile has an empty DB.** Seed history by clicking the
  **"Load sample data"** button on the empty home screen — `SEED` in
  `index.html` is NOT loaded automatically. Use
  `getByRole('button', { name: 'Load sample data' })` — `text=Load sample
  data` also matches the empty-state paragraph and silently clicks that. Latest seeded Bench Press:
  47.5 kg × [8,8,7]/[8,8,8].
- Flow to the logging screen: **Log a workout → pick "Push + Legs" → Start**.
  Weighted exercises require confirming weight (input prefills from last
  session) before the reps stepper appears.
- Reps are entered via a stepper (`+5` / `+` buttons), then **"Log set N"**.
- Logging or skipping the 3rd set auto-advances to the next exercise (or to
  Review after the last one); there is no "Next exercise" button. To reach
  Review quickly, loop: Confirm weight → Skip set ×3.
- Set deltas lead with estimated 1RM (`+N 1RM`), with volume as a sub-line.
- The workout date defaults to the session's `startedAt` (stored in the
  `inProgressWorkout` localStorage snapshot), not the day you finish.
- On the Review screen, skipped-set boxes are `<button>`s labeled
  "SKIP Set n" — use `exact: true` when locating the "Skip set" action
  button or Playwright strict mode trips.
- Home shows "All notes (N)" when any workout has a note (sample data has one).
- Useful selectors: `.set-box-done`, `.set-box-skip` (per-set boxes with
  inline deltas), `h1` holds the exercise name.
