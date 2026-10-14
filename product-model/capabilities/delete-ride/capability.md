---
availability:
- place: web::signed-in
domain: rides
references:
- kind: code
  role: implementation
  target: server/internal/rides/rides.go#handleDelete
- kind: doc
  role: intent
  target: docs/decisions/0047-deleting-a-ride-keeps-its-xp.md
  title: ADR-0047
---

# Delete a ride

A rider deletes one of their rides for good. Its XP stays: deleting a ride is privacy, not work undone.
