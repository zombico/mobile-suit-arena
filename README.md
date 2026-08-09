# Mobile Suit Arena

A standalone playable game exported from [mojulo](https://github.com/zombico/mojulo) — recipes, not renders: `recipe/` is the sovereign source, everything else is its deterministic derived render.

## Provenance

- game ref: `sk_ms_arena`
- manifest sha256/16: `47861003dfa5d6f9`
- levels:
  - `sk_ms_arena_solo_ground` — Solo Duel · Canyon
  - `sk_ms_arena_solo_city` — Solo Duel · City
  - `sk_ms_arena_solo_hangar` — Solo Duel · Depot
  - `sk_ms_arena_solo_space` — Solo Duel · Space
  - `sk_ms_arena_solo_colony` — Solo Duel · Colony
  - `sk_ms_arena_practice_ground` — Practice · Canyon
  - `sk_ms_arena_practice_city` — Practice · City
  - `sk_ms_arena_practice_hangar` — Practice · Depot
  - `sk_ms_arena_practice_space` — Practice · Space
  - `sk_ms_arena_practice_colony` — Practice · Colony
  - `sk_ms_arena_team_ground` — Team Battle · Canyon
  - `sk_ms_arena_team_city` — Team Battle · City
  - `sk_ms_arena_team_hangar` — Team Battle · Depot
  - `sk_ms_arena_team_space` — Team Battle · Space
  - `sk_ms_arena_team_colony` — Team Battle · Colony
  - `sk_ms_arena_ffa_ground` — Free for all · Canyon
  - `sk_ms_arena_ffa_city` — Free for all · City
  - `sk_ms_arena_ffa_hangar` — Free for all · Depot
  - `sk_ms_arena_ffa_space` — Free for all · Space
  - `sk_ms_arena_ffa_colony` — Free for all · Colony
  - `sk_ms_arena_watch_solo_ground` — AI Spectate — Solo Duel · Canyon
  - `sk_ms_arena_watch_solo_city` — AI Spectate — Solo Duel · City
  - `sk_ms_arena_watch_solo_hangar` — AI Spectate — Solo Duel · Depot
  - `sk_ms_arena_watch_solo_space` — AI Spectate — Solo Duel · Space
  - `sk_ms_arena_watch_solo_colony` — AI Spectate — Solo Duel · Colony
  - `sk_ms_arena_watch_team_ground` — AI Spectate — Team Battle · Canyon
  - `sk_ms_arena_watch_team_city` — AI Spectate — Team Battle · City
  - `sk_ms_arena_watch_team_hangar` — AI Spectate — Team Battle · Depot
  - `sk_ms_arena_watch_team_space` — AI Spectate — Team Battle · Space
  - `sk_ms_arena_watch_team_colony` — AI Spectate — Team Battle · Colony
  - `sk_ms_arena_watch_ffa_ground` — AI Spectate — Free for all · Canyon
  - `sk_ms_arena_watch_ffa_city` — AI Spectate — Free for all · City
  - `sk_ms_arena_watch_ffa_hangar` — AI Spectate — Free for all · Depot
  - `sk_ms_arena_watch_ffa_space` — AI Spectate — Free for all · Space
  - `sk_ms_arena_watch_ffa_colony` — AI Spectate — Free for all · Colony

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

## How to re-mint

On any host running mojulo, the recipes under `recipe/` reproduce this artifact:
each `recipe/<ref>.json` is a world manifest (`compose_world` + its `game:`
channel mints the level), and `recipe/game.json` is the game manifest
(`create_game` promotes the levels back into this shell). Same recipes → the
same game, byte-for-byte where it matters.

## Files

- `assets/menu-art.png` — 3642 KB
- `assets/setup-art.png` — 2020 KB
- `assets/maps/map-canyon.png` — 826 KB
- `assets/maps/map-city.png` — 700 KB
- `assets/maps/map-hangar.png` — 85 KB
- `assets/maps/map-space.png` — 185 KB
- `assets/maps/map-colony.png` — 809 KB
- `game.html` — 148 KB
- `recipe/game.json` — 30 KB
- `assets/figures/g_multi-30f8c540.json` — 11076 KB
- `assets/figures/z_multi-813c8d3f.json` — 12875 KB
- `assets/figures/toretto_multi-d02d37f7.json` — 9708 KB
- `assets/figures/taisa_multi-ffc40e67.json` — 9576 KB
- `assets/figures/diaz_multi-3c5b77b2.json` — 6933 KB
- `assets/figures/geof_multi-8b9748f6.json` — 12717 KB
- `assets/figures/gframe_mk2_multi-27e50520.json` — 10527 KB
- `assets/figures/g_multi__union-55ef7773.json` — 11076 KB
- `assets/figures/z_multi__zeonic-bd518962.json` — 12693 KB
- `assets/figures/z_multi__akai-5a6e01b4.json` — 12693 KB
- `assets/figures/toretto_multi__ground-1c2e9ce9.json` — 9709 KB
- `assets/figures/taisa_multi__zeonic-6dba0785.json` — 9576 KB
- `assets/figures/diaz_multi__black-14688a10.json` — 6933 KB
- `assets/figures/geof_multi__ground-2ec891e1.json` — 12717 KB
- `levels/sk_ms_arena_solo_ground.html` — 4249 KB
- `recipe/sk_ms_arena_solo_ground.json` — 6883 KB
- `levels/sk_ms_arena_solo_city.html` — 3174 KB
- `recipe/sk_ms_arena_solo_city.json` — 4121 KB
- `levels/sk_ms_arena_solo_hangar.html` — 2966 KB
- `recipe/sk_ms_arena_solo_hangar.json` — 2731 KB
- `assets/figures/g_multi-7df780d6.json` — 11111 KB
- `assets/figures/z_multi-c8ba1beb.json` — 12910 KB
- `assets/figures/toretto_multi-8d9b9626.json` — 9732 KB
- `assets/figures/taisa_multi-ea288a17.json` — 9599 KB
- `assets/figures/diaz_multi-4051bfa0.json` — 6960 KB
- `assets/figures/geof_multi-57c5a1f9.json` — 12769 KB
- `assets/figures/gframe_mk2_multi-d9f5b109.json` — 10558 KB
- `assets/figures/g_multi__union-ed90befd.json` — 11111 KB
- `assets/figures/z_multi__zeonic-d7d8e88b.json` — 12729 KB
- `assets/figures/z_multi__akai-c3d0d5f0.json` — 12729 KB
- `assets/figures/toretto_multi__ground-e1169217.json` — 9733 KB
- `assets/figures/taisa_multi__zeonic-94679cab.json` — 9599 KB
- `assets/figures/diaz_multi__black-798b4313.json` — 6960 KB
- `assets/figures/geof_multi__ground-bca7d64a.json` — 12769 KB
- `levels/sk_ms_arena_solo_space.html` — 3187 KB
- `recipe/sk_ms_arena_solo_space.json` — 4197 KB
- `levels/sk_ms_arena_solo_colony.html` — 2596 KB
- `recipe/sk_ms_arena_solo_colony.json` — 1521 KB
- `levels/sk_ms_arena_practice_ground.html` — 4249 KB
- `recipe/sk_ms_arena_practice_ground.json` — 6883 KB
- `levels/sk_ms_arena_practice_city.html` — 3174 KB
- `recipe/sk_ms_arena_practice_city.json` — 4121 KB
- `levels/sk_ms_arena_practice_hangar.html` — 2966 KB
- `recipe/sk_ms_arena_practice_hangar.json` — 2731 KB
- `levels/sk_ms_arena_practice_space.html` — 3187 KB
- `recipe/sk_ms_arena_practice_space.json` — 4197 KB
- `levels/sk_ms_arena_practice_colony.html` — 2596 KB
- `recipe/sk_ms_arena_practice_colony.json` — 1521 KB
- `levels/sk_ms_arena_team_ground.html` — 4269 KB
- `recipe/sk_ms_arena_team_ground.json` — 6936 KB
- `levels/sk_ms_arena_team_city.html` — 3194 KB
- `recipe/sk_ms_arena_team_city.json` — 4175 KB
- `levels/sk_ms_arena_team_hangar.html` — 2986 KB
- `recipe/sk_ms_arena_team_hangar.json` — 2784 KB
- `levels/sk_ms_arena_team_space.html` — 3207 KB
- `recipe/sk_ms_arena_team_space.json` — 4251 KB
- `levels/sk_ms_arena_team_colony.html` — 2616 KB
- `recipe/sk_ms_arena_team_colony.json` — 1575 KB
- `levels/sk_ms_arena_ffa_ground.html` — 4242 KB
- `recipe/sk_ms_arena_ffa_ground.json` — 6862 KB
- `levels/sk_ms_arena_ffa_city.html` — 3167 KB
- `recipe/sk_ms_arena_ffa_city.json` — 4101 KB
- `levels/sk_ms_arena_ffa_hangar.html` — 2959 KB
- `recipe/sk_ms_arena_ffa_hangar.json` — 2711 KB
- `levels/sk_ms_arena_ffa_space.html` — 3180 KB
- `recipe/sk_ms_arena_ffa_space.json` — 4177 KB
- `levels/sk_ms_arena_ffa_colony.html` — 2589 KB
- `recipe/sk_ms_arena_ffa_colony.json` — 1501 KB
- `assets/figures/gframe_mk2_multi-2a0ff071.json` — 10524 KB
- `levels/sk_ms_arena_watch_solo_ground.html` — 4246 KB
- `recipe/sk_ms_arena_watch_solo_ground.json` — 6873 KB
- `levels/sk_ms_arena_watch_solo_city.html` — 3170 KB
- `recipe/sk_ms_arena_watch_solo_city.json` — 4112 KB
- `levels/sk_ms_arena_watch_solo_hangar.html` — 2963 KB
- `recipe/sk_ms_arena_watch_solo_hangar.json` — 2721 KB
- `assets/figures/gframe_mk2_multi-094df0d9.json` — 10554 KB
- `levels/sk_ms_arena_watch_solo_space.html` — 3185 KB
- `recipe/sk_ms_arena_watch_solo_space.json` — 4189 KB
- `levels/sk_ms_arena_watch_solo_colony.html` — 2594 KB
- `recipe/sk_ms_arena_watch_solo_colony.json` — 1513 KB
- `levels/sk_ms_arena_watch_team_ground.html` — 4246 KB
- `recipe/sk_ms_arena_watch_team_ground.json` — 6873 KB
- `levels/sk_ms_arena_watch_team_city.html` — 3171 KB
- `recipe/sk_ms_arena_watch_team_city.json` — 4112 KB
- `levels/sk_ms_arena_watch_team_hangar.html` — 2963 KB
- `recipe/sk_ms_arena_watch_team_hangar.json` — 2721 KB
- `levels/sk_ms_arena_watch_team_space.html` — 3185 KB
- `recipe/sk_ms_arena_watch_team_space.json` — 4189 KB
- `levels/sk_ms_arena_watch_team_colony.html` — 2594 KB
- `recipe/sk_ms_arena_watch_team_colony.json` — 1513 KB
- `levels/sk_ms_arena_watch_ffa_ground.html` — 4244 KB
- `recipe/sk_ms_arena_watch_ffa_ground.json` — 6870 KB
- `levels/sk_ms_arena_watch_ffa_city.html` — 3169 KB
- `recipe/sk_ms_arena_watch_ffa_city.json` — 4109 KB
- `levels/sk_ms_arena_watch_ffa_hangar.html` — 2962 KB
- `recipe/sk_ms_arena_watch_ffa_hangar.json` — 2718 KB
- `levels/sk_ms_arena_watch_ffa_space.html` — 3183 KB
- `recipe/sk_ms_arena_watch_ffa_space.json` — 4186 KB
- `levels/sk_ms_arena_watch_ffa_colony.html` — 2592 KB
- `recipe/sk_ms_arena_watch_ffa_colony.json` — 1510 KB
- `assets/figures/g_federal-2a32a421.json` — 10605 KB
- `assets/figures/g_union-d09d2dc9.json` — 10605 KB
- `assets/figures/z_zeonic-7639af94.json` — 12212 KB
- `assets/figures/z_akai-ad9083d5.json` — 12212 KB
- `assets/figures/t_black-9458a20e.json` — 9375 KB
- `assets/figures/t_ground-29f1ccc5.json` — 9376 KB
- `assets/figures/taisa_akai-7868df4b.json` — 9396 KB
- `assets/figures/taisa_zeonic-6daf9a2a.json` — 9396 KB
- `assets/figures/diaz_akai-4d6d9200.json` — 6646 KB
- `assets/figures/diaz_black-99c2b503.json` — 6646 KB
- `assets/figures/geof_blue-00bc6402.json` — 12144 KB
- `assets/figures/geof_ground-4f959578.json` — 12144 KB
- `levels/menu-sk_ms_hangar.html` — 4279 KB
- `recipe/sk_ms_hangar.json` — 17 KB
- `assets/sk_ms_menu_loop.wav` — 2142 KB
- `assets/sk_qh71f3s3th.wav` — 4755 KB
- `assets/sk_edsk7vhxxb.wav` — 3056 KB
- `assets/sk_qev9kzqz5e.wav` — 6251 KB
- `assets/sk_ernkpg7avf.wav` — 2741 KB
- `assets/sk_p7348t4kaa.wav` — 4531 KB
- `assets/sk_ms_head_unit.png` — 277 KB
- `levels/preview-sk_ms_preview_unit_federal.html` — 14526 KB
- `levels/preview-sk_ms_preview_unit_union.html` — 14526 KB
- `assets/sk_ms_head_z_unit.png` — 371 KB
- `levels/preview-sk_ms_preview_z_unit_zeonic.html` — 16862 KB
- `levels/preview-sk_ms_preview_z_unit_akai.html` — 16862 KB
- `assets/sk_ms_head_t_unit.png` — 459 KB
- `levels/preview-sk_ms_preview_t_unit_black.html` — 13117 KB
- `levels/preview-sk_ms_preview_t_unit_ground.html` — 13117 KB
- `assets/sk_ms_head_taisa_unit.png` — 319 KB
- `levels/preview-sk_ms_preview_taisa_unit_akai.html` — 13364 KB
- `levels/preview-sk_ms_preview_taisa_unit_zeonic.html` — 13364 KB
- `assets/sk_ms_head_d_unit.png` — 236 KB
- `levels/preview-sk_ms_preview_d_unit_akai.html` — 9109 KB
- `levels/preview-sk_ms_preview_d_unit_black.html` — 9109 KB
- `assets/sk_ms_head_geof_unit.png` — 332 KB
- `levels/preview-sk_ms_preview_geof_unit_blue.html` — 15779 KB
- `levels/preview-sk_ms_preview_geof_unit_ground.html` — 15779 KB
- `assets/sk_ms_head_gframe_mk2_unit.png` — 496 KB
- `levels/preview-sk_ms_preview_gframe_mk2_unit.html` — 13957 KB
- `assets/sk_ms_head_unit.png` — 277 KB
- `levels/preview-sk_ms_preview_unit_federal.html` — 14526 KB
- `assets/sk_ms_head_z_unit.png` — 371 KB
- `levels/preview-sk_ms_preview_z_unit_zeonic.html` — 16862 KB
- `assets/sk_ms_head_t_unit.png` — 459 KB
- `levels/preview-sk_ms_preview_t_unit_black.html` — 13117 KB
- `assets/sk_ms_head_taisa_unit.png` — 319 KB
- `levels/preview-sk_ms_preview_taisa_unit_akai.html` — 13364 KB
- `assets/sk_ms_head_d_unit.png` — 236 KB
- `levels/preview-sk_ms_preview_d_unit_akai.html` — 9109 KB
- `assets/sk_ms_head_geof_unit.png` — 332 KB
- `levels/preview-sk_ms_preview_geof_unit_blue.html` — 15779 KB
- `assets/sk_ms_head_gframe_mk2_unit.png` — 496 KB
- `levels/preview-sk_ms_preview_gframe_mk2_unit.html` — 13957 KB
- `assets/sk_ms_head_unit.png` — 277 KB
- `levels/preview-sk_ms_preview_unit_federal.html` — 14526 KB
- `assets/sk_ms_head_z_unit.png` — 371 KB
- `levels/preview-sk_ms_preview_z_unit_zeonic.html` — 16862 KB
- `assets/sk_ms_head_t_unit.png` — 459 KB
- `levels/preview-sk_ms_preview_t_unit_black.html` — 13117 KB
- `assets/sk_ms_head_taisa_unit.png` — 319 KB
- `levels/preview-sk_ms_preview_taisa_unit_akai.html` — 13364 KB
- `assets/sk_ms_head_d_unit.png` — 236 KB
- `levels/preview-sk_ms_preview_d_unit_akai.html` — 9109 KB
- `assets/sk_ms_head_geof_unit.png` — 332 KB
- `levels/preview-sk_ms_preview_geof_unit_blue.html` — 15779 KB
- `assets/sk_ms_head_gframe_mk2_unit.png` — 496 KB
- `levels/preview-sk_ms_preview_gframe_mk2_unit.html` — 13957 KB
