---
appliesTo:
- type: capability
  id: change-profile-settings
- type: capability
  id: accept-suggested-ftp
- type: entity
  id: rider
  facts:
  - FTP
  - Weight
  - Threshold heart rate
references:
- kind: doc
  role: intent
  target: docs/spec/stats.md
  title: 'Spec: the rider''s two numbers'
---

# FTP is 50–600 W, weight 30–200 kg and threshold heart rate 100–210 bpm

A number outside the bounds is refused naming the field, never coerced. While a number is still the starting guess, w/kg is withheld.
