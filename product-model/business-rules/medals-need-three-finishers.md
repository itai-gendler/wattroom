---
appliesTo:
- type: capability
  id: end-session
- type: entity
  id: medal
references:
- kind: code
  role: implementation
  target: server/internal/stats/medals.go#Medals
- kind: doc
  role: intent
  target: docs/spec/stats.md
  title: 'Spec: medals'
---

# Medals are awarded only when at least three riders finish the session

Finishing means the rider reached the workout's final block. Among the finishers who reported power: Hammer goes to the best 5-second w/kg and Lanterne Rouge to the lowest; Metronome to the best execution, only when the workout scored anything; Diesel to the steadiest power across steady blocks, only when there were steady blocks. Ties go to the earlier joiner.
