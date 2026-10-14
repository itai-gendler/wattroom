---
kind: validation
routes:
  web: Web
steps:
- text: The Rider picks a workout with a heart-rate hold, or one longer than a day or too large to share
  kind: actor
  actor: rider
  entities:
  - entity: workout
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::voice-channel
- text: The Product refuses it and says why in one line
  kind: product
  actor: rider
  entities: []
  contexts:
    web:
      place: web::signed-in::voice-channel
references:
- kind: code
  role: implementation
  target: server/internal/hub/ws.go#checkPick
---

# A workout a session cannot ride

## Trigger

The coach picks a workout made for riding alone.

## Outcome

No session is loaded.
