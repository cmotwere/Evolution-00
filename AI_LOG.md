# AI_LOG.md

## Week 00 — Evolution 0 (Orientation)

**Date:** 2026-08-30

**What I asked:** Help understanding the Evolution 0 assignment (initially
unclear from the assignment page alone); after clarifying the repo
structure, asked for drafts of `pitch.md`, `choices.md`,
`skills-inventory.md`, and `design-analysis.md` based on my own system
idea (a groundwater early-warning agent for the Ogallala Aquifer) and my
prior project work.

**Model and harness:** Claude (claude.ai chat interface), no coding
harness yet — Evolution 0 predates any code.

**What I accepted:**
- The PEAS specification structure and PEAS-to-nine-components mapping in
  `pitch.md`, after confirming the user, problem, and risk framing matched
  my actual intent for the system.
- The Route A / Claude Code / LangGraph reasoning in `choices.md` — this
  reflects a real decision I'd already leaned toward given my Killgore and
  Ogallala proposal experience with LangGraph.
- The skills inventory content describing my prior projects (Killgore,
  Ogallala, Mailroom Management System, Monaak Services) — these are
  facts about my own work, not generated claims.

**What I modified/will modify:**
- `skills-inventory.md` is incomplete — I still need to add real links to
  my repos and fill in what I carried in from CIDM 6303, since the model
  had no visibility into that course.
- `design-analysis.md` was drafted at ~180 words against Claude Code
  specifically; I need to trim it to ~150 words and rewrite it in my own
  language before Drift, since I have to defend it without this file or
  any AI in front of me.

**What I rejected:** Nothing outright yet — everything drafted needs a
pass in my own words before it counts as understood, per the course's own
rule that Sprint output has no authority until it survives Drift.

**Why:** The nine-component structure and PEAS framing were unfamiliar to
me going in; using AI to get an initial structure right, then rewriting it
myself, matched the course's stated model (AI as amplifier, not
authority).

**How I verified what I kept:** Cross-checked the PEAS and nine-component
definitions against the assignment materials and lecture slides provided
in this course (not against external sources), and confirmed the
project-history claims (Killgore, Ogallala, Mailroom system) against my
own actual work rather than taking them as generated fact.

---

## Week 00 — Evolution 0, session 2 (toolkit + repo setup)

**Date:** 2026-09-21

**What I asked:** Asked Claude Code (in the VS Code extension) to check
whether E0 was ready to submit, then to fix the gaps it found: verify/
install the actual toolkit, stand up the git repository with the required
structure, close out the two open TODOs in `skills-inventory.md`, add the
missing `design-analyses/LEDGER.md`, trim `design-analysis.md` toward 150
words, and fill in `board.md`'s reading-list section.

**Model and harness:** Claude Sonnet 5, via Claude Code (VS Code
extension), using its Bash/PowerShell/file-edit tools directly on my
machine.

**What I accepted:**
- Running the actual install commands for `uv`, Python 3.14 (via `uv`),
  `gzkit`, and pulling `llama3.2:1b` in Ollama, then pasting the real
  command output into `toolkit-check.md` — this is exactly what the
  assignment asks for (verified output, not a description of output).
- Cloning the course org repo, and when my account (`cmotwere`) got a 403
  on push (write access not yet granted in `WTAMU-CIDM6333`), pushing the
  same commit to a personal repo (`github.com/cmotwere/Evolution-00`) as a
  stopgap so the work is not stuck local-only before the deadline.
- The `evolution-00/` + root `AI_LOG.md` + `design-analyses/LEDGER.md`
  structure the model inferred from the assignment text, since I hadn't
  pulled up the exact structure image posted in WTClass at the time.
- The real links it found on my own portfolio site (charlesotwere.com) for
  `skills-inventory.md` — I confirmed each one is actually mine before
  accepting them.

**What I modified/will modify:**
- `design-analysis.md` was mechanically trimmed to ~150 words by the
  model, but it is still written in the model's phrasing, not mine. I
  need to rewrite it myself before Drift — the whole point of that
  exercise is being able to defend it without this file or any AI open.
