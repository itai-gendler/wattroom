---
domain: schedule
relations:
- entity: answer
  verb: has
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_schedule.go
- kind: doc
  role: intent
  target: docs/spec/crew.md
  title: 'Spec: planned sessions'
---

# Planned session

A ride the crew puts on its schedule: a workout at a time, in one of its voice channels or none yet. Members say whether they are in.

## Information kept

- **Workout** — the workout it will ride, by name and steps
- **Starts at** — between now and three months out
- **Voice channel** — the voice channel it will run in, or none yet
- **Who is in** — the riders who said they are in, by name
- **Out** — how many said they are out
- **Unanswered** — how many have not answered
- **Who is out** — the names behind Out
- **Who has not answered** — the names behind Unanswered

## States

### Planned

On the schedule and not started. A plan whose time passed unstarted stays startable for 30 minutes, then drops off the schedule.

### Started

A session was opened from it; it leaves the schedule.
