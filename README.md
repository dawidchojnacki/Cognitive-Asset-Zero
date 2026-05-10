# Cognitive-Asset-Zero
### Unified AI Agent Infrastructure

A provider-agnostic AI orchestration framework running on a Debian VPS. Implements a **triple-layer memory architecture** (`soul`, `memory`, `skills`) via [Aider](https://aider.chat) and [OpenRouter](https://openrouter.ai) for seamless context preservation across LLM providers — and bridges that context with **Claude Code's** native memory system through a single shared rulebook.

Engineered for high-density logic retention, operational continuity, and enterprise-grade scalability.

---

## Why this exists

LLM tooling is fragmented. Aider has its own chat history. Claude Code has its own auto-memory. ChatGPT has its own threads. Switch providers and you lose context.

Cognitive-Asset-Zero decouples the **reasoning engine (LLM)** from the **strategic and operational context**, so you can change models without losing your project's brain.

---

## Core Architecture

Three layers of context, each serving a different purpose:

| File | Role |
|------|------|
| `soul.md` | Strategic intent and behavioral constraints — *who the agent is* |
| `memory.md` | Historical ledger of decisions and project evolution — *what happened* |
| `skills.md` | Codified technical workflows and specialized procedures — *how to act* |

Each layer is a plain Markdown file. Portable, diffable, version-controlled.

---

## Master Protocol — Single Source of Truth

To guarantee behavioral consistency across **all** AI interfaces (Aider, Claude Code, future tools), the framework uses one centralized global rulebook.

- **Central Brain:** `/home/debian/CLAUDE.md` — global rules, coding conventions, mission-critical facts.
- **Context Automation:** `.aider.conf.yml` mounts `CLAUDE.md` as read-only context in every Aider session.
- **Claude Code:** auto-loads `CLAUDE.md` natively — no configuration required.

**Result:** one file edit propagates instantly to every AI tool you use.

### `.aider.conf.yml`
```yaml
read:
  - /home/debian/CLAUDE.md
```

That's the entire bridge. Two lines.

---

## Bridging Claude Memory with OpenRouter / Aider

Claude Code maintains its own auto-memory at:
```
~/.claude/projects/<project>/memory/
```
This is structured (YAML frontmatter + per-topic files) and Claude-specific. Aider can't read it directly.

The pattern this repo demonstrates:

1. **Strategic / shared knowledge** → `CLAUDE.md` (read by both Claude Code and Aider via `.aider.conf.yml`).
2. **Layered project context** → `soul.md` / `memory.md` / `skills.md` (loaded into Aider via `--read`).
3. **Claude-private auto-memory** → stays in `~/.claude/...` for Claude Code's own continuity.

When something Claude learned in a session needs to be visible to Aider too, you promote it from auto-memory into `CLAUDE.md`. One file, both worlds.

---

## Operational Launch Command

```bash
aider \
  --model openrouter/anthropic/claude-3.5-sonnet \
  --no-show-model-warnings \
  --chat-history-file /home/debian/MASTER_MEMORY/global_soul.md \
  --read soul.md \
  --read memory.md \
  --read skills.md
```

`.aider.conf.yml` adds `CLAUDE.md` automatically on top of the three `--read` files.

### Switching providers
Because the context is decoupled from the model, swapping providers is one flag:
```bash
--model openrouter/openai/gpt-4o
--model openrouter/google/gemini-2.0-flash
--model openrouter/meta-llama/llama-3.3-70b
```
The `soul / memory / skills` triad travels with you.

---

## Repository Layout

```
COGNITIVE-ASSET-ZERO/
├── CLAUDE.md            # → symlink or pointer to /home/debian/CLAUDE.md
├── soul.md              # strategic intent
├── memory.md            # decision ledger
├── skills.md            # workflows
├── .aider.conf.yml      # auto-mounts CLAUDE.md into Aider
└── README.md
```

---

## Requirements

- Debian-based Linux (tested on Debian 12 VPS)
- Python 3.10+
- [Aider](https://aider.chat) - `pip install aider-chat`
- [OpenRouter](https://openrouter.ai) API key (or any model provider Aider supports)
- *(Optional)* [Claude Code](https://claude.com/claude-code) for the integrated memory bridge

---

## Quickstart

```bash
git clone https://github.com/dawidchojnacki/Cognitive-Asset-Zero.git
cd Cognitive-Asset-Zero

# point .aider.conf.yml at your own CLAUDE.md path if different
export OPENROUTER_API_KEY=sk-or-...

aider --model openrouter/anthropic/claude-3.5-sonnet \
      --read soul.md --read memory.md --read skills.md
```

---

## Design Principles

- **Provider-agnostic.** No lock-in. Markdown + Aider + OpenRouter.
- **Plain text wins.** Memory you can `grep`, `diff`, and `git blame`.
- **One source of truth.** `CLAUDE.md` is canonical; everything else points at it.
- **Layered context.** Identity (`soul`) ≠ history (`memory`) ≠ procedure (`skills`).

---

## License

MIT

---

*Cognitive-Asset-Zero - your project's brain, independent of any single LLM vendor.*
