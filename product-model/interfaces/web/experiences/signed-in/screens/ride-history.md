---
entities:
- entity: ride
  shows:
  - Average power
  - Duration
  - FTP at the ride
  - FTP produced
  - Ridden with
  - Started at
  - Workout
  - XP
- entity: rider
  shows:
  - FTP
  - Suggested FTP
  collects:
  - FTP
  - FTP source
entryPoints:
- web: /history
references:
- kind: code
  role: implementation
  target: web/src/routes/(app)/history/+page.svelte
---

# Rides

The rider's ride history with their FTP trend and power curve, and the FTP prompt when the curve outgrows the setting.
