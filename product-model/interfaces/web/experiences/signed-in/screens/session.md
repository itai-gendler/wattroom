---
entities:
- entity: crew
  shows:
  - Name
- entity: ride
  shows:
  - Workout
- entity: rider
  shows:
  - FTP
  - Weight
- entity: session
  shows:
  - Coach
  - Elapsed
  - Game mode
  - Workout
  collects:
  - Coach
  - Elapsed
  - Game mode
  - Sprint moment
- entity: workout
  shows:
  - Name
entryPoints:
- web: /crew/{id}/s/{session}
references:
- kind: code
  role: implementation
  target: web/src/routes/(app)/crew/[id]/s/[session]/+page.svelte
---

# Session

The session's riding surface in its voice channel: the shared interval timeline, every rider's numbers, the coach's controls, sprints, games and the countdown. On a phone it is the spectator's view.
