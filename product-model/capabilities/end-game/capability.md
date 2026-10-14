---
availability:
- place: web::signed-in
domain: voice-channels
references:
- kind: code
  role: implementation
  target: server/internal/hub/channel_game.go
---

# End a game

The coach ends the game that is running; a finished game's lingering podium may be cleared by anyone.
