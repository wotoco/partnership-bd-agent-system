# Porting to other agent CLIs

This system was built on Claude Code, but the architecture is deliberately tool-agnostic: it's markdown files plus an agent that reads, writes and calls tools. Here's how the pieces map to **Google Gemini CLI**.

| Piece | Claude Code | Gemini CLI | Ports cleanly? |
|-------|-------------|------------|----------------|
| Always-loaded context | `CLAUDE.md` | `GEMINI.md` (hierarchical, auto-loaded) | ✅ direct |
| Memory files | markdown in `memory/` | same — just files | ✅ direct |
| Custom commands / skills | `~/.claude/commands/*.md` | `.gemini/commands/*.toml` | ✅ (reformat to TOML) |
| Tool integrations | MCP servers | MCP servers (supported) | ✅ direct |
| Persistent memory tool | memory + recall | `/memory` + `save_memory` | ✅ near-equivalent |
| Sub-agents | first-class `Agent` tool | subagents (newer, less mature) | ⚠️ partial |
| Autonomous loop | `/loop` | no native loop — wrap with `cron` | ⚠️ needs glue |
| Hooks | rich hook system | lighter hook support | ⚠️ partial |

## Bottom line

About **80% transfers directly.** The file-based memory, the layered context, custom commands and MCP tools all have clean Gemini equivalents.

The two pieces that need work on Gemini:
- **Multi-agent orchestration** — Gemini's subagents are catching up but aren't as mature as Claude Code's `Agent` tool, so the `/post` and `/qa-check` patterns need more manual wiring.
- **The autonomous night loop** — there's no native `/loop`, so you'd schedule `nightwatch` with a plain `cron` job instead.

Everything else — the memory architecture, the self-improvement loop, the short-core/deep-reference design — is just files and prompts. It doesn't care which model reads it.
