# pogo-showcase

Reverse-engineered mechanics of Pokémon GO **PokéStop Showcases**, focused on how
points are calculated for **"The Biggest"** (size-based) single-species showcases.

> ⚠️ **None of this is officially published by Niantic.** Everything here is
> community-data-mined from the game master file and from in-game observation,
> then cross-checked. It is multiply corroborated and embedded in working
> third-party calculators, but treat exact constants as reverse-engineered, not
> authoritative. Findings compiled **2026-06-26**.

> 📚 See also:
> - **[`showcase-types.md`](./showcase-types.md)** — catalog of every showcase *format*
>   (single-species, all-type, buddy-status), the pivotal Sept 2024 relative-size
>   change, rewards/medals, and why no "smallest/XXS" showcase exists.
> - **[`predicting-showcases.md`](./predicting-showcases.md)** — how to anticipate
>   *upcoming* showcases: the weekly "Showcase Tuesday" cadence, the fixed 20-category
>   pool, event tie-ins, and why they can't be data-mined in advance.
> - **[`upcoming-likelihood.md`](./upcoming-likelihood.md)** — a *speculative* ordered
>   most→least-likely list for upcoming showcases (snapshot 2026-06-26), reasoned from
>   the current season, event calendar, and spawn pools.

---

## TL;DR

For a single-species **"The Biggest"** showcase, your score comes from exactly
**three inputs — Height, Weight, and IVs** — plus a flat bonus if your Pokémon is
**XXL**. **CP is not a factor at all.**

```
score = (ScaledHeight × 800) + (ScaledWeight × 150) + (ScaledIVs × 50) + XXL_bonus
```

| Component  | Max points | Share | Notes                                   |
|------------|-----------:|------:|-----------------------------------------|
| Height     |        800 |  80%  | Dominates the result                    |
| Weight     |        150 |  15%  | Minor; partly derived from height       |
| IVs        |         50 |   5%  | Nearly negligible                       |
| XXL bonus  |       +178 |   —   | Flat, only if classified XXL            |
| **Base max** | **1000** |       | "THOUSANDOS" (perfect non-XXL)          |
| **True max** | **1178** |       | Base + XXL bonus                        |

**Practical upshot:** because of the +178 XXL bonus, **any XXL beats any XL of the
same species** — a **0% IV XXL routinely beats a perfect-IV (hundo) normal-size
specimen.** For "The Biggest," hunting XXL matters far more than IVs or CP.

---

## The formula in detail

Each factor is normalized against a species-specific maximum (landing it on a 0–1
scale) and then multiplied by its point weight.

### Height — 800 pts (80%)

```
((your height / species mean height) / maxHeightClass) × 800
```

- `maxHeightClass` is the species' XXL height ceiling: one of **1.55, 1.75, or 2.00**
  (normalized classes; species-dependent).
- **Worked example (Squirtle):** display height 0.84 m, species mean 0.5 m, class 1.75
  → `((0.84 / 0.5) / 1.75) × 800 = 768 pts`.

### Weight — 150 pts (15%)

```
((your weight / species mean weight) / maxWeightClass) × 150
```

- The weight ceiling is **derived from the height class**:
  `weight = weight_variate + (height − 1)`, with max `weight_variate = 1.5`.
  This gives weight classes **2.05, 2.25, 2.50** paired with height classes
  **1.55, 1.75, 2.00** respectively.
- **Worked example (Squirtle):** weight 16.54 kg, mean 9.0 kg, class 2.25
  → `((16.54 / 9.0) / 2.25) × 150 = 122.5 pts`.

### IVs — 50 pts (5%)

```
(IV_sum / 45) × 50
```

- `IV_sum = Attack + Defense + Stamina` (max 15 each → 45).
- Perfect (15/15/15) → `(45/45) × 50 = 50 pts`. IV-sum of 20 → `22.2 pts`.
- A perfect IV adds only ~4% of the 1178 max — effectively negligible.

### XXL bonus — flat +178 pts

- Awarded only to **XXL-classified** Pokémon; non-XXL gets 0.
- True rational value is **7300/41 ≈ 178.0488**, rounded to 178.
- It is deliberately engineered as the **gap between the best-scoring XL and the
  worst-scoring XXL** (e.g. 1025.41 vs 847.36 for the 1.55 class), per data-miner
  **bmenrigh**. That is what guarantees any XXL outscores any XL of the same species.

---

## What size class (XXS/XS/Standard/XL/XXL) means

- **Size class is driven by HEIGHT, not weight.** It is the same height-based class
  that feeds the **Jumbo / Tiny collector medals**. The XL/XXL tag you see is the
  height tag.
- Weight has its own independent variation, but its tag is **not displayed or
  searchable**, and the weight max is derived from height (see above).
- XXL itself comes in three height classes (1.55 / 1.75 / 2.00 normalized).

---

## Practical notes & gotchas

