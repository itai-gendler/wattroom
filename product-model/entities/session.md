---
domain: voice-channels
references:
- kind: code
  role: implementation
  target: server/internal/hub/session.go
- kind: code
  role: implementation
  target: server/internal/hub/channel_ride.go
- kind: doc
  role: intent
  target: docs/spec/roles.md
  title: 'Spec: session lifecycle'
---

# Session

One shared ride in a voice channel: a workout or a game on one timeline, run by its coach, with each joined rider riding their own share of FTP. A session lives while it runs; what lasts are the rides, medals and recap it leaves.

## Information kept

- **Workout** — the workout every joined rider rides at their own FTP, or the game's name
- **Game mode** — the game being played, when one runs: Sprint Roulette, Points Race, Watt Golf, Backyard Ramp, Collective Ramp, Floor is Lava or Team Relay
- **Coach** — the rider running the session: whoever started it, until it is handed on
- **Riders in the ride** — who joined the ride; anyone else in the channel is watching
- **Elapsed** — where the shared timeline stands
- **Sprint moment** — an all-out sprint the coach armed, scored on best 5-second w/kg

## States

### Picked

A workout is loaded and the session has not started.

### Counting in

The 10-second countdown before the timeline starts.

### Running

The shared timeline is moving.

### Paused

The coach holds the timeline.

### Ended

The timeline ran out or the session was ended; its rides are being saved.
