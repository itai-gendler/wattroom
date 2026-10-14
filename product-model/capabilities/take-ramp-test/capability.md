---
availability:
- place: web::signed-in
domain: ride
references:
- kind: code
  role: implementation
  target: web/src/routes/(app)/ramp/+page.svelte
- kind: code
  role: implementation
  target: server/internal/rides/ftp_after.go
- kind: doc
  role: intent
  target: docs/spec/stats.md
  title: 'Spec: ramp test'
---

# Take a ramp test

A rider measures their FTP: five minutes of warm-up, then a target that starts at 100 W and climbs 20 W a minute until they cannot hold it. Their FTP is 75 % of their best minute, offered to save, never applied by itself. The test is saved as an unscored ride.
