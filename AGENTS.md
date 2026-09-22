# Ogallala Groundwater Early-Warning Agent

This repo is the CIDM 6333 semester system: an agent that turns fragmented
TWDB/USGS/USDA groundwater data into early depletion alerts for Texas
Panhandle GCD staff. It must never issue an alert without a documented,
checkable basis — no silent extrapolation past what the data supports.

## Run and test
- No source code exists yet (Evolution 0 is decisions and docs only). Do
  not invent install/run/test commands — none exist until real code lands.
- Toolkit versions are verified in `evolution-00/toolkit-check.md`;
  re-verify with `uv --version`, `gz --version`, `ollama list`.
- gzkit is not yet initialized in this repo (`gz init` has not been run).
  Once it is, `gz status` shows ledger state.

## Conventions that differ from defaults
- The framework choice (LangGraph) in `evolution-00/choices.md` is
  provisional — do not treat it as final until ADR-1 (Evolution 2) is
  committed with alternatives weighed.
- Route A means Claude API + a small budget, not hosted-only — local
  Ollama runs are still required for Evolutions 3 and 7.
- A file in `evolution-00/` that reads as finished may still contain a
  TODO or bracketed placeholder — check before treating it as authoritative.

## Rules that must hold (enforced)
- Never fabricate a URL, username, or repo link. Enforced by: nothing
  yet — ask the human for the real one every time.
- No file is marked done while it still contains a placeholder or TODO.
  Enforced by: nothing yet — human re-read required before commit.
- No push to `main` on the org repo without confirmed collaborator
  access. Enforced by: nothing yet — GitHub org permissions only (see
  the 2026-09-21 entry in `AI_LOG.md` for the 403 this caused).

## Where the truth lives
- What the system is and why: `evolution-00/pitch.md`
- Route/harness/framework reasoning (provisional): `evolution-00/choices.md`
- Toolkit state: `evolution-00/toolkit-check.md`
- AI interaction history: `AI_LOG.md`
- Design analyses index: `design-analyses/LEDGER.md`
- Not yet created: `docs/prd.md`, `docs/adr/` (ADR-1 lands Evolution 2),
  `evolution-01/flight-card.md` onward
