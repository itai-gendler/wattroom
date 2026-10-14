---
appliesTo:
- type: capability
  id: end-session
- type: capability
  id: ride-workout-alone
- type: capability
  id: free-ride
- type: entity
  id: ride
references:
- kind: code
  role: implementation
  target: server/internal/rides/save.go
- kind: code
  role: implementation
  target: server/internal/protocol/limits.go
---

# A ride under a minute is not saved

The same rule holds for a session ride, a ride alone and a free ride. A ride the browser saves is also refused when it runs over six hours.
