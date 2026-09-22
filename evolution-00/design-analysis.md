# Design Analysis #1 — Chat Assistant vs. Agent Harness (Claude Code)

**Sources read:** Anthropic, "Building Effective Agents" (workflows vs.
agents); Sprint and Drift, "Tree Hollow"; gzkit docs/user/why.md; E0
lecture slides (nine components, worked Design Analysis).

**Nine components, one line each:**
1. **Foundation** — both hosted frontier models; Claude Code tiers models per task, no local option.
2. **Perception** — chat sees only user text; Claude Code also sees repo files, shell output, tool results.
3. **Planning & reasoning** — chat is one turn, human closes the loop; Claude Code runs an open ReAct loop with subagents.
4. **Tools & orchestration** — chat has none or a closed set; Claude Code has read/edit/bash plus MCP, gated by prompts.
5. **Memory & context** — chat keeps only the window; Claude Code adds compaction and CLAUDE.md, still no long-term memory.
6. **Coordination** — chat is single-threaded; Claude Code dispatches subagents from a main session.
7. **Evaluation & feedback** — both rely on the human; Claude Code also runs tests but has no built-in evaluator.
8. **Governance & human interface** — chat has a human every turn by construction; Claude Code asks per tool call, unrecorded.
9. **Runtime & operations** — chat is a stateless page; Claude Code runs in a terminal with background and cloud sessions.

**Why it was built this way, and what it cost:** The harness owns the loop
so tools, permissions, hooks, and subagents ship as product features —
that is what turns a generative system into an agent. The cost is that
governance becomes per-call and implicit: every tool call asks "allow?",
and by week four a user approves without reading. Nothing records what was
actually attested — the gap a governance layer like gzkit exists to close.

**Judgment loop:**
- **Decision** — give the harness direct tool and repo access instead of keeping the human as sole actor.
- **Characteristics privileged** — autonomy and speed over safety-by-default.
- **Cost** — a wider surface for output accepted without real scrutiny.
- **Failure mode** — automation bias: approving diffs and calls unread once it becomes routine (the Degradation Pattern).
- **Preservation mechanism** — the permission prompt on write actions, which only holds if actually read, not reflexively clicked.
