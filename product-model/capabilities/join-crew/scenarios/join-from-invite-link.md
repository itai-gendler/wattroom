---
kind: primary
routes:
  web: Web
steps:
- text: The Rider opens the crew's invite link
  kind: actor
  actor: rider
  entities:
  - entity: crew
    effect: reads
    facts:
    - Name
    - Icon
    - Picture
    - Weekly board
  contexts:
    web:
      place: web::signed-in::crew-door
- text: The Rider chooses Join
  kind: actor
  actor: rider
  entities: []
  contexts:
    web:
      place: web::signed-in::crew-door
- text: The Product makes the Rider a member of the crew
  kind: product
  actor: rider
  entities:
  - entity: crew-membership
    effect: creates
    facts:
    - Role
    - Joined on
    - Notify me
    - On the weekly board
  - entity: crew
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::crew-door
- text: The Product opens the crew's Home
  kind: product
  actor: rider
  entities:
  - entity: crew
    effect: reads
    facts:
    - Name
    - Members
  contexts:
    web:
      place: web::signed-in::crew-home
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_join.go#handleJoinCrew
- kind: code
  role: implementation
  target: server/internal/crews/crew_join.go#handleRememberCrewDoor
---

# Join from an invite link

## Trigger

A friend sends a rider their crew's link.

## Outcome

The rider is a Member of the crew and lands on its Home; its open channels are theirs to enter.

## Edge cases

- A signed-out person following the link signs in first and comes back to the same door.
- A rider who signs up in another tab is still pointed at the crew whose door they last opened.
