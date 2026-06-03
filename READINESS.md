# gald3r Readiness Report — OpenClaw

> An honest accounting of how much of the gald3r framework installs natively on this
> platform, what degrades to an approximation, and what has no native home yet.
> Generated from a live documentation crawl on 2026-06-02.

**Overall readiness: ✅ Full.** OpenClaw is an open-source, self-hosted AI agent gateway with
a deep, file-based extensibility surface. All five C.R.A.S.H. layers — commands, rules,
agents, skills, and hooks — map onto native mechanisms, and MCP is supported as both client
and server. gald3r installs here without compromise.

## C.R.A.S.H. capability grid

| | Capability | Native? | What gald3r gets here | The gap |
|---|---|:---:|---|---|
| **C** | Commands | ✅ | User-invocable Skills surface as slash commands; `/skill <name>` is the generic entrypoint, plus direct `registerCommand()` and native Discord/Telegram registration | None — gald3r's `@g-*` command set installs as native slash commands |
| **R** | Rules | ✅ | `AGENTS.md` (operating rules) + `SOUL.md` (persona + "never do X" hard rules) + `MEMORY.md`, injected into agent context every session | None — gald3r rules load as first-class workspace instruction files |
| **A** | Agents | ✅ | Per-persona `bindings` route channels to isolated agents (own workspace/auth/sessions); `sessions_spawn` launches sub-agents at runtime | Recursive nesting gated by `maxSpawnDepth` (default 1); sub-agents run with restricted tool policies by default |
| **S** | Skills | ✅ | Agent Skills — `SKILL.md` (YAML frontmatter + markdown body), precedence-loaded across workspace, `.agents/skills`, `~/.openclaw/skills`, bundled, and plugin sources | None — gald3r's `SKILL.md` skills install directly; highest source wins on name clash |
| **H** | Hooks | ✅ | Event-driven `HOOK.md` (frontmatter `metadata.openclaw.events`) + `handler.ts`; broad taxonomy: `command:new/reset/stop`, `session:compact`, `agent:bootstrap`, `gateway:*`, `message:*` | None — gald3r's `g-hk-*` lifecycle wiring maps onto native events (TypeScript handlers) |

_Legend: ✅ native · ⚠️ partial / approximated · ❌ no native mechanism · ❓ unverified_

**Beyond C.R.A.S.H. — MCP: ✅** Native MCP client *and* server. Client saves server
definitions under `mcp.servers` in `openclaw.json` (stdio, HTTP/SSE, streamable-http);
`openclaw mcp serve` exposes channel conversations over stdio MCP. gald3r's MCP backend
reaches this platform with no bridge required.

## Adoptable extras (non-C.R.A.S.H.)

Platform-native strengths gald3r can lean on, and which need wiring:

| Feature | Status | gald3r fit |
|---|:---:|---|
| Lobster workflow pipelines (multi-step orchestration) | ⚙️ needs customization | A native host for gald3r `g-go`-style pipelines |
| Plugin system (`dock`/plugin channels) | ⚙️ needs customization | Plugins ship skills/hooks and call `registerCommand()` — a packaging path for gald3r bundles |
| Built-in `session-memory` hook (auto-extracts last 15 messages on `/new` / `/reset`) | ✅ present | A ready-made persistence pattern for gald3r session memory |
| `HEARTBEAT.md` scheduled/recurring behavior (cron-like) | ✅ present | Maps to gald3r heartbeat tasks |
| Inline directives (`/think`, `/fast`, `/model`, `/exec`, `/reasoning`, …) | ✅ present | Extra control surfaces; stripped before the model — no gald3r work required |

## The ceiling, and what's beyond it

gald3r runs at full strength on this platform — commands, rules, agents, skills, and hooks all map onto native mechanisms, so the framework installs without compromise. As third-party adaptation goes, this is the high end: nothing here has to be approximated.

But adaptation, however clean, is still gald3r living as a guest inside someone else's tool. The native build goes further — **gald3r_agent**, running on the **gald3r throne** over the **gald3r_world_tree** — where these primitives aren't mapped onto a host, they *are* the substrate. Same framework, no host in between.

> ### gald3r_agent — coming soon. 🌳

---

<sub>Capabilities verified against the platform's official documentation on 2026-06-02, and
re-verified each release via the gald3r platform-docs crawl. This report describes gald3r's
third-party adaptation surface; it is not an endorsement or critique of the platform itself.</sub>
