# Cowtown Gym Match: agent definition

Working name for the W524 EAP project. This file is the source of truth for how the matching agent thinks. `index.html` implements it. Change the rules here first, then the code.

## Job

Help someone new to Fort Worth pick a gym by training style and atmosphere, not by proximity alone. Output a ranked shortlist with reasons a person can check on a tour.

## Inputs

1. **Vibe profile** from the 16-question forced-choice quiz.
2. **Start point**: device location, a chosen area, or a pin dropped on the map.
3. **Hard limits**: max distance, monthly budget, 24/7 access.
4. **Gym dossiers** (below).

## The six dimensions

| Dimension | Type | Low end (0) | High end (1) |
|---|---|---|---|
| Visibility | axis | Private | Camera-friendly |
| Energy | axis | Quiet, focused | Loud, high-energy |
| Structure | axis | Open floor | Coached classes |
| Social style | axis | Solo | Community |
| Training focus | weights | strength, functional, conditioning, recovery | |
| Identity | weights | physique, performance, wellness | |

Quiz mapping: three A/B questions per axis, so each axis lands on 0, 0.33, 0.67, or 1. Training focus is a first pick (0.65) and a second pick (0.35). Identity is two three-way questions at 0.5 each.

## Scoring

- Axis fit = `1 - |user - gym|`.
- Focus fit and identity fit = sum of `user weight x gym score`.
- Axis weight = `0.4 + 1.2 x |user - 0.5|`. A strong lean counts more than a split answer. Identity weight is 0.8.
- Base = weighted mean of the four axis fits and identity fit.
- **Score = base x (0.45 + 0.55 x focus fit).** Focus scales everything, so a gym that cannot train you the way you want cannot win on mood alone. An earlier additive version ranked Planet Fitness first for a quiet powerlifter, which is why this changed.
- Hard limits never change the score. A gym that breaks a limit moves to a separate "fits your vibe, breaks a limit" list with the reason shown.
- If the best score is under 60, say plainly that nothing in the set is a strong match.

## Explanation rules

- "Why it fits": up to three dimensions with fit of 0.62 or more, ordered by fit x weight. Show the dossier note for each.
- "Watch for": up to two dimensions with fit under 0.5 that the user cares about (weight 0.6 or more).
- Every claim shown to a user must trace to a dossier note. No invented amenities, prices, or policies.
- Every card says whether the dossier is web research or visited.

## Claude layer

Where the viewer has Claude available, an "Ask the matching agent" box sends the profile, limits, model ranking, and all dossiers to Claude with these standing rules: use only the dossiers, respect limits, flag what to confirm on a tour, name one gym to tour first, plain text, under 170 words. The deterministic ranking still decides order. Claude explains trade-offs and answers follow-ups ("I train at 5am").

## Dossier schema

```
id, name, cat, kind (gym | recovery), addr, lat, lon,
price (number or null), priceNote, h24 (true | false | null), hours,
vis, energy, structure, social            # 0..1
focus {s, f, c, r}, aes {phys, perf, well} # 0..1 each
notes {vis, energy, structure, social, focus, aes}  # one sentence each, evidence-based
ask [ ... ]        # questions for a tour
site, src [ ... ]  # where the facts came from
dayPass (optional)
```

Planned additions after Week 2 visits: `verified` (date visited), `filmingPolicy` (quoted), `peakCrowd`, `contractTerms`.

## Current dossier set (14, all web-seeded on 2026-10-10)

Premium and hardcore strength: Absolute Recomp Fort Worth, Gym Evolution, Strong Performance Co.
Small-group and neighborhood: Forged Fitness, Pop's Gym.
Functional: CrossFit Panther City, CrossFit Iron Horse.
Class-based: Body Machine Fitness, SPENGA Fort Worth.
High-end: Life Time Fort Worth-Alliance.
Big-box: EoS Fitness Altamesa, Planet Fitness Wedgwood.
Recovery: SweatHouz Camp Bowie, City Cave Near Southside.

## Known weak spots

- Vibe scores are my first estimates from websites, press, and reviews. Nobody has walked into these gyms yet.
- Map coordinates were placed by hand from street addresses. Geocode them before anyone relies on distances.
- Several prices and hours are unconfirmed and marked that way in the app.
- No quiet, serious barbell gym is in the set, so that profile tops out under 50%. Fort Worth Barbell is the obvious add once its address is confirmed.
