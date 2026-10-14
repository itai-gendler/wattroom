---
appliesTo:
- type: capability
  id: take-ramp-test
- type: entity
  id: ride
  facts:
  - FTP produced
references:
- kind: doc
  role: intent
  target: docs/spec/stats.md
  title: 'Spec: ramp test'
---

# A ramp test's FTP is 75 % of its best rolling minute

The test ends itself once power stays under 75 % of the target for five seconds. Fewer than two steps past the warm-up produce no FTP. The number is saved only when the rider saves it.
