# AGENTS.md Lab — Measurement

Run 2026-09-21, outside the scheduled 09/17 class session (missed that
session; completing the technical measurement solo, ahead of arranging
the Chase peer swap separately — see "Chase swap" below).

## Setup
- `opencode --version`: 1.18.21
- Model: `opencode/big-pickle` (confirmed via `opencode models`; no
  separate OpenCode Zen login was required — it listed without one)
- No pre-existing `CLAUDE.md` in the project root before this lab.

## Inventory (drawn from AI_LOG.md — no coding sorties flown yet for this
system; Evolution 0 is still docs/decisions only, so this pulls from the
two real AI-assisted sessions logged so far, not from flight logs that
don't exist yet)

**Three things the agent got wrong more than once:**
1. Left required sections half-finished with placeholder/TODO text and
   treated the file as "done" until asked to actually finish it —
   happened separately in `skills-inventory.md` (links, CIDM 6303
   section), `board.md` (reading list), and `toolkit-check.md` (entirely
   unfilled).
2. Assumed a repo/file structure (evolution-00/ + root AI_LOG.md +
   design-analyses/LEDGER.md) from the assignment text instead of
   checking the authoritative structure posted in WTClass first.
3. Skipped the required commit attribution line on the first commit and
   had to amend it immediately after.

**Two things re-explained that had already been established:**
1. Don't fabricate URLs, usernames, or links — a standing rule, but the
   human still had to hand over the real GitHub username/repo URL twice
   (once for the org repo, again for the personal-repo fallback) before
   either push could happen.
2. Work that must be defensible as the *student's own* understanding
   (the Design Analysis rewrite) can't be satisfied by the AI producing
   better-sounding prose in the student's voice — this had to be
   clarified twice: once when trimming the word count, again when asked
   to "rewrite it."

**Where the truth lives (paths, not descriptions):**
- `evolution-00/pitch.md`, `evolution-00/choices.md`, `AI_LOG.md`,
  `design-analyses/LEDGER.md`, `evolution-00/toolkit-check.md`.
- Not yet created: `docs/prd.md`, `docs/adr/` (ADR-1 lands Evolution 2),
  `evolution-01/flight-card.md` onward.

## Measurement

| Field | Value |
|---|---|
| `wc -c AGENTS.md` | 2163 |
| Baseline input tokens (no AGENTS.md present) | 9220 |
| With-file input tokens | 9816 |
| Difference | 596 |
| Difference ÷ byte count | 596 / 2163 ≈ 27.6% — lands inside the "roughly a quarter to a third" range the facilitator notes predict |
| Verbatim recall of test command (step 4) | **Yes.** Asked "What does this project's AGENTS.md say the test command is?" and Big Pickle answered by quoting the exact sentence: *"No source code exists yet (Evolution 0 is decisions and docs only). Do not invent install/run/test commands — none exist until real code lands."* |
| `wc -c` of `/init` output | 2610 (generated in a scratch copy of the repo with `AGENTS.md` removed first) |

Both probe runs used `opencode run -m opencode/big-pickle --format json
"Reply with the single word OK."` and read `tokens.input` from the
`step-finish` event — a CLI-based version of the TUI's input-token
readout, since this was run headless rather than interactively.

## /init specimen (for Probe 1 practice)

The generated file was better than a pure encyclopedia — it picked up
real facts from `git log` and `AI_LOG.md` (e.g., a "Git / remote state"
section noting the org-access issue). But it still has classic
encyclopedia lines. Self-applying Probe 1 to it:

- `## Layout` lists every file in `evolution-00/` with a one-line
  description of each — this is exactly what `ls evolution-00/` plus
  opening each file already tells the agent. **Result: would be deleted
  under Probe 1.**
- The "Verified tooling" line under `## Environment facts` restates
  version numbers that live in `toolkit-check.md`, which the file
  doesn't even point to — a pointer would survive; a copy of numbers
  that will go stale as soon as a tool is upgraded would not.

This is the argument the lab is testing: the hand-written file (2,163
bytes) is under budget and every line is a command, a differing
convention, or a pointer; `/init`'s output (2,610 bytes) is only
~20% larger by byte count here but spends a much larger share of that
budget restating what the repo already shows.

## Chase swap

**Not completed.** This session's technical measurement (setup through
`/init` comparison) was done solo, without a class partner, since the
09/17 session was missed. I have not exchanged files with a classmate, so
there is no real Probe 1/2/3 verdict from another reader yet — writing
one myself would defeat the point of the exercise (the Chase is supposed
to read cold, not hear the author explain).

**Still to do before the E5 Sprint deliverable is due:** trade this
`AGENTS.md` with an actual classmate, have them run the three probes,
record their verbatim findings below, revise the file, and re-measure.

| Chase partner | *pending* |
|---|---|
| Probe 1 result | *pending* |
| Probe 2 result | *pending* |
| Probe 3 result | *pending* |
| Verdict | *pending — not PASS/FAIL until a real peer reads it* |

## Ledger event

Not recorded via `gz ledger` — gzkit has not been initialized in this
repo yet (`gz init` also scaffolds a Python project skeleton and picks a
governance mode, which is a bigger decision for the semester system than
this lab should trigger as a side effect). The commit itself is recorded
in `git log` in the interim; a real `gz` ledger event should be added
once gzkit governance is formally initialized for this system.
