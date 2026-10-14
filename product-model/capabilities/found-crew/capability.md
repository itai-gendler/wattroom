---
availability:
- place: web::signed-in
domain: crews
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_found.go#handleFoundCrew
- kind: code
  role: implementation
  target: web/src/lib/home/StartOrJoin.svelte
---

# Found a crew

A rider starts a crew by naming it. They own it, and it opens with a chat channel and a voice channel, both called Lounge, so there is somewhere to talk and somewhere to ride from the first second.
