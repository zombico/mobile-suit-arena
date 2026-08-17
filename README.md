# Mobile Suit Arena

**▶ Play it now: [zombico.github.io/mobile-suit-arena](https://zombico.github.io/mobile-suit-arena/)**

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

### About — on the title screen (Start / About)

What this is and what made it: levels and suits generated from mojulo's 3D primitives,
music and SFX synthesized from seeded math, pixel art by Codex — with links to the source,
mojulo (GitHub / npm), and mojulo.ai, under the hangar's own theme, *Hangar Vigil*.

## Built with mojulo

There is no game engine and no art pipeline behind this. The whole game was built by
talking to a coding agent whose workshop is [mojulo](https://github.com/zombico/mojulo) —
a local substrate where everything the agent makes is minted as a small deterministic
**recipe** into a SQLite database on the operator's own machine. The suits, the maps, the
match modes, the synthesized music, the tutorial director, and this export are all rows in
that database, each reproducible byte-for-byte from its recipe.

- **Worlds are manifests.** A level is a JSON manifest (see `recipe/`) — terrain geometry,
  the suit roster, arena bounds, match mode, audio — resolved into a three.js scene at
  export time. The simulation is data-composed too: each suit's handling is a plain rule
  object (`speed`, `boostMax`, `dodge`, `tackle`, `boostInertia`, …) interpreted by a
  shared engine, so a new suit is data, not code.
- **Music is math.** The scores and SFX are seeded synthesis (mojulo's beats system) —
  no samples; the WAVs in `assets/` are offline renders of tiny seeded recipes.
- **Levels must prove themselves.** mojulo refuses to mint a game level unless a compiled
  traversal proves it completable — playability is an invariant, not a hope.
- **Mechanics land conversationally.** The newest one, **boost inertia**, shipped exactly
  that way: describe the feel ("the suit should skid for half a second when the thrust
  cuts, leaning against its own momentum, and a melee swing plants it"), and the agent
  wires it into the shared engine as an opt-in rule parameter, regression-tests it, and
  re-mints the fleet — no rig was rebaked, because the braking pose is the existing boost
  animation played transposed (a left skid plays the boost-right lean).

## How a suit is made — the 3D shapes

Every mobile suit is composed from three families of primitive solids, authored as
numbers, never sculpted in a modeling tool:

- **Lathes** — a radius profile spun around an axis, the way a chess pawn is turned on a
  lathe. Limb segments, joints, ankles, gun barrels.
- **Extrudes** — a 2D outline pushed through a depth. Armor plates, the chest box, skirts,
  shields, feet.
- **Sweeps** — a profile dragged along a curved path. Hoses, curved guards, the odd horn.

The flagship suit in this roster is **58 named parts** (`foot_l`, `knee_pad_r`,
`ankle_guard_l`, `thigh_cross_r`, …) totalling **479 primitives** — 137 lathes, 330
extrudes, 12 sweeps. Each part is authored alone at its own origin on mojulo's
*workbench*, then an *assembler* seats the parts into one body (parts drop under gravity
onto the part below, so nobody hand-computes a lift). The assembled body is welded to a
skeleton — each part rides one bone — and animation is procedural pose curves shared by
the whole roster: every suit walks, boosts, and swings from the same choreography shelf,
which is why a new suit inherits the full moveset the moment it is assembled.

There are no textures and no runtime lights. Every primitive carries a tint and a material
grain, baked into per-vertex colours; the hero finishes go one step further and bake full
global illumination into those same vertex colours offline — which is how the suits read
as lit metal while the browser does zero lighting work.

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
