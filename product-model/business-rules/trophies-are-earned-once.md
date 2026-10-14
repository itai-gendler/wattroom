---
appliesTo:
- type: entity
  id: trophy
references:
- kind: code
  role: implementation
  target: server/internal/gamify/catalogue.go
- kind: doc
  role: intent
  target: docs/spec/stats.md
  title: 'Spec: achievements'
---

# A trophy is earned once, from what the Product can verify itself

Achievements pay 100, 250 or 500 XP the day they are earned and never again; clock achievements use the rider's own time zone, and nothing a client merely claims earns one.
