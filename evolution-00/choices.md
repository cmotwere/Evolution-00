# Route, Harness, and Candidate Framework

## Route: A — Subscription + small API budget
I already hold an active Claude subscription and have used the Claude API
extensively across prior projects (the Killgore-funded rural hospital
early-warning system and the Ogallala Aquifer MAS proposal), so the
marginal cost of a small additional API budget is low relative to the
capability gain. Route A gives access to frontier tool use, longer context,
and subagent support — all of which the groundwater system's multi-agent
architecture (data-collection, forecasting, adversarial-review, and
communication agents) will need from early weeks. I understand Route A
still requires running locally via Ollama for Evolutions 3 and 7.

## Harness: Claude Code
Claude Code is the richest harness under Route A — hooks
(PreToolUse/Stop/SessionStart), subagents, CLAUDE.md-based instruction
files, skills, and plan mode. Since my prior projects (Killgore,
Monaak Services, the SaaS portfolio) already rely on Django/Python
workflows and Claude API integration, Claude Code fits my existing
toolchain with minimal switching cost, and its subagent model maps
naturally onto the multi-agent design this system will need starting in
E8.

## Candidate orchestration framework: LangGraph
I've already used LangGraph as the orchestration architecture for the
Killgore-funded rural hospital financial early-warning system, and framed
the Ogallala groundwater MAS proposal as a parallel extension of that same
architecture. LangGraph's state-graph model — explicit state, checkpoints,
human-in-the-loop nodes — matches the governance requirements this course
emphasizes (a human checkpoint before actions execute) and gives me a
framework I can defend from direct prior experience rather than only
theory. This choice is provisional; ADR-1 in Evolution 2 will weigh it
against the alternatives (Claude Agent SDK, Pydantic AI, stdlib-only) with
the trade-offs and costs.
