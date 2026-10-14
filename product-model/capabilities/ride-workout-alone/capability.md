---
availability:
- place: web::signed-in
domain: ride
references:
- kind: code
  role: implementation
  target: web/src/routes/(app)/ride/+page.svelte
- kind: code
  role: implementation
  target: server/internal/rides/save.go
- kind: doc
  role: intent
  target: docs/spec/roles.md
  title: 'Spec: a ride alone'
---

# Ride a workout alone

A rider pairs their trainer and rides a workout from the library or their own shelf on their own clock: a 3-second count-in, then each block at their own share of FTP. Alone, they keep +1 min and Skip block. The ride is saved and scored like any other.
