---
scope: 'The WattRoom web app and its Go server: sign-in, crews, channels, chat, the schedule, sessions and game modes, riding alone, workouts, rides, medals, XP and trophies.'
method: Static reading of the Go handlers, hub and queries and the SvelteKit routes, with the product spec and decisions as leads.
covered:
- description: Server handlers for crews, membership, roles, the directory, pins, the schedule and recaps.
  paths:
  - server/internal/crews/
  - server/internal/recap/
- description: Server handlers for channels, channel access and moving riders.
  paths:
  - server/internal/channels/
- description: Server handlers for chat channel messages and announcements.
  paths:
  - server/internal/chat/
- description: 'The live voice-channel hub: sessions, coaches, game modes, sprint moments and presence.'
  paths:
  - server/internal/hub/
- description: Workout parsing and validation, and the saved workout shelf.
  paths:
  - server/internal/workout/
  - server/internal/customworkouts/
- description: Ride saving, ride detail, feel, FIT download, stats, medals, XP and trophies.
  paths:
  - server/internal/rides/
  - server/internal/stats/
  - server/internal/gamify/
  - server/internal/fitexport/
  - server/internal/progression/
  - server/internal/riders/
- description: Sign-in, the account, profile numbers and account deletion.
  paths:
  - server/internal/auth/
  - server/internal/account/
- description: Shared protocol vocabulary, limits and the database schema and queries behind the covered areas.
  paths:
  - server/internal/protocol/
  - server/internal/store/
- description: Web pages for signing in, Home, crews, channels, sessions, riding alone, the ramp test, workouts, rides, rider pages and settings.
  paths:
  - web/src/routes/(app)/login/
  - web/src/routes/(app)/home/
  - web/src/routes/(app)/enter/
  - web/src/routes/(app)/c/
  - web/src/routes/(app)/crew/
  - web/src/routes/(app)/crews/
  - web/src/routes/(app)/ride/
  - web/src/routes/(app)/ramp/
  - web/src/routes/(app)/workouts/
  - web/src/routes/(app)/history/
  - web/src/routes/(app)/u/
  - web/src/routes/(app)/settings/
  - web/src/routes/(app)/+layout.svelte
- description: Web client code for crews, channels, chat, sessions, riding, workouts, trophies and the account.
  paths:
  - web/src/lib/channel/
  - web/src/lib/session/
  - web/src/lib/ride/
  - web/src/lib/workout/
  - web/src/lib/chat/
  - web/src/lib/trophies/
  - web/src/lib/pins/
  - web/src/lib/announce/
  - web/src/lib/home/
  - web/src/lib/auth/
  - web/src/lib/profile/
  - web/src/lib/ble/
  - web/src/lib/crew.ts
  - web/src/lib/channels.ts
  - web/src/lib/crew-schedule.ts
  - web/src/lib/account.svelte.ts
exclusions:
- description: Developer mock pages, the seed command and performance probes.
  paths:
  - web/src/routes/(app)/dev/
  - server/cmd/seed/
  - web/src/lib/perf/
- description: Build, release, deployment and CI tooling.
  paths:
  - .github/
  - deploy/
  - scripts/
  - Dockerfile
  - docker-compose.yml
  - Makefile
  - changelog.d/
- description: 'Operational plumbing with no product behavior: metrics, health, retries, budgets and job bookkeeping.'
  paths:
  - server/internal/metrics/
  - server/internal/jobmetrics/
  - server/internal/retry/
  - server/internal/safego/
  - server/internal/budget/
  - server/internal/housekeeping/
  - server/internal/httpx/
  - server/internal/testx/
- description: Visual identity, theming, fonts, motion and shared presentational components.
  paths:
  - web/src/lib/brand/
  - web/src/lib/fonts/
  - web/src/lib/motion/
  - web/src/lib/components/
  - web/src/lib/themes.ts
  - web/src/lib/theme.svelte.ts
- description: End-to-end browser tests.
  paths:
  - web/e2e/
unmapped:
- description: 'The desktop app shell: native Bluetooth, the floating HUD, notifications and the sign-in hand-off.'
  paths:
  - desktop/
  - web/src/routes/(app)/hud/
  - web/src/lib/hud/
- description: Voice and camera, the jukebox, crew and personal playlists, the music pool and the soundboard.
  paths:
  - server/internal/av/
  - server/internal/audio/
  - server/internal/playlists/
  - server/internal/tracks/
  - server/internal/board/
  - web/src/lib/sound/
  - web/src/lib/music/
  - web/src/lib/board/
  - web/src/routes/(app)/music/
- description: Friends, direct messages, pokes, personal status lines, crew emoji, GIFs and link previews.
  paths:
  - server/internal/friends/
  - server/internal/dms/
  - server/internal/status/
  - server/internal/emoji/
  - server/internal/gifs/
  - server/internal/unfurl/
  - server/internal/blocks/
  - web/src/lib/friends/
  - web/src/lib/dm/
  - web/src/lib/messages/
  - web/src/lib/emoji/
  - web/src/lib/status-line/
  - web/src/routes/(app)/friends/
  - web/src/routes/(app)/messages/
  - web/src/routes/(app)/dm/
- description: Roads, routes, races, the world and its living scenery, the wardrobe and the wallet.
  paths:
  - server/internal/road/
  - server/internal/routes/
  - server/internal/race/
  - server/internal/wardrobe/
  - server/internal/wallet/
  - web/src/lib/world/
  - web/src/lib/road/
  - web/src/lib/race/
  - web/src/lib/wardrobe/
- description: Training-service connections and ride delivery, calendar feeds, personal tokens and the MCP server.
  paths:
  - server/internal/strava/
  - server/internal/intervals/
  - server/internal/tokens/
  - server/internal/mcp/
  - server/internal/crews/calendar.go
- description: Email and browser notifications, the session reminder mail and unsubscribe links.
  paths:
  - server/internal/notify/
- description: Feedback reports, avatars, link-preview cards and the account export.
  paths:
  - server/internal/feedback/
  - server/internal/avatars/
  - server/internal/og/
  - server/internal/account/export.go
- description: The public marketing site, its FTP calculator and game-mode demo, and the legal pages.
  paths:
  - web/src/routes/(site)/
  - web/src/lib/site/
  - web/src/routes/(app)/(legal)/
limitations: []
---

# Coverage
