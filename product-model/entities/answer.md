---
domain: schedule
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_schedule.go#handleCrewRsvp
- kind: code
  role: implementation
  target: web/src/lib/session/rsvp.ts
---

# Answer

One rider's answer to one planned session. There is no maybe: a rider is in or out, or has not answered.

## Information kept

- **Answer** — In or Out
