---
kind: primary
routes:
  web: Web
steps:
- text: The Rider, the coach, arms a sprint during the running session
  kind: actor
  actor: rider
  entities:
  - entity: session
    effect: changes
    facts:
    - Sprint moment
  contexts:
    web:
      place: web::signed-in::session
- text: The Product counts the riders in and ranks them by best 5-second w/kg on a podium
  kind: product
  actor: rider
  entities:
  - entity: rider
    effect: reads
    facts:
    - Weight
  contexts:
    web:
      place: web::signed-in::session
references:
- kind: code
  role: implementation
  target: server/internal/hub/sprint.go
---

# Arm a sprint

## Trigger

The coach wants a burst of fun in a long endurance block.

## Outcome

The sprint's podium shows; a first place with at least two riders scored counts toward Sprint Snob.
