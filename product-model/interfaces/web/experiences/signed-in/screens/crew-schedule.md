---
entities:
- entity: answer
  shows:
  - Answer
  collects:
  - Answer
- entity: crew
  shows:
  - Name
- entity: crew-membership
  shows:
  - Notify me
- entity: planned-session
  shows:
  - Out
  - Starts at
  - Unanswered
  - Voice channel
  - Who has not answered
  - Who is in
  - Who is out
  - Workout
  collects:
  - Starts at
- entity: session
  shows:
  - Coach
- entity: voice-channel
  shows:
  - Name
- entity: workout
  shows:
  - Name
entryPoints:
- web: /crew/{id}/schedule
references:
- kind: code
  role: implementation
  target: web/src/routes/(app)/crew/[id]/schedule/+page.svelte
---

# Crew schedule

The crew's calendar of planned sessions, with each plan's answers.
