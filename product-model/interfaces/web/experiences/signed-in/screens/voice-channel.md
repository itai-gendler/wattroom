---
entities:
- entity: crew
  shows:
  - Name
- entity: ride
  shows:
  - Workout
- entity: session
  shows:
  - Coach
  - Elapsed
  - Game mode
  - Workout
- entity: voice-channel
  shows:
  - Name
  - Riders present
- entity: workout
  shows:
  - Name
entryPoints:
- web: /crew/{id}/v/{channel}
references:
- kind: code
  role: implementation
  target: web/src/routes/(app)/crew/[id]/v/[channel]/+page.svelte
- kind: code
  role: implementation
  target: web/src/routes/(app)/crew/[id]/v/[channel]/training/+page.svelte
---

# Voice channel

One voice channel: who is present and riding, the session running there or the way to start one, and the free ride when no session holds the rider.
