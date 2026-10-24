# playtest-builds

Playable web builds of Jan's Godot prototypes. **Builds only, no source.**

- Open https://janxzs.github.io/playtest-builds/ and pick a build, or link one directly with `#<build-id>`.
- `engine/<godot-version>/`: the shared Godot web engine (no-threads export, no COOP/COEP needed).
- `builds/<game>/<build-id>/<game>.pck`: one small game pack per build. Build ids are `pr<N>-<sha7>-<date>` (or `main-<sha7>-<date>` for direct merges). Each entry in `versions.json` carries controls and what-to-test notes, shown under **Notes** in the picker.
- `versions.json`: the list of published builds, newest first. Builds are never deleted.

Browser builds are offline/solo: ENet multiplayer doesn't run on the web.
