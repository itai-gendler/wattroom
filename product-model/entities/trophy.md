---
references:
- kind: code
  role: implementation
  target: server/internal/gamify/catalogue.go
- kind: code
  role: implementation
  target: server/internal/gamify/evaluate.go
- kind: doc
  role: intent
  target: docs/spec/stats.md
  title: 'Spec: achievements'
---

# Trophy

An achievement a rider has earned and the XP it paid, once.

## Information kept

- **Achievement** — one of Sunrise Club, Night Shift, 200 Rides, Sufferfest Survivor, Hot End, Espresso Ride, Lounge Lizard, DJ, Crew Chief or Sprint Snob
- **Earned on** — the day it was earned
- **XP paid** — 100, 250 or 500 by the achievement's tier