- Need to confirm with the instructor whether org access
  (`WTAMU-CIDM6333`) has been granted, and if so, push this same commit
  there and treat the personal repo as a backup only, not the graded
  location.
- Need to check the personal-repo stopgap doesn't itself count against
  "GitHub onboarding" — the assignment specifies the org, not a personal
  account.

**What I rejected:** Nothing — the toolkit output and file structure are
mechanical, verifiable facts (version strings, file locations), not
claims requiring judgment calls.

**Why:** I asked the harness to run real commands and paste real output
rather than writing docs describing what installation "would" look like,
because "toolkit verified" is graded and a placeholder doesn't verify
anything. I drew the line at having it rewrite my Design Analysis prose
in "my own language," since that specific exercise only counts if the
words are actually mine.

**How I verified what I kept:** Re-ran `gz --version`, `ollama list`, and
`uv --version` myself after the session to confirm the pasted output in
`toolkit-check.md` matches reality; confirmed the pushed repo at
`github.com/cmotwere/Evolution-00` actually contains the right file tree
by checking it in a browser rather than trusting the push log alone.

---

## AGENTS.md Lab (catch-up — missed the 09/17 in-class session)

**Date:** 2026-09-21

**What I asked:** Asked Claude Code to complete the AGENTS.md lab I'd
missed: draft an AGENTS.md for the system under the 4,000-character
budget, measure what OpenCode's `opencode/big-pickle` model actually
loads from it versus a baseline, verify verbatim recall of one line, and
compare against `/init`'s generated output.

**Model and harness:** Claude Sonnet 5, via Claude Code (VS Code
extension), which in turn drove `opencode run` non-interactively
(OpenCode 1.18.21, model `opencode/big-pickle`) to produce the actual
measurements.

**What I accepted:**
- The AGENTS.md content itself: since this system has no code yet
  (Evolution 0 is still docs/decisions), the file is scoped to what's
  real right now — pointers to `pitch.md`/`choices.md`/`toolkit-check.md`,
  an explicit "don't invent run/test commands, none exist yet" line, and
  rules drawn from actual mistakes made in this repo's own AI_LOG (see
  the two "got wrong twice" / "re-explained" lists in
  `evolution-03/agents-md-measurement.md`), not invented ones.
- The real measured numbers: 2,163 characters on disk; 9,220 baseline
  input tokens vs. 9,816 with the file present (596-token delta, ~27.6%
  of the byte count, matching the lab's predicted quarter-to-third
  range); verbatim recall of the test-command line confirmed word for
  word; `/init`'s generated file at 2,610 bytes for comparison.
- The `CLAUDE.md` bridge (`@AGENTS.md`) so Claude Code picks up the same
  map, per the lab's own note that Claude Code imports AGENTS.md rather
  than reading it directly.

**What I rejected:**
- Running `gz init` to record a real gzkit ledger event for the commit.
  It also scaffolds a Python project skeleton and picks a governance
  mode (`lite`/`heavy`) — a real structural decision for the semester
  system, not something a 30-minute instruction-file lab should trigger
  as a side effect. Left as a documented pending item instead.
- Fabricating the Chase peer-swap step. I don't have a partner's real
  read of the file, so `evolution-03/agents-md-measurement.md` marks
  Chase partner/probe results/verdict as pending rather than inventing
  plausible-sounding findings — the whole point of that step is a cold
  read from someone who didn't write the file.

**Why:** The lab's own claim is that an instruction file should be a map,
not an encyclopedia — restating anything derivable from the code is
wasted budget. Since the "code" here is really the rest of this repo's
docs, I had it ground every AGENTS.md line in something a peer or a
future me could actually check, and refuse to manufacture the two things
(a live peer, a governance-mode decision) that aren't mine to invent.

**How I verified what I kept:** Re-ran the `opencode run` probes myself
after the fact to confirm the token counts were stable across repeats;
read the `/init`-generated file in the scratch copy directly rather than
trusting a description of it; confirmed `AGENTS.md` (2,163 chars) is well
under the 4,000-character budget with `wc -c`.
