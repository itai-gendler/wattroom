---
kind: primary
routes:
  web: Web
steps:
- text: The Rider chooses Join the ride
  kind: actor
  actor: rider
  entities:
  - entity: session
    effect: reads
    facts:
    - Workout
    - Elapsed
  - entity: ride
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::session
- text: The Product adds the Rider to the ride and sets their trainer to their own share of FTP at the current block
  kind: product
  actor: rider
  entities:
  - entity: session
    effect: changes
    facts:
    - Riders in the ride
  - entity: rider
    effect: reads
    facts:
    - FTP
  - entity: ride
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::session
references:
- kind: code
  role: implementation
  target: server/internal/hub/channel_ride.go
---

# Join a running session

## Trigger

A member arrives ten minutes into the session.

## Outcome

The member rides the rest of the session in sync with everyone.

## Edge cases

- A rider who stops pedalling pauses only their own targets; the shared timeline never waits.
- Joining saves any free ride or own workout the rider was riding in the channel first.
