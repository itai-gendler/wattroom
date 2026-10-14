---
kind: primary
routes:
  web: Web
steps:
- text: The Rider chooses Make member on an admin
  kind: actor
  actor: rider
  entities:
  - entity: crew-membership
    as: target
    effect: reads
    facts:
    - Role
  contexts:
    web:
      place: web::signed-in::crew-members
- text: The Product makes them a plain member
  kind: product
  actor: rider
  entities:
  - entity: crew-membership
    as: target
    effect: changes
    facts:
    - Role
  contexts:
    web:
      place: web::signed-in::crew-members
- text: The Product takes them out of the voice of any private channel they are not named into
  kind: product
  actor: rider
  entities:
  - entity: voice-channel
    effect: changes
    facts:
    - Riders present
  contexts:
    web:
      place: web::signed-in::crew-members
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_write.go#handleSetCrewRole
---

# Make an admin a member

## Trigger

An admin no longer helps run the crew.

## Outcome

They are a Member and keep only what a member may do.
