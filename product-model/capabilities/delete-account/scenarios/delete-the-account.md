---
kind: primary
routes:
  web: Web
steps:
- text: The Rider types the confirmation phrase and deletes their account
  kind: actor
  actor: rider
  entities: []
  contexts:
    web:
      place: web::signed-in::data-settings
- text: The Product hands each crew the Rider owns to its longest-standing admin, else its longest-standing member
  kind: product
  actor: rider
  entities:
  - entity: crew
    effect: changes
    facts:
    - Owner
  - entity: crew-membership
    as: successor
    effect: changes
    facts:
    - Role
  contexts:
    web:
      place: web::signed-in::data-settings
- text: The Product deletes the account with its rides and saved workouts and signs the person out everywhere
  kind: product
  actor: rider
  entities:
  - entity: rider
    effect: removes
  - entity: ride
    effect: removes
    with: rider
  - entity: workout
    effect: removes
    with: rider
  contexts:
    web:
      place: web::signed-in::data-settings
references:
- kind: code
  role: implementation
  target: server/internal/account/delete.go
- kind: code
  role: implementation
  target: server/internal/crews/crew_ownership.go#releaseCrew
---

# Delete the account

## Trigger

A rider leaves WattRoom.

## Outcome

The account is gone; the crews it owned carry on under their next owner.

## Edge cases

- A rider who was in a session's recap is taken out of it.
