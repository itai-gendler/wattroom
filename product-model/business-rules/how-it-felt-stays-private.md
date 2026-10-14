---
appliesTo:
- type: entity
  id: ride
  effect: reads
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
  target: server/internal/rides/feel.go
- kind: doc
  role: intent
  target: docs/decisions/0055-a-shared-ride-carries-numbers-not-words.md
  title: ADR-0055
---

# Only the rider reads how their ride felt

Sharing a ride shares the numbers the trainer recorded; the rating and the note stay on the rider's own account and in their export.
