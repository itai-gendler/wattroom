---
type: web
actors:
- visitor
- rider
entryPoints:
- web: /login
- web: /home
- web: /c/{code}
references:
- kind: code
  role: implementation
  target: web/src/routes/(app)/+layout.svelte
- kind: code
  role: implementation
  target: server/spa.go
---

# WattRoom web app

The WattRoom app in Chrome or Edge, where riders pair their smart trainer over
Bluetooth: crews and their channels, sessions, riding alone, workouts and
rides. A phone opens the same app to follow a session, chat and plan.
