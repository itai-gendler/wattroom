---
appliesTo:
- type: entity
  id: crew-membership
  effect: changes
  facts:
  - Notify me
  - On the weekly board
permits:
- related:
  - verb: holds
    entity: rider
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_members.go#handleSetCrewPrefs
---

# Only the member changes their own switches for a crew

Notify me and the weekly board's include-me are each rider's own; an owner editing the crew never touches them.
