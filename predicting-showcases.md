# Predicting upcoming PokéStop Showcases

How to anticipate which PokéStop Showcase types/species are coming up next, and where
to look. Companion to [`README.md`](./README.md) (scoring) and
[`showcase-types.md`](./showcase-types.md) (formats).

> ⚠️ **Time-sensitive.** The "Showcase Tuesday" cadence, the 10am–8pm window, the
> 20-category pool, and the 5-concurrent limit are **current-season parameters**
> (Memories in Motion / Forever Forward, ~2025–2026) that Niantic changes often —
> not permanent rules. Compiled **2026-06-26**.

---

## TL;DR

You **cannot** learn a specific upcoming showcase's featured species/type from the
game itself in advance — the in-game **Today View** and Leek Duck only reveal the
**current/active** category. But:

- **Timing is highly predictable:** "**Showcase Tuesday**," every Tuesday 10am–8pm local.
- **Location is predictable:** same designated PokéStops all Season.
- **The category pool is bounded:** up to **5 concurrent** categories from a fixed
  pool of **20** (the 18 types + Good Buddy + Great Buddy).
- **Species correlate with concurrent in-game events** — reading the event calendar
  is the strongest species-level predictor.
- **Cannot be data-mined** for specific upcoming species — the Game Master holds only
  generic mechanics.

So: predict from **Niantic's event calendar + community trackers**, not from the game
or the datamine.

---

## Predictable vs. not

| Dimension | Predictable? | How / source |
|-----------|:---:|------|
| Day & time | ✅ very | "Showcase Tuesday" — every Tue, 10am–8pm local |
| Location | ✅ yes | Same designated PokéStops all Season (blue icon → purple after entry) |
| Category pool | ✅ bounded | Up to 5 concurrent from a fixed 20 (18 types + Good/Great Buddy) |
| Specific weekly category/species | ⚠️ partial | Trackers/announcements, usually days ahead; event-correlated |
| From the datamine | ❌ no | Game Master has only generic `CONTEST_SETTINGS` mechanics |

---

## 1. Where upcoming showcases are listed

- **In-game (Today View):** shows only the **current/active** showcase and your
  ranking — *no advance schedule*. (Niantic Help Center.)
- **Leek Duck:** lists the ~20 possible category buckets but says *"Log in to find out
  which Pokémon you can show off!"* — does **not** name per-Tuesday species ahead.
- **Best advance sources** (often days ahead):
  - **Nintendo Wire** — dated weekly *"Showcase Tuesday for [date]"* columns that
    enumerate that week's active categories.
  - **Dexerto** — running showcase schedule.
  - **Pokémon GO Hub**, **Sportskeeda**, **Fandom wiki** — corroborating per-week lists.
  - **Niantic seasonal blog** ("Welcome to Memories in Motion") — establishes the cadence.

---

## 2. Do showcases follow current events? **Yes — the key species predictor**

Featured species/types are **drawn from / launch alongside** the concurrent in-game
event, so reading the current event calendar (anniversaries, Community Days, special
events) is the strongest species-level predictor.

Concrete historical examples:

