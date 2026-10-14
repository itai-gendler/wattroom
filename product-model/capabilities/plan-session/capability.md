---
availability:
- place: web::signed-in
domain: schedule
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_schedule.go#handleCrewPlan
- kind: doc
  role: intent
  target: docs/spec/crew.md
  title: 'Spec: planned sessions'
---

# Plan a session

A member puts a session on the crew's schedule: a workout at a time, in a voice channel they may enter or none yet. The plan is announced in its channel, and the crew's members who keep notifications on are told.
