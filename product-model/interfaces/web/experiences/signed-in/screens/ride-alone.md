---
entities:
- entity: ride
  shows:
  - Average power
  - Duration
  - Execution score
  - Power curve
  - Started at
  - XP
- entity: rider
  shows:
  - FTP
- entity: workout
  shows:
  - Name
  - Steps
entryPoints:
- web: /ride
references:
- kind: code
  role: implementation
  target: web/src/routes/(app)/ride/+page.svelte
---

# Ride alone

Where a rider pairs their trainer and rides a workout or a free ride on their own clock.
