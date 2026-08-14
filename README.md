# Mobile Suit Arena

A standalone playable game exported from [mojulo](https://github.com/zombico/mojulo) — recipes, not renders: `recipe/` is the sovereign source, everything else is its deterministic derived render.

> Pilot a mobile suit — or watch the machines fight.

## Game modes

### Tutorial — Learn your machine — two guided sorties

- **1. Mobile Suit Rising** — City — movement, boost, vulcans, the saber *(maps: City)*
- **2. Canyon Rumble** — Canyon — weapon switching, staggers, an ACE, then backup arrives *(maps: Canyon)*
- **3. Encounters in Space** — Space — 6DoF thrust, the space roll, first contact *(maps: Space)*

### Single Player — Take the cockpit

- **Solo Duel** — 1 v 1 — pick your suit and your enemy *(maps: Canyon · City · Depot · Arctic Launch · Space · Colony)*
- **Team Battle** — pick your suit — allies and enemies at random *(maps: Canyon · City · Depot · Arctic Launch · Space · Colony)*
- **Free for all** — pick your suit — random enemies *(maps: Canyon · City · Depot · Arctic Launch · Space · Colony)*
- **Practice Mode** — no destruction — drill your moves; the AI holds fire until you switch it on *(maps: Canyon · City · Depot · Arctic Launch · Space · Colony)*

### AI Spectate — Watch — WASD free-cam, Tab to switch fighters

- **Solo Duel** — watch a 1 v 1 *(maps: Canyon · City · Depot · Arctic Launch · Space · Colony)*
- **Team Battle** — watch BLUE vs RED *(maps: Canyon · City · Depot · Arctic Launch · Space · Colony)*
- **Free for all** — watch an all-AI free-for-all *(maps: Canyon · City · Depot · Arctic Launch · Space · Colony)*

### Hangar — Inspect the suits — turntable, liveries, weapons

## Provenance

- game ref: `sk_ms_arena`
- manifest sha256/16: `ecc2375e5365db5e`
- levels: 45 minted level worlds (one `recipe/<ref>.json` each)

## How to play

Serve this folder with any static server and open `game.html`:

```bash
npx serve .        # or: python3 -m http.server
```

GitHub Pages works as-is (the folder has zero EXTERNAL dependencies — no CDN).
Level pages fetch the shared rigged-figure bank from `assets/figures/` within
this folder (hoisted out of each page so no file tops static hosts' size
limits, and the browser caches the suits across levels) — so the folder needs
an HTTP server; opening `game.html` via `file://` will not load levels.

World geometry is likewise hoisted into shared `assets/geometry/` files (levels
that play on the same map fetch its terrain once and the browser caches it).

## How to re-mint

On any host running mojulo, the recipes under `recipe/` reproduce this artifact:
each `recipe/<ref>.json` is a world manifest (`compose_world` + its `game:`
channel mints the level), and `recipe/game.json` is the game manifest
(`create_game` promotes the levels back into this shell). Same recipes → the
same game, byte-for-byte where it matters.

## Files

- `assets/` — 117 files, 198 MB
- `game.html` — 157 KB
- `recipe/` — 53 files, 34 MB
- `levels/` — 73 files, 124 MB
