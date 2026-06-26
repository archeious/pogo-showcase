# Types of PokéStop Showcases

A catalog of every PokéStop Showcase format in Pokémon GO, what each ranks by, and
how scoring works across them. Companion to [`README.md`](./README.md), which covers
the "biggest size" scoring formula in depth.

> ⚠️ Same caveat as the README: scoring internals are **community-reverse-engineered**,
> not officially published by Niantic. Pokémon GO Hub notes observed scores have been
> "erratic and unpredictable," so treat numbers as a well-corroborated approximation.
> Compiled **2026-06-26**.

---

## TL;DR

Showcase **types are defined by their *entry criterion*** (which Pokémon may enter),
**not** by a different scoring metric. **Every showcase in the feature's entire
history has ranked by "biggest" size.** There has never been a smallest/XXS,
CP-based, IV-based, or otherwise stat-based showcase.

---

## The three showcase formats

| Format | Who can enter | Scoring metric |
|--------|---------------|----------------|
| **Single-species** | One species only (e.g. Squirtle) | Biggest-size composite (see README) |
| **Multi-species / all-type** | Any Pokémon of a whole typing (e.g. all Fairy-, Dragon-, Normal-types) | Biggest-size, **relative within species** since 2024-09-16 |
| **Buddy-status** | Any Pokémon at/above a buddy level (Great / Ultra / Best Buddy) | Biggest-size; only the entry *filter* differs |

Common to all: timed contests at select PokéStops, leaderboard ranking, **up to 50
entries** per showcase, eligibility rotates per event, weekly (Tuesday) cadence as of
June 2026.

### Single-species
The original/inaugural format. Debuted in the **7th Anniversary Party (Squirtle,
July 6–12, 2023)** — "enter Squirtle… to see whose Pokémon is the biggest." Placement
shown as a 1–3 star rating. Scored by the composite height/weight/IV formula in the
README. **Unaffected** by the September 2024 change.

### Multi-species / all-type
Introduced so an entire typing can compete in one category (e.g. all Fairy-types, all
Dragon-types). Examples: Fairy-type (2024-01-13), Dragon-type (2024-02-08), combined
Fighting/Fairy (2024-09-30). See the September 2024 change below — this is the format
it affected.

### Buddy-status
Filters entries by **buddy level** rather than species: e.g. "Ultra Buddy or Best
Buddy" (2024-07-22), "Great Buddy or Higher" (2025-08-12). Thresholds vary per
instance; recurring. Trainers below the required buddy status **cannot enter at all**.
Scoring is still the standard size formula — only the entry filter differs.

---

## The pivotal change: relative-size scoring (2024-09-16)

The single most important mechanical inflection point. **Applies only to all-type /
multi-species showcases — single-species showcases are unaffected.**

- **Before (historical):** every entrant was judged on **one shared absolute-size
  scale**, anchored to a single (often undisclosed) reference species. Naturally large
  rare species dominated — e.g. a **Celesteela** in a Flying-type showcase hugely
  outclassed a **Pidgey**, so the *species*, not your specimen, effectively dictated
  the winner.
- **After (current):** debuting with the **Normal-type showcase (Sept 16–18, 2024)**,
  each Pokémon is judged by its **relative size *within its own species***. Overall
  absolute size no longer matters, so **any XXL specimen becomes competitive** — an
  XXL Pidgey can beat a Celesteela; the largest XXL Rattata outscores an average
  Snorlax. Ranking is by the "points bigger than others of its species" margin (e.g.
  a Skitty 10 points bigger than other Skitty beats a Regigigas only 9 points bigger
  than other Regigigas).
- Still in effect as of June 2026.

---

## Does a "smallest / XXS" showcase exist?

**No.** Despite being teased in launch marketing (the "smallest Charmander" example),
a smallest/XXS-favoring showcase has **never run** — confirmed as of June 2024 and
still through the June 2026 search window. **No showcase inverts the formula to reward
XXS.** Fandom wiki: *"Currently, there is only one criteria used for judging
Showcases: Biggest Size."*

(A low-quality 2026 SEO article claiming showcases "sometimes judge by smallest size"
is uncorroborated and was treated as unreliable.)

---

## Scoring recap (all size-based)

