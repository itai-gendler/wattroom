---
kind: primary
routes:
  web: Web
steps:
- text: The Rider picks a game mode, such as Backyard Ramp, in a voice channel with no session
  kind: actor
  actor: rider
  entities:
  - entity: voice-channel
    effect: reads
    facts: []
  - entity: session
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::voice-channel
- text: The Product opens a session for the game with the Rider as coach and runs it at once
  kind: product
  actor: rider
  entities:
  - entity: session
    effect: creates
    to: Running
    facts:
    - Workout
    - Game mode
    - Coach
  contexts:
    web:
      place: web::signed-in::voice-channel
- text: The Product scores every joined rider against their own FTP and keeps the game's own clock
  kind: product
  actor: rider
  entities:
  - entity: rider
    effect: reads
    facts:
    - FTP
    - Weight
  contexts:
    web:
      place: web::signed-in::session
references:
- kind: code
  role: implementation
  target: server/internal/hub/channel_game.go#startGameOn
---

# Start a game in the channel

## Trigger

The crew wants to race each other rather than ride intervals.

## Outcome

The game runs; its rides are saved unscored, and its podium shows when it ends.

## Decision points

### How is the game played?

Which mode was picked?

- Sprint Roulette → five sprints land at random, a klaxon three seconds before each, scored on best 5-second w/kg.
- Points Race → two-minute intervals with four sprints hidden in them, every one scoring.
- Watt Golf → nine holes, each a wattage to hold for ten seconds with the meter hidden.
- Backyard Ramp → three-minute rounds from 80 % FTP, 5 % more each; ten seconds below and the rider is out.
- Collective Ramp → the same on the session's average, so nobody is dropped alone.
- Floor is Lava → a power zone is called every two minutes; leaving it for more than five seconds burns one of three lives.
- Team Relay → one rider on the front at 110 % FTP while the others recover at 55 %, rotating every 60–90 seconds.

## Edge cases

- A rider who drops out of an elimination game has 30 seconds to come back before the rules see their silence.
