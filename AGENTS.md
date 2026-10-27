# AGENTS.md: EAP Project (Cowtown Gym Match)

Instructions for any AI agent or assistant working in this project folder. Not to be confused with `agent.md`, which defines how the gym-matching agent inside the app scores and explains gyms.

## What this project is

Ian Demroff's Entrepreneurial Action Project for W524 Strategic Entrepreneurship (Prof. Greg Fisher, Kelley School of Business). Cowtown Gym Match helps people new to Fort Worth pick a gym by training style and atmosphere, not proximity alone: a 16-question forced-choice quiz, 14 gym "vibe dossiers", and a deterministic ranking that Claude can explain.

The real subject of the EAP is Ian's skill gap: he believes a good enough product sells itself. The project tests that with a passive launch (Week 3) against active outreach (Weeks 4 to 5), including at least one gym referral pitch. Help that test happen. Do not help him avoid it by polishing the product.

## Files

| File | Role | Who changes it |
|---|---|---|
| `journal.md` | Weekly evidence log, outreach log, feedback log | Append only, after Ian confirms |
| `agent.md` | Matching rules and dossier schema, source of truth for scoring | Ian decides; change rules here before code |
| `index.html` | Ian's working app (single file) | Ask before changing |
| `cowtown-gym-match/` | Variant with live map and nearby search; Ian has not decided whether to keep it | Ask before changing |
| `cowtown-gym-match/EAP_Proposal_IanDemroff.docx` | Proposal: plan, deliverable, principles forecast | Read only |
| `memos/` | Graded write-ups (Word) | New files only |
| `skills/` | Skill drafts for this project | Edit freely |

## Status (from journal.md, last entry 2026-10-10)

- Week 1 build done: quiz, 14 web-seeded dossiers, scoring, limits, Claude layer, feedback summary, map variant.
- Not done or not logged: customer discovery conversations, geocoding, Fort Worth Barbell dossier, Week 2 visits, hosting for passive launch, referral gym choice.
- Journal has no entries after Oct 10. Weeks 2 to 6 evidence must come from Ian before any report is drafted.

## Standing rules

1. **Evidence first.** Every claim in the app, a memo, or the report traces to a dossier note, a journal entry, a source URL, or Ian's own words. No invented gyms, prices, hours, policies, users, or conversations.
2. **Don't rebuild.** Ian's app works. Prefer small changes, and ask before editing his files.
3. **Keep it a prototype.** Free tools only, no backend, no accounts, no paid APIs (Affordable Loss, Prototype). If a request is more building when the plan calls for outreach, say so once.
4. **Honest tone.** The course grades honesty. Name what went wrong and what was under-applied.
5. **Course frame.** Twelve principles of entrepreneurial progress; eight known (Problem, Exploration, Simplicity, Prototype, Experimentation, Hustle, Story, Affordable Loss). Never guess the other four.
6. **Writing style.** Plain full sentences, no em dashes, no arrow chains. Write-ups go to Claude Docs; graded deliverables can also get a Word copy in `memos/`.
7. **Privacy.** No tester contact details in the journal or any shared file.

## Skills

| Skill | Use it to |
|---|---|
| `cowtown-journal` | Log a week, an outreach attempt, or a feedback summary in `journal.md` |
| `cowtown-dossier` | Add a gym or correct one after a visit, in the `agent.md` schema |
| `cowtown-principles` | Map work to the principles with concrete evidence |
| `cowtown-memo` | Draft check-ins and the final report (max 4 pages of text) |

Typical flow: log it with the journal skill the day it happens, update dossiers after visits, run the principles check at each check-in, and write the memo or report from the journal.
