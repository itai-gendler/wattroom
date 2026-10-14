---
domain: rides
relations:
- entity: medal
  verb: wins
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: server/internal/rides/detail.go
- kind: code
  role: implementation
  target: server/internal/stats/saver.go
- kind: doc
  role: intent
  target: docs/spec/stats.md
  title: 'Spec: stats formulas'
---

# Ride

One rider's saved ride: alone, free or in a session. A rider's history is the product, so nothing caps it.

## Information kept

- **Workout** — the workout or game ridden, or "Free ride"
- **Started at** — when the ride started
- **Duration** — how long it ran; at least a minute
- **Average power** — in watts
- **Normalized power** — in watts
- **Energy** — in kilojoules
- **Execution score** — the share of riding seconds inside the band around the rider's own target, weighted by intensity
- **Scored** — whether the workout prescribed anything to score; a ramp test, a free ride and a game are not scored
- **FTP at the ride** — the FTP the ride was scored against
- **FTP produced** — the FTP a ramp test measured, once the rider saved it
- **XP** — what the ride paid
- **Power curve** — best efforts at 5 seconds, 1, 5 and 20 minutes
- **Samples** — power every second, with heart rate and cadence when the ride carried them
- **Ridden with** — the crew and voice channel a session ride was ridden in, or alone
- **RPE** — how hard it felt on the Borg CR10 scale, 1–10, when the rider said
- **Note** — one sentence the rider wrote about it, 1–500 characters
