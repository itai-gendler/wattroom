---
kind: edge
routes:
  web: Web
steps:
- text: The coach's last connection has been gone for the 15-second grace
  kind: condition
  unattended: true
  entities:
  - entity: session
    effect: reads
    facts:
    - Coach
  contexts:
    web:
      place: web::signed-in::session
- text: The Product passes the session to whoever has ridden in it longest and is still pedalling, and says so on the timeline
  kind: product
  entities:
  - entity: session
    effect: changes
    facts:
    - Coach
  contexts:
    web:
      place: web::signed-in::session
references:
- kind: code
  role: implementation
  target: server/internal/hub/channel_ride.go#passSessionLocked
- kind: code
  role: implementation
  target: server/internal/hub/channel_presence.go#sayDepartedLocked
---

# The coach is gone

## Trigger

The coach's laptop dies mid-session.

## Outcome

Someone riding can pause, resume and hand it on; with nobody riding, an owner's or admin's End is the way out.
