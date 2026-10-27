# EAP Project journal

## 2026-10-10 (Week 1): first working prototype

**Built**
- `index.html`: single-file web app. 16-question forced-choice quiz, vibe profile, location (device location, area picker, or map pin), hard limits (distance, budget, 24/7), ranked match cards with "why it fits" and "watch for", tour questions per gym, shortlist, schematic map, and a copyable feedback summary.
- `agent.md`: dimensions, scoring rules, dossier schema.
- 14 dossiers seeded from web research across all six categories in the proposal.

**Decisions**
- Scoring is deterministic and Claude explains it, so the same answers always give the same ranking and every reason traces to a dossier note.
- Training focus multiplies the score. The first additive version put Planet Fitness on top for a quiet powerlifter.
- Limits never hide a gym. They move it to a second list with the reason, because a newcomer may still be choosing where to live.
- No backend yet. Usage tracking for the passive and active phases runs through the "Copy my summary" box, which captures profile, top 3, votes, how they found the tool, and willingness to pay.

**Tested**
- Five personas through the scoring model: physique lifter gets Absolute Recomp (72%), CrossFit-style gets Panther City and Iron Horse (82%, 79%), recovery gets SweatHouz and City Cave, class cardio gets Body Machine. Quiet barbell purist tops out at 47%, which is a gap in the gym set and not a bug.
- Page loads and the quiz completes with no script errors at desktop and phone width.

**Not verified**
- Vibe scores (estimates), map coordinates (hand-placed), several prices and hours.
- Whether device location works depends on where the page is opened. It is blocked inside the Claude artifact viewer and works when `index.html` is opened directly or hosted.

**Next**
- [ ] Customer discovery conversations (5 or more newcomers): is this a real problem, and would they pay?
- [ ] Geocode all 14 addresses and replace the hand-placed coordinates.
- [ ] Add Fort Worth Barbell and one more quiet strength gym.
- [ ] Week 2 visits: start with Absolute Recomp, one CrossFit box, one big-box. Record filming policy, noise, crowding, and correct the scores.
- [ ] Decide where to host for the passive launch, and whether to add real usage logging.
- [ ] Pick the gym for the referral pitch.

## Outreach log

| Date | Phase | Channel | Who | Result |
|---|---|---|---|---|
| | | | | |

## Feedback log (paste summaries here)


## 2026-10-10 (Week 1): app build with geolocation

**Built** `cowtown-gym-match/` (open `index.html`, see its README)
- Live map (Leaflet + OpenStreetMap tiles) replaces the schematic map. Draggable start pin, distance ring, numbered matches.
- Start point from device location, typed address (Nominatim), area picker, or dropped pin.
- Nearby tab: every gym OpenStreetMap lists within the max distance (Overpass), typed as gym, CrossFit, studio, combat, climbing, or recovery. Private apartment gyms are hidden. Gyms that match a dossier show the vibe score; others get "Rate this gym for me", which lands in the feedback summary as demand for new dossiers.
- Saved tab: tour plan with checklist, notes, tour date, and a 1 to 5 fit rating.

**Tested** with mocked map and OpenStreetMap responses at desktop and phone width: quiz, location, address search, nearby list and filters, map pins and popups, saving, tour notes surviving a reload, summary copy. No script errors. Not yet tested against the live OpenStreetMap services.
