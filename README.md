# Progressive Overload

A lightweight, mobile-first PWA for tracking gym workouts and monitoring progressive overload over time.

## Features

- **Log workouts** — Select a workout type, customize your exercise list, and log sets/reps/weight as you go
- **Progressive overload tracking** — See how each set compares to your last session with inline deltas (+/- indicators)
- **Progress charts** — Visualize trends for any exercise over time with per-exercise history graphs
- **Workout history** — Browse all past sessions; view full details for any workout
- **Past workout logging** — Optionally backfill sessions with a custom date
- **Workout templates** — Built-in templates for Push + Legs, Pull + Core, and Full Body; templates auto-update based on your last session for that type
- **Exercise types** — Supports weighted (lbs/kg), reps-only, and timed exercises
- **Undo last set** — Remove the most recently logged set while mid-session
- **Works offline** — Service worker caches the app for full offline use
- **No account required** — All data is stored locally in IndexedDB; nothing leaves your device

## Usage

Open the app, tap **LOG WORKOUT**, choose a workout type, adjust the exercise list if needed, then work through your sets. When done, review your entries and save. Tap **VIEW PROGRESS** from the home screen to explore per-exercise charts and history.

## Tech Stack

- Vanilla JS (no frameworks)
- IndexedDB for persistent local storage
- Service worker for offline/PWA support
- Single `index.html` — no build step required

## Development

Clone the repo and open `index.html` directly in a browser, or serve it with any static file server:

```bash
npx serve .
```

The app is deployable to GitHub Pages as-is.
