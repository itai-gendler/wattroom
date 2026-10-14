---
appliesTo:
- type: entity
  id: ride
  effect: removes
permits:
- related:
  - verb: owns
    entity: rider
references:
- kind: code
  role: implementation
  target: server/internal/rides/rides.go#handleDelete
---

# Only the rider deletes their ride

Someone else's ride reads as absent rather than forbidden.
