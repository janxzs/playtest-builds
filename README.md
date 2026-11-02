# playtest-builds

Playable web builds of Jan's Godot prototypes. **Builds only, no source.**

- Open https://janxzs.github.io/playtest-builds/, pick a game, then press Play on a build. The engine loads only when a build is opened.
- `engine/<godot-version>/`: the shared Godot web engine (no-threads export, no COOP/COEP needed).
- `builds/<game>/<build-id>/<game>.pck`: one small game pack per build. Build ids are `pr<N>-<sha7>-<date>` (or `main-<sha7>-<date>` for direct merges). Each entry in `versions.json` carries controls and what-to-test notes, shown on each build card.
- `games.json`: the games on the home page, in order: `slug`, `name`, one-line `description`, source `repo`, `project` (dir holding `project.godot`) and optional `scene` (main-scene override). Games can come from different repos; a build's `game` field is one of these slugs.
- `versions.json`: the list of published builds, newest first by `datetime` (the source merge commit's time, ISO 8601 with the America/Los_Angeles offset). Builds are never deleted.

Browser builds are offline/solo: ENet multiplayer doesn't run on the web.

## Hosted Zeigote servers ("Start server" on the picker)
Zeigote builds that have an image on Edgegap show a **Start server** button on the Zeigote page. It talks to a small Cloudflare Worker
(`https://zeigote-servers.janxzs.workers.dev`, source and deploy script in the hosting notes, not in this repo) that starts an Edgegap
**free-tier** server for that build near you, near Los Angeles if your location can't be used.
- Enter the passcode Jan gave you (kept in this browser only), press **Start server**, wait 5-30 s, then use **Play** (opens this page with `?server=wss://...`), **Copy link** for friends, or **Copy desktop command** (`--connect wss://...`).
- Free tier: one server at a time, 60 minutes at most. It stops by itself 10 minutes after the last player leaves. **Stop server** ends it early.
- The Worker never uploads or creates anything: only builds that already have an Edgegap version can be started. Builds without one show "No hosted server for this build".
- No secrets live in this repo or in the page. The passcode and the Edgegap token are Worker secrets; the page only sends the passcode you type.
