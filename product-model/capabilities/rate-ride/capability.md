---
availability:
- place: web::signed-in
domain: rides
references:
- kind: code
  role: implementation
  target: server/internal/rides/feel.go#handleFeel
- kind: doc
  role: intent
  target: docs/spec/stats.md
  title: 'Spec: how a ride felt'
---

# Say how a ride felt

After a ride, a rider records how hard it felt on the Borg CR10 scale, 1 to 10, and one sentence about it. Both are optional, erasable and never asked for twice.
