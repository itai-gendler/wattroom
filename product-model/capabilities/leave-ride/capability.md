---
availability:
- place: web::signed-in
domain: voice-channels
references:
- kind: code
  role: implementation
  target: server/internal/hub/channel_ride.go#controlOn
---

# Leave the ride

A rider in a session leaves its ride and stays in the channel, watching or riding on their own.
