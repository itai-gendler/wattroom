---
kind: primary
routes:
  web: Web
steps:
- text: The Rider chooses Ban from the crew on a member
  kind: actor
  actor: rider
  entities:
  - entity: crew-membership
    as: target
    effect: reads
    facts:
    - Role
  - entity: crew
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::crew-members
- text: The Product marks their membership banned and drops their naming into private channels
  kind: product
  actor: rider
  entities:
  - entity: crew-membership
    as: target
    effect: changes
    facts:
    - Role
  - entity: channel-naming
    effect: removes
  contexts:
    web:
      place: web::signed-in::crew-members
- text: The Product cuts them out of every voice channel of the crew at once
  kind: product
  actor: rider
  entities:
  - entity: voice-channel
    effect: changes
    facts:
    - Riders present
  - entity: crew
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::crew-members
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_write.go#handleSetCrewRole
---

# Ban a member

## Trigger

A member is causing trouble.

## Outcome

The rider is banned: out of every channel now, refused at the door later, and on the crew's ban list.
