---
kind: primary
routes:
  web: Web
steps:
- text: The Rider picks a workout from the library in a voice channel with no session
  kind: actor
  actor: rider
  entities:
  - entity: voice-channel
    effect: reads
    facts: []
  - entity: session
    effect: reads
    facts: []
  - entity: workout
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::voice-channel
- text: The Product loads it as the channel's session with the Rider as its coach
  kind: product
  actor: rider
  entities:
  - entity: session
    effect: creates
    to: Picked
    facts:
    - Workout
    - Coach
  contexts:
    web:
      place: web::signed-in::voice-channel
- text: The Rider chooses Start
  kind: actor
  actor: rider
  entities: []
  contexts:
    web:
      place: web::signed-in::session
- text: The Product counts in for 10 seconds with the Rider in the ride
  kind: product
  actor: rider
  entities:
  - entity: session
    effect: changes
    from: Picked
    to: Counting in
    facts:
    - Riders in the ride
  - entity: ride
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::session
- text: The Product runs the shared timeline and sends each joined rider's trainer their own share of FTP for each block
  kind: product
  entities:
  - entity: session
    effect: changes
    from: Counting in
    to: Running
    facts:
    - Elapsed
  - entity: rider
    effect: reads
    facts:
    - FTP
  contexts:
    web:
      place: web::signed-in::session
references:
- kind: code
  role: implementation
  target: server/internal/hub/channel_ride.go#controlOn
- kind: code
  role: implementation
  target: server/internal/hub/ws.go#checkPick
---

# Pick a workout and start

## Trigger

The crew is in the Lounge and ready to ride.

## Outcome

The session is running; a 180 W rider and a 320 W rider ride the same intervals at their own watts.

## Edge cases

- The coach may pick another workout before pressing Start; picking never replaces a running session.
- Starting needs the riding screen and a paired trainer; a phone follows the session instead.
