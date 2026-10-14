---
appliesTo:
- type: entity
  id: ride
  effect: changes
  facts:
  - RPE
  - Note
permits:
- related:
  - verb: owns
    entity: rider
references:
- kind: code
  role: implementation
  target: server/internal/rides/feel.go#handleFeel
---

# Only the rider says how their ride felt

A rating and a note are both optional and erasable, and neither feeds the training load.
