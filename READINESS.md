# gald3r Readiness Report — OpenCode

> An honest accounting of how much of the gald3r framework installs natively on this
> platform, what degrades to an approximation, and what has no native home yet.
> Generated from a live documentation crawl on 2026-06-02.

**Overall readiness: ✅ Full.** OpenCode (SST) is a capable agentic coding tool with
native, documented support for all six gald3r extension mechanisms. It even discovers
Claude Code's `.claude/` tree and the open `.agents/` standard, so gald3r's commands,
rules, agents, and skills are largely drop-in.

## C.R.A.S.H. capability grid

| | Capability | Native? | What gald3r gets here | The gap |
|---|---|:---:|---|---|
| **C** | Commands | ✅ | Custom Commands as markdown in `.opencode/commands/` with YAML frontmatter; `$ARGUMENTS`, positional `$1/$2`, and `!cmd` bash injection | None — gald3r's `@g-*` command set installs as native custom commands |
| **R** | Rules | ✅ | `AGENTS.md` (CLAUDE.md fallback) loaded at startup, plus the `instructions` field in `opencode.json` for extra files/globs/URLs | None — gald3r rules load here as first-class instruction files |
| **A** | Agents | ✅ | Primary agents + subagents from `.opencode/agents/` markdown or `opencode.json`; `@mention` or Task-tool invocation | None — gald3r's `g-agnt-*` roles map to native agent files |
| **S** | Skills | ✅ | Native `skill` tool loads `SKILL.md` on-demand; discovers `.opencode/skills/`, `.claude/skills/`, and `.agents/skills/` | None — gald3r `SKILL.md` packages drop in with no conversion |
| **H** | Hooks | ✅ | JS/TS plugins subscribe to lifecycle events: `tool.execute.before/after`, `file.edited`, `session.created`, and ~20 more | No first-class git pre-commit event, and hooks need a JS/TS wrapper — gald3r PowerShell/Python scripts must be shelled out |

_Legend: ✅ native · ⚠️ partial / approximated · ❌ no native mechanism · ❓ unverified_

**Beyond C.R.A.S.H. — MCP: ✅** Native MCP under `mcp` in `opencode.json`, supporting both
`local` (spawned command) and `remote` (URL) servers; 2026 updates added MCP OAuth
callback-port config — gald3r's MCP backend connects directly.

## Adoptable extras (non-C.R.A.S.H.)

Platform-native strengths gald3r can lean on, and which need wiring:

| Feature | Status | gald3r fit |
|---|:---:|---|
| Custom Tools (LLM-callable functions alongside read/write/bash) | ⚙️ needs customization | Could expose gald3r operations as first-class tool calls |
| Plan vs Build modes (read-only/suggest vs full-access profiles) | ✅ present | Maps to gald3r's plan/execute separation; no work required |
| Official `@opencode-ai/sdk` + in-process HTTP server | ✅ present | A real automation entry point for gald3r tooling and session metadata |
| `opencode.json` config (project + global, loads upward) | ✅ present | Single home for gald3r MCP, instructions, plugins, and agent wiring |

## The ceiling, and what's beyond it

gald3r runs at full strength on this platform — commands, rules, agents, skills, and hooks all map onto native mechanisms, so the framework installs without compromise. As third-party adaptation goes, this is the high end: nothing here has to be approximated.

But adaptation, however clean, is still gald3r living as a guest inside someone else's tool. The native build goes further — **gald3r_agent**, running on the **gald3r throne** over the **gald3r_world_tree** — where these primitives aren't mapped onto a host, they *are* the substrate. Same framework, no host in between.

> ### gald3r_agent — coming soon. 🌳

---

<sub>Capabilities verified against the platform's official documentation on 2026-06-02, and
re-verified each release via the gald3r platform-docs crawl. This report describes gald3r's
third-party adaptation surface; it is not an endorsement or critique of the platform itself.</sub>
