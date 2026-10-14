---
appliesTo:
- type: capability
  id: end-session
- type: capability
  id: ride-workout-alone
- type: entity
  id: rider
  facts:
  - Total XP
  - Level
references:
- kind: code
  role: implementation
  target: server/internal/stats/engine.go
- kind: doc
  role: intent
  target: docs/spec/stats.md
  title: 'Spec: stats formulas'
---

# A ride pays one XP per kilojoule, plus execution and streak bonuses

The execution bonus is the execution score × 50 and the streak bonus 25 per week of the rider's current streak, at most 250. Levels follow Total XP: level n needs 500 × n^1.6.