- **Inaugural:** **Squirtle (#007)** during the **7th Anniversary Party**
  (July 6–12, 2023) — a deliberate "007 for the 7th" tie-in.
- **Community Day tie-in:** **Sobble / Inteleon** showcase coinciding exactly with the
  **Sobble Community Day** (July 4, 2026; matching the 2–5pm window).
- Niantic's Help Center states eligible Pokémon are chosen from the current event and
  change per event.

**Important nuance (verification flagged this):** the *strong* claim — "species are
**restricted** to the current event's roster" — was **refuted** (votes 0-3 and 1-2)
because no official page literally states a hard restriction. The **durable, verified**
version is the weaker one: featured species are **drawn from / launch alongside**
concurrent events. Treat it as a strong correlation, not a guaranteed rule.

---

## 3. Cadence

Fixed **weekly Tuesday** cadence ("Showcase Tuesday"), **10am–8pm local time** as of
the current seasons.

Caveats — this is **season-structural, not permanent**. Niantic has changed it
repeatedly:

- Timing window updated to 10am–8pm on **2026-03-10**.
- Max concurrent entries raised **3 → 5** on **2026-06-02**.
- Early (2023) showcases were event-tied across **assorted days** before the Tuesday
  cadence was formalized.

---

## 4. The fixed 20-category pool

Each Showcase Tuesday draws **up to five active categories** from a fixed pool of **20**:

- **Good Buddy or higher**
- **Great Buddy or higher**
- **All 18 Pokémon types** (Normal, Fire, Water, Grass, Electric, Ice, Fighting,
  Poison, Ground, Flying, Psychic, Bug, Rock, Ghost, Dragon, Dark, Steel, Fairy)

Concrete example: **Tuesday June 9, 2026** ran **Ghost / Psychic / Dark** types plus
**Good Buddy** and **Great Buddy** simultaneously.

Caveat: this bounded weekly format is the **current-season** structure;
**special-event** showcases still feature specific species **outside** this pool.

---

## 5. Can upcoming showcases be data-mined? **No**

Direct inspection of the **PokeMiners** Game Master (`latest.json`, 18,152 templates,
2026-06-26): the only showcase-related template is **`CONTEST_SETTINGS`**, which holds
**generic mechanics only** — height/weight/IV scoring coefficients,
`playerContestMaxEntries`, warmup/cooldown, length thresholds, feature flags. There is
**no per-event featured-species/type schedule, listing, or prediction**.

Per-event featured species are delivered **server/event-side**, not in the Game Master.
Practical implication: trackers predict upcoming showcases from **Niantic's published
event calendar**, not from the datamine.

---

## 6. Selection patterns (how Niantic picks)

- **Event tie-ins** (anniversaries, Community Days, special events) — strongest driver.
- **Type / buddy-level rotation** within the 20-pool each Tuesday.
- **New-release / seasonal-theme** alignment.
- The exact within-pool rotation **algorithm is not documented** (see open questions).

---

## Claims refuted during verification (7 killed — a skeptical pass)

- ❌ Multiple **conflicting time-windows** scraped by trackers — 12am–11:59am (0-3),
  8am–12pm (0-3), "next Tuesday only" framings (0-3). The verified window is
  **10am–8pm local**.
- ❌ "Eligible species are **restricted** to the current event's roster" — refuted
  **0-3** (announcement post) and **1-2** (weaker rewording). The correlation survives;
  the hard restriction does not.
- ❌ A Dec-2023 Sportskeeda framing of type/buddy rotation — refuted **1-2** on sourcing.

---

## Open questions

- How early are the **specific five categories** confirmed each week — seasonal blog,
  weekly, or only via in-game datapush on the day?
- Does Niantic ever pre-announce a **full season's** category rotation (enabling
  species-level prediction weeks out), or are categories decided per-week?
- For **special-event** (non-Tuesday) showcases, is there any verbatim official
  statement that species are strictly limited to the event roster, or only a pattern?
- What drives **type/category selection** within the 20-pool — an observable rotation
  algorithm, seasonal-theme weighting, or new-release promotion bias?

---

## Sources

| # | Source | Type |
|---|--------|------|
| 1 | [Niantic — Welcome to Memories in Motion (Showcase Tuesday)](https://pokemongo.com/news/welcome-to-memories-in-motion) | **primary** |
| 2 | [Niantic — PokéStop Showcase announcement](https://pokemongo.com/en/post/pokestop-showcase-new-feature) | **primary** |
| 3 | [Niantic Help Center — What is a PokéStop Showcase](https://niantic.helpshift.com/hc/en/6-pokemon-go/faq/4142-what-is-a-pokestop-showcase-and-how-can-i-be-featured/) | **primary** (FAQ) |
| 4 | [Niantic — July 2026 Sobble Community Day](https://pokemongo.com/news/communityday-july-2026-sobble) | **primary** |
| 5 | [PokeMiners — game_masters repo](https://github.com/PokeMiners/game_masters) | primary (datamine substrate) |
| 6 | [Nintendo Wire — Showcase Tuesday for June 23rd, 2026](https://nintendowire.com/guides/pokemon-go/showcase-tuesday-for-june-23rd-2026/) | secondary |
| 7 | [Nintendo Wire — Showcase Tuesday for June 9th, 2026](https://nintendowire.com/guides/pokemon-go/showcase-tuesday-for-june-9th-2026/) | secondary |
| 8 | [Dexerto — PokéStop Showcase schedule](https://www.dexerto.com/pokemon/pokemon-go-pokestop-showcase-schedule-2312673/) | secondary |
| 9 | [Pokémon GO Hub — June 2026 events](https://pokemongohub.net/post/event/june-2026-pokemon-go-events/) | secondary |
| 10 | [Fandom — PokéStop Showcase](https://pokemongo.fandom.com/wiki/Pok%C3%A9Stop_Showcase) | secondary |
| 11 | [Leek Duck — Showcase Tuesday](https://leekduck.com/events/pokemon-showcase-tuesday/) | secondary |
| 12 | [Leek Duck — July Community Day 2026](https://leekduck.com/events/july-communityday2026/) | secondary |
| 13 | [Sportskeeda — Showcase dates & featured Pokémon](https://www.sportskeeda.com/pokemon/pokemon-go-pokestop-showcase-december-2023-all-dates-featured-pokemon) | secondary |
| 14 | [GameRant — PokéStop Showcases](https://gamerant.com/pokemon-go-pokestop-showcases/) | secondary |
