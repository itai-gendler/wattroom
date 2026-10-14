---
entities:
- entity: pin
  shows:
  - Body
  - Title
  - Written by
  collects:
  - Body
  - Title
  - Written by
entryPoints:
- web: /crew/{id}/board
references:
- kind: code
  role: implementation
  target: web/src/routes/(app)/crew/[id]/board/+page.svelte
---

# Crew board

What the crew wrote down: the newest announcement across its chat channels, then its pins.
