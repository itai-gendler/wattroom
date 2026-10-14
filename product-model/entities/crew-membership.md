---
domain: members
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_write.go
- kind: code
  role: implementation
  target: server/internal/crews/crew_members.go
---

# Crew membership

A rider's seat in one crew and the role it holds there. A ban is a membership too: it keeps the seat, so it survives every way back in.

## Information kept

- **Role** — Owner, Admin, Member or Banned
- **Joined on** — the day the rider joined the crew
- **Notify me** — whether planned sessions in this crew mail and notify the rider
- **On the weekly board** — whether the rider's week appears on the crew's weekly board
