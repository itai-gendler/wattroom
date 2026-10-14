---
kind: primary
routes:
  web: Web
steps:
- text: The Rider chooses Make a new invite link
  kind: actor
  actor: rider
  entities: []
  contexts:
    web:
      place: web::signed-in::crew-settings
- text: The Product gives the crew a new six-character code
  kind: product
  actor: rider
  entities:
  - entity: crew
    effect: changes
    facts:
    - Invite code
  contexts:
    web:
      place: web::signed-in::crew-settings
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_write.go#handleRotateCrewCode
---

# Replace a leaked code

## Trigger

A crew's link was shared further than it should have been.

## Outcome

Only the new code opens the crew's door; members already in stay in.
