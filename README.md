# Mishika's World Explorer — Countries

**Play (live, v1 on main):** https://akshay-hw-notebook.github.io/mishika-countries-game/
**This branch (`redesign/world-explorer-v2`) is NOT live. Do not merge — awaiting Akshay review + Grok Bot review.**

## Point of view
Mishika is a young explorer with a real passport, travelling a real world map.
It should feel like a travel adventure — warm and crafted, not a pink quiz template.
She is the explorer and the expert — not a child being tested.

## v2 redesign (this branch)
- Every round starts on the full world map with the target glowing, then zooms smoothly (~900ms) to the framed country (neighbours visible), with a persistent corner mini-map ("You are here" dot). Zooms back out before the next round. `prefers-reduced-motion` gets instant cuts.
- Highlight rebuilt: solid magenta fill, white outline scaled to the view, gentle pulse on the fill only. No glow blob, halo rings or giant pin; a small anchored dot scales with the country (tiny countries like Sri Lanka stay readable).
- Design system: Fredoka + Nunito (Google Fonts with strong system fallbacks; game still works offline / from `file://` if fonts fail), CSS vars (ink navy, teal, coral, magenta target), inline SVG icons instead of emoji headings, one button system.
- DISCOVERED stamp moment on every correct answer, with a more faithful flag, capital and wow fact in larger type. Sound on by default (WebAudio tones) with a visible mute toggle that persists.
- Persistent Passport (separate `mishika_passport_v1` key, migrated from existing stats): stamps grid, discovered/mastered counts, star HUD, round dots 1–10, new stamps shown on the end screen.
- Grown-ups (parent thumbs, strong/wobbly lists, copy learning data) moved behind a "Grown-ups" button/modal, out of the kid flow. Wrong-answer lines rewritten in Grade-4 explorer voice. Pico the Parrot has a face (inline SVG) and a named speech bubble; catching him is celebrated.
- **Bug fixed — always 4 choices:** the old picker took 2 same-continent + 1 other; Oceania (Australia/New Zealand) and Europe-Asia (Russia/Turkey) have only one same-continent peer in the 31-country set, so those rounds showed only 3 choices (this is what Fo saw). The picker now fills to 3 distractors from the whole pool.

Preserved from v1: learning engine and data keys (`mishika_country_stats_v1`, `mishika_playtime_v1`, `mishika_log_queue_v1` offline queue, MishikaLog events), spaced/weighted practice (wobbly 6×, strong 0.7×), hints after misses, re-visit ~3 rounds later, Catch-Pico rounds 5 and 9, curiosity capital/flag/fact, worked example first (India on the world, then zoom).

## How to play together (for Akshay)
Sit beside her for one 10-country trip and let her be the expert. Lines that work:
"Pico sounds very sure. Is he?" • "Catch him if he is wrong!" • "Tell me one wow fact you remember."
One yes/no check: does she ask for it again on day three without prompting?

## Test (branch build only, not deployed)
Playwright, local server on the branch file: desktop 1280, phone 390, tablet 820 — full 10-round sessions, 4 choices asserted every round, 2 catch rounds, zero console/page errors, log queue + stats + passport persist across reload. Screenshots are local files in the source mirror: `/workspace/mishika/countries/screenshots/v2-*.png` (including `v2-shape-{nzl,rus,fra,lka}-zoom.png`).
