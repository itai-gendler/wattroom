---
appliesTo:
- type: entity
  id: crew-membership
  effect: removes
permits:
- related:
  - verb: holds
    entity: rider
  when:
  - fact: Role
    is-not: Owner
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_join.go#handleLeaveCrew
---

# A member leaves on their own, and the owner hands the crew on first

Leaving ends the leaver's own seat. The owner may not leave, so a crew is never ownerless.
