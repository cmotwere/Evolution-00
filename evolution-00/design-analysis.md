# Design Analysis #1 — Chat Assistant vs. Agent Harness (Claude Code)

**Sources read:** Anthropic, "Building Effective Agents" (workflows vs.
agents); Sprint and Drift, "Tree Hollow"; gzkit docs/user/why.md; E0
lecture slides (nine components, worked Design Analysis).

**Nine components, one line each:**
1. **Foundation** — same hosted frontier models under both; Claude Code just tiers which model handles which task.
2. **Perception** — a chat assistant only sees what I type; Claude Code also reads my repo, shell output, and its own tool results.
3. **Planning & reasoning** — chat is one exchange and I close the loop myself; Claude Code keeps looping (plan, act, check) until it decides it's done.
4. **Tools & orchestration** — chat has no tools or a fixed vendor set; Claude Code can read/edit files and run shell commands, plus MCP, each gated by a prompt.
5. **Memory & context** — chat only remembers the current window; Claude Code compacts long sessions and keeps CLAUDE.md around, but still forgets between sessions.
6. **Coordination** — chat is one thread; Claude Code can spin up subagents from the main session.
7. **Evaluation & feedback** — both still lean on me to judge the output; Claude Code can also run tests, but nothing grades its own work.
8. **Governance & human interface** — chat forces a human turn by design; Claude Code asks "allow?" per tool call, but never records what I actually approved.
9. **Runtime & operations** — chat is a stateless page; Claude Code runs in my terminal and can keep working in the background.

**Why it was built this way, and what it cost:** Handing the harness the
loop is what makes it an agent instead of a chatbot — Anthropic can ship
tools, permissions, and subagents as real product features instead of me
manually copy-pasting between turns. The cost is that governance turns
into a stream of small "allow?" prompts instead of one clear decision, and
by week four I'm clicking through them out of habit rather than reading
each one — nothing keeps a record of what I actually approved.

**Judgment loop:**
- **Decision** — give the harness direct file and shell access instead of staying the only actor in the loop.
- **Characteristics privileged** — speed and autonomy over safety-by-default.
- **Cost** — more surface area where I can accept output I never really scrutinized.
- **Failure mode** — automation bias: approving prompts unread once it becomes routine (the Degradation Pattern).
- **Preservation mechanism** — the permission prompt on write actions, which only protects me if I actually read it instead of reflexively hitting yes.
