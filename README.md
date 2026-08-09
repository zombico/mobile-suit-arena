# Mobile Suit Arena

**Play it now: https://zombico.github.io/mobile-suit-arena/**

> Pilot a mobile suit — or watch the machines fight.

A single-player 3D mech arena that runs entirely in your browser — no server, no install, no account. Exported from [mojulo](https://github.com/zombico/mojulo) as recipes, not renders: `recipe/` is the sovereign source, everything else is its deterministic derived render.

## Game modes

### Single Player — take the cockpit

- **Solo Duel** — 1 v 1: pick your suit and your enemy
- **Team Battle** — BLUE vs RED: pick your suit; allies and enemies drawn at random
- **Free for all** — pick your suit; random enemies, everyone hunts everyone
- **Practice Mode** — no destruction; drill your moves, the AI holds fire until you switch it on

### AI Spectate — watch, WASD free-cam, Tab to switch fighters

- **Solo Duel** — pick both fighters (mirror matches welcome)
- **Team Battle** — pick up to three suits per side
- **Free for all** — pick the cast; everyone fights by default

### Hangar

Inspect the suits up close — turntables, liveries, weapons.

Every mode plays on any of the five maps — **Canyon · City · Depot · Space · Colony** — chosen on the setup screen, with a difficulty select (RECRUIT / ACE / NEWTYPE) on piloted modes. Controls are listed in the in-game pause menu (☰); gamepads are supported.

## How it works

There is no game server. The whole simulation — physics, combat, the AI opponents, the soundtrack — runs in your browser from static files:

- `game.html` — the menu shell (mode picker, setup screens, score screens, music)
- `levels/` — one page per battle: the arena world with three.js inlined
- `assets/figures/` — the rigged mobile suits, stored **once** and shared by every level; your browser caches them, so the first battle downloads the roster (~20 MB compressed) and later battles load in a couple of MB
- `assets/` — the synthesized score (WAV), map stills, hangar portraits

Because the level pages fetch the shared suits from within the folder, the game needs to be served over HTTP (as GitHub Pages does here) — opening `game.html` straight from the filesystem won't load battles.

## Provenance

- game ref: `sk_ms_arena`
- 35 minted level worlds (one `recipe/<ref>.json` each)

Everything under `recipe/` is the sovereign manifest set. On any host running mojulo, those recipes reproduce this exact artifact: each `recipe/<ref>.json` is a world manifest whose `game:` channel mints the level, and `recipe/game.json` promotes them back into this shell. Same recipes → the same game.
