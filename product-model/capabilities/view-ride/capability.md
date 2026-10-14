---
availability:
- place: web::signed-in
domain: rides
references:
- kind: code
  role: implementation
  target: server/internal/rides/detail.go#handleGet
- kind: code
  role: implementation
  target: web/src/routes/(app)/history/[id]/+page.svelte
---

# View a ride

A rider opens one of their rides: its numbers, power trace and zones, heart rate and cadence when it carried them, the medals it won and where it was ridden.
