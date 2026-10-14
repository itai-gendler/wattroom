---
appliesTo:
- type: capability
  id: start-session
- type: capability
  id: start-planned-session
- type: capability
  id: start-game
- type: entity
  id: session
references:
- kind: code
  role: implementation
  target: server/internal/hub/channel_ride.go#refusalLocked
- kind: code
  role: implementation
  target: server/internal/channels/write.go#handleDelete
---

# A voice channel runs one session at a time

Starting another while one runs there is refused, naming its coach. A session holds its channel: the channel cannot be deleted while it runs.