- **Calculators return a RANGE, not an exact integer.** Scoring uses the precise
  server-side height/weight floats, but the game *displays* rounded height/weight,
  so player-side predictions can be off by a few points (forum example: 712.7
  calculated vs 710 shown; 574.4 vs 572). The IV component is exact (from appraisal).
- Working third-party calculators:
  - <https://pokemondb.net/go/showcases>
  - <https://pokexperience.com/showcase/>
  - <https://charlierose.dev/pokemon/go/sizecalculator.html>

---

## Scope & time-sensitivity

- This formula is specifically for **single-species "The Biggest" showcases.**
- A Niantic update around **2024-09-16** changed **multi-species / all-type**
  showcases to rank by **relative size within each species** — a different mechanic
  not fully documented here.
- The inaugural showcase (7th Anniversary, **July 2023**) was size-based, using
  Squirtle, ranking "whose Pokémon is the biggest."

---

## Claims that were REFUTED during verification

Listed so they don't mislead you elsewhere (each killed by adversarial 3-vote review):

- ❌ **"Size categories come from fixed multipliers (XXS=0.5×, XS=0.75×, Standard=1×,
  XL=1.25×, XXL=1.5×)."** — Killed **0-3**. Common but wrong simplification.
- ❌ **"IVs don't factor into the score at all."** — Killed **0-3**. They *do* factor,
  just minimally (the 5% / 50-pt slice).
- ❌ **"XXL = height ≥ exactly 1.5× base height."** — Weakly supported, killed **1-2**.
  The exact XL→XXL boundary was not firmly established.

---

## Open questions (not resolved by available sources)

- **Tie-breaking:** how are identical scores resolved? (catch time? exact float
  ordering? IV?) No source addressed this.
- The **exact numeric XXL height threshold** (the XL vs XXL boundary).
- A complete published **species → height/weight class lookup table** and how a
  species is assigned to its class.
- How the **September 2024** per-species relative-size update changed multi-type
  showcase scoring specifically.

---

## Methodology

Compiled via a deep-research harness: question decomposed into 5 search angles
(broad, mechanic, data-mined, practitioner, contrarian), parallel web searches,
12 sources fetched and de-duplicated, 50 falsifiable claims extracted, 25
adversarially verified by a 3-vote panel (≥2/3 refutations kill a claim). Result:
**22 confirmed, 3 killed.**

Attribution for the original decoding traces to data-miners **bmenrigh, sellyme,
minibenoit, and LemmoritoSensei**, plus Reddit user **u/FatalisticFeline-47**
(evolution-size/score spreadsheet).

---

## Sources

| # | Source | Type |
|---|--------|------|
| 1 | [Pokémon GO Hub — Showcase Scores, XXS and XXL Pokémon and How it Works](https://pokemongohub.net/post/research/showcase-scores-xxs-and-xxl-pokemon-and-how-it-works/) | secondary (primary data-mined writeup) |
| 2 | [pokemondb.net — Showcase calculator](https://pokemondb.net/go/showcases) | secondary (calculator) |
| 3 | [Fandom — PokéStop Showcase](https://pokemongo.fandom.com/wiki/Pok%C3%A9Stop_Showcase) | secondary |
| 4 | [Fandom — Weight and Height](https://pokemongo.fandom.com/wiki/Weight_and_Height) | secondary |
| 5 | [Future Game Releases — Showcases Scoring System Deciphered](https://www.futuregamereleases.com/2023/07/pokemon-go-showcases-scoring-system-successfully-deciphered-shorter-pokemon-receive-lower-scores/) | secondary |
| 6 | [Pokémon GO Hub forum — Showcase Scores thread](https://forum.pokemongohub.net/t/55-showcase-scores/29074) | forum |
| 7 | [pokexperience.com — Showcase](https://pokexperience.com/showcase/) | blog (calculator) |
| 8 | [charlierose.dev — Size calculator](https://charlierose.dev/pokemon/go/sizecalculator.html) | blog (calculator) |
| 9 | [Niantic — PokéStop Showcase announcement](https://pokemongo.com/post/pokestop-showcase-new-feature?hl=en) | **primary** (inaugural showcase only) |
| 10 | [bmenrigh on X — +178 XXL fixed-points explanation](https://x.com/bmenrigh_pogo/status/1718927008736927980) | primary data-miner (X post) |
| 11 | [Bulbapedia — Size and weight variation](https://bulbapedia.bulbagarden.net/wiki/Size_and_weight_variation) | secondary |
| 12 | [thephrasemaker.com — How to win type-based showcases](https://thephrasemaker.com/2026/03/10/how-to-win-type-based-pokemon-go-showcase/) | blog |

> Of these, only the Niantic announcement (#9) is a first-party source, and it
> covers only the existence/format of the inaugural showcase — not the scoring
> math. All scoring constants are reverse-engineered.
