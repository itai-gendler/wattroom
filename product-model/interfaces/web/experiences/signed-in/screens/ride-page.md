---
entities:
- entity: medal
  shows:
  - Kind
- entity: ride
  shows:
  - Average power
  - Duration
  - Energy
  - Execution score
  - FTP at the ride
  - Normalized power
  - Note
  - Power curve
  - RPE
  - Ridden with
  - Samples
  - Scored
  - Started at
  - Workout
  - XP
  collects:
  - Note
  - RPE
- entity: rider
  shows:
  - Total XP
entryPoints:
- web: /history/{id}
references:
- kind: code
  role: implementation
  target: web/src/routes/(app)/history/[id]/+page.svelte
---

# Ride

One past ride: its numbers, trace, zones, medals, where it was ridden and how it felt.
