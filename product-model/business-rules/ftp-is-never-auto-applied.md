---
appliesTo:
- type: capability
  id: accept-suggested-ftp
- type: capability
  id: dismiss-suggested-ftp
- type: entity
  id: rider
  facts:
  - Suggested FTP
references:
- kind: doc
  role: intent
  target: docs/spec/stats.md
  title: 'Spec: FTP suggestions'
---

# A suggested FTP is never applied by itself

It is offered when 95 % of the best 20 minutes in the last 90 days beats the set FTP by more than 2 %, and only the rider applies it.
