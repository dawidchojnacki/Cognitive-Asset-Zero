# Cognitive-Asset-Zero: Unified AI Agent Infrastructure

## Description
Cognitive-Asset-Zero: A provider-agnostic AI orchestration framework on Debian VPS. Implements a triple-layer memory architecture (soul, memory, skills) via Aider and OpenRouter for seamless context preservation across LLM providers. Engineered for high-density logic retention, operational continuity, and enterprise-grade scalability.

## Core Architecture
This system decouples the reasoning engine (LLM) from the strategic and operational context.

- **soul.md**: Strategic intent and behavioral constraints.
- **memory.md**: Historical ledger of decisions and project evolution.
- **skills.md**: Codified technical workflows and specialized procedures.

## Operational Launch Command
```bash
aider --model openrouter/anthropic/claude-3.5-sonnet \
--no-show-model-warnings \
--chat-history-file /home/debian/MASTER_MEMORY/global_soul.md \
--read soul.md \
--read memory.md \
--read skills.md
