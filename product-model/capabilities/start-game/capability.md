---
availability:
- place: web::signed-in
domain: voice-channels
references:
- kind: code
  role: implementation
  target: server/internal/hub/channel_game.go#startGameOn
- kind: code
  role: implementation
  target: server/internal/hub/game.go
- kind: doc
  role: intent
  target: docs/spec/game-modes.md
  title: 'Spec: game mode parameters'
---

# Start a game

Someone present in a voice channel starts one of the seven game modes, decided by watts alone and measured on each rider's own FTP. With no session running the game opens one with them as coach; inside a running session the coach starts it.