`Score = (ScaledHeight × 800) + (ScaledWeight × 150) + (IVSum/45 × 50) + XXL_bonus`

Height ~80%, weight ~15%, IVs ~5%, flat **+178** for XXL. Full breakdown, worked
examples, and normalization details are in [`README.md`](./README.md).

---

## Rewards & medals (tiered by placement)

| Tier | Reward |
|------|--------|
| All participants | Stardust, XP, and more |
| Top 3 | Items — Incubator, Star Piece, and more |
| 1st place | **Showcase Star medal** (levels at cumulative wins: 1 / 10 / 50 / 100) |

---

## Claims refuted during verification

- ❌ **"Type showcases pick one of two scoring systems (server-chosen baseline species
  vs each entrant's own standard form)."** — Killed **1-2**. A garbled/superseded
  description of the real pre/post-Sept-2024 mechanic.
- ❌ A **duplicate** single-species formula-breakdown claim — killed **0-3** on a vote
  technicality; the formula itself is confirmed via other sources (see README).

---

## Open questions

- **No CP/IV/stat-based format was found** — but the absence is inferred, not stated
  by a primary source.
- Whether other **seasonal/event-specific formats** exist beyond single-species,
  all-type, and buddy-status (costume / regional / legendary-themed, etc.). Species
  rotate per event, but no distinct extra format was enumerated.
- The **precise** post-Sept-2024 within-species normalization, and whether the +178
  XXL bonus still applies under per-species scaling in type showcases.
- Whether Niantic will ever implement the originally-teased **smallest/XXS** condition
  (no official roadmap statement found).

---

## Sources

| # | Source | Type |
|---|--------|------|
| 1 | [Niantic — PokéStop Showcase announcement](https://pokemongo.com/post/pokestop-showcase-new-feature?hl=en) | **primary** |
| 2 | [Niantic — Showcase updates (Pikachu 2024, all-type)](https://pokemongo.com/post/pokestop-showcase-updates-pikachu-2024?hl=en) | **primary** |
| 3 | [Pokémon GO Hub — Major changes made to PokéStop Showcases](https://pokemongohub.net/post/news/major-changes-made-to-pokestop-showcases/) | secondary |
| 4 | [Pokémon GO Hub — Showcase Scores, XXS and XXL](https://pokemongohub.net/post/research/showcase-scores-xxs-and-xxl-pokemon-and-how-it-works/) | secondary |
| 5 | [esports.gg — Niantic introduces big change to Showcases](https://esports.gg/news/pokemon/niantic-introduces-big-change-to-pokestop-showcases/) | secondary |
| 6 | [Dexerto — What are PokéStop Showcases](https://www.dexerto.com/pokemon/what-are-pokestop-showcases-in-pokemon-go-2201728/) | secondary |
| 7 | [GameRant — PokéStop Showcases guide & rewards](https://gamerant.com/pokemon-go-pokestop-showcases-guide-rewards/) | secondary |
| 8 | [Sportskeeda — players comment on latest showcase](https://www.sportskeeda.com/pokemon/they-remove-elemental-contests-size-pokemon-go-player-comments-latest-pokestop-showcase) | secondary |
| 9 | [Fandom — PokéStop Showcase](https://pokemongo.fandom.com/wiki/Pok%C3%A9Stop_Showcase) | secondary |
| 10 | [pokemondb.net — Showcase calculator](https://pokemondb.net/go/showcases) | secondary |
| 11 | [pokexperience.com — Showcase calculator](https://pokexperience.com/showcase/) | blog |
| 12 | [Leek Duck — events (showcase schedule)](https://leekduck.com/events/) | secondary |
| 13 | [Leek Duck — Normal-type showcase 2024-09-16](https://leekduck.com/events/pokemon-showcase-normal-type-2024-09-16/) | secondary |
| 14 | [Leek Duck — Ultra/Best Buddy showcase 2024-07-22](https://leekduck.com/events/pokemon-showcase-ultra-buddy-or-higher-2024-07-22/) | secondary |
| 15 | [Leek Duck — Great Buddy or Higher showcase 2025-08-12](https://leekduck.com/events/pokemon-showcase-great-buddy-or-higher-2025-08-12/) | secondary |
