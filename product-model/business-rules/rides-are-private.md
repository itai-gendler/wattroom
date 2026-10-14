---
appliesTo:
- type: capability
  id: view-ride
- type: entity
  id: ride
references:
- kind: code
  role: implementation
  target: server/internal/rides/rides.go
- kind: code
  role: implementation
  target: web/src/lib/profile/YourData.svelte
---

# A ride is its rider's own unless they share it

Rides are private by default; sharing is per ride and opt-in.
