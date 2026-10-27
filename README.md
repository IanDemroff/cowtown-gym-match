# Cowtown Gym Match

A web app that helps people who just moved to Fort Worth find a gym that fits how they train, discover gyms near their new place, and plan tours. Built for the W524 EAP project (see `EAP_Proposal_IanDemroff.docx`).

**Live site:** https://YOUR-GITHUB-USERNAME.github.io/cowtown-gym-match/ (works after GitHub Pages is turned on, see DEPLOY.md)

## What is in this repository

| Path | What it is |
|---|---|
| `index.html` | The app (map version). This is the page the website opens. |
| `vendor/leaflet/` | Map library the app needs. Keep it next to `index.html`. |
| `classic/index.html` | The first version of the app, without the live map. Opens at `/classic/`. |
| `agent.md` | Matching rules and gym dossier schema. Source of truth for scoring. |
| `journal.md` | Weekly build and outreach log for the EAP. |
| `AGENTS.md` | Standing rules for any AI assistant working on this project. |
| `docs/skills/` | Claude skills for the project (journal, principles, memo, dossier). |
| `docs/coursework/` | EAP proposal and check-in memo (Word). |
| `DEPLOY.md` | Step-by-step: put this on GitHub and turn on the website. |
| `.nojekyll`, `.gitignore` | Housekeeping files for GitHub. Leave them in. |

This is a static website (HTML and JavaScript). It has no Python, no server, no database, and no API keys, so there are no secrets to configure.

## Run it on your own computer

Double-click `index.html`, or for device location to work, run a small local server from this folder:

```
python -m http.server 8000
```

Then open http://localhost:8000.

## What a gym goer does with it

1. **Take the quiz** (16 quick either-or questions) to get a training vibe profile.
2. **Set where they'll train from**: "Use my location", type a new address or office, pick a Fort Worth area, or drop a pin on the map.
3. **Set limits**: max distance, monthly budget, 24/7 access.
4. **Matches tab**: rated Fort Worth gyms ranked by vibe match, with "why it fits", "watch for", price, hours, distance, directions, and tour questions.
5. **Map tab**: live map with your start point (drag the yellow diamond), a ring for your max distance, numbered matches, and other gyms nearby.
6. **Nearby tab**: every gym, CrossFit box, studio, boxing gym, climbing gym, and sauna OpenStreetMap lists around you, including ones not rated yet. Filter by type or 24/7, sort by distance or match, get directions, call, or ask for a rating.
7. **Saved tab**: a tour plan. Tick off questions on the tour, write notes, record the tour date, and rate how it felt. Then "Copy my summary" to send feedback.

Everything a user saves stays in their own browser (localStorage). Nothing is sent to a server except map tiles, address lookups, and the nearby-gym search.

## Free services used (no accounts or API keys)

| What | Service |
|---|---|
| Map library | Leaflet 1.9.4 (bundled in `vendor/leaflet`) |
| Map tiles | CARTO basemaps, OpenStreetMap data |
| Address search | Nominatim (OpenStreetMap) |
| Nearby gyms | Overpass API (OpenStreetMap) |
| Your location | The browser's built-in geolocation |

These free services have fair-use limits, which are fine for a prototype and a few hundred testers.

## Where things live in the code

- `index.html`, script `core`: quiz questions, the 14 gym dossiers (`GYMS`), Fort Worth areas, and scoring. Same rules as `agent.md`.
- `index.html`, script `geo`: OpenStreetMap search, gym-type classification, and matching OSM gyms to dossiers.
- The last script: the screens (tabs, map, nearby list, tour planner, feedback summary).

To add a gym dossier, copy one entry in `GYMS` and edit it. "Rate this gym for me" requests in feedback summaries show which gyms people want added.

## Known limits

- Vibe scores, prices, and hours are web research, not yet checked in person.
- Dossier map positions were placed by hand and can be off by a few blocks.
- Distances are straight-line miles; drive times are rough estimates.
- Location can be blocked when the page is opened inside some previews. Opening it from a local server or a hosted URL fixes that.
