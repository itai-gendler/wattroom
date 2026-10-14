---
domain: rides
references:
- kind: code
  role: implementation
  target: server/internal/stats/medals.go#Medals
- kind: doc
  role: intent
  target: docs/spec/stats.md
  title: 'Spec: medals'
---

# Medal

A medal a session awards one rider, measured on their own numbers.

## Information kept

- **Kind** — Diesel (steadiest power), Metronome (best execution), Hammer (best 5-second w/kg) or Lanterne Rouge (last on 5-second w/kg, but finished)
