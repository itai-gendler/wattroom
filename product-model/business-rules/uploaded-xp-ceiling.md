---
appliesTo:
- type: capability
  id: ride-workout-alone
- type: capability
  id: free-ride
- type: capability
  id: take-ramp-test
- type: entity
  id: ride
references:
- kind: doc
  role: intent
  target: docs/spec/stats.md
  title: 'Spec: XP sources'
---

# Rides saved from the browser pay at most 6,000 XP a day

A ride alone, a free ride or a recovered ride is the client's word, so it is bounded; a ride past the ceiling is saved with what is left, down to none. Session rides are outside it.
