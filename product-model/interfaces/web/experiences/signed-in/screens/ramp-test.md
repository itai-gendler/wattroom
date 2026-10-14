---
entities:
- entity: ride
  shows:
  - Power curve
  collects:
  - FTP produced
- entity: rider
  shows:
  - FTP
  collects:
  - FTP
  - FTP source
entryPoints:
- web: /ramp
references:
- kind: code
  role: implementation
  target: web/src/routes/(app)/ramp/+page.svelte
---

# Ramp test

The ramp test and its result.
