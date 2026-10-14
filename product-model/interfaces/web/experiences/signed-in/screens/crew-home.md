---
entities:
- entity: answer
  collects:
  - Answer
- entity: crew
  shows:
  - Invite code
  - Members
  - Name
  - Owner
- entity: planned-session
  shows:
  - Starts at
  - Who is in
  - Workout
- entity: session
  shows:
  - Workout
entryPoints:
- web: /crew/{id}
references:
- kind: code
  role: implementation
  target: web/src/routes/(app)/crew/[id]/+page.svelte
- kind: code
  role: implementation
  target: web/src/routes/(app)/crew/[id]/CrewNow.svelte
---

# Crew home

One crew's Home: its name, what is live in its voice channels, its next planned session, its invite code, and the way out.
