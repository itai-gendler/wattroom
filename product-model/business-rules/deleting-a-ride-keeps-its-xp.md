---
appliesTo:
- type: capability
  id: delete-ride
- type: entity
  id: rider
  facts:
  - Total XP
references:
- kind: doc
  role: intent
  target: docs/decisions/0047-deleting-a-ride-keeps-its-xp.md
  title: ADR-0047
---

# Deleting a ride keeps its XP

Deleting a ride is privacy, not work undone: the rider's Total XP and level do not move, and the day's XP ceiling is not given back.
