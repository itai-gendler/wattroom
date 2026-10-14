---
appliesTo:
- type: entity
  id: session
  effect: changes
  facts:
  - Coach
permits:
- related:
  - verb: coaches
    entity: rider
- unattended: true
references:
- kind: code
  role: implementation
  target: server/internal/hub/channel_ride.go#handOffLocked
- kind: code
  role: implementation
  target: server/internal/hub/channel_ride.go#passSessionLocked
---

# Only the session's coach hands it on, to someone riding in it

When the coach has been gone past the 15-second grace, the Product passes the session to whoever has ridden in it longest and is still pedalling.
