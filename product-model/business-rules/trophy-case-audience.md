---
appliesTo:
- type: capability
  id: view-rider-page
- type: entity
  id: trophy
references:
- kind: code
  role: implementation
  target: server/internal/gamify/api.go
- kind: doc
  role: intent
  target: docs/spec/stats.md
  title: 'Spec: achievements'
---

# A rider's trophy case shows to those who share a channel with them and to their friends

Their XP breakdown and progress counts are theirs alone; everyone else gets no answer at all.
