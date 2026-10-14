---
availability:
- place: web::signed-in
domain: crew-settings
references:
- kind: code
  role: implementation
  target: server/internal/channels/write.go#handleDelete
- kind: code
  role: implementation
  target: web/src/lib/channels.ts#deleteChannelWarning
---

# Delete a channel

The crew's owner or an admin deletes a channel after confirming, with no undo. A chat channel takes its messages; a voice channel takes its recaps, and the sessions planned in it are cancelled when it was private or keep their place on the schedule with no channel when it was open.
