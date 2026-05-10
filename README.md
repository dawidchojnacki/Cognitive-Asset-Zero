Cognitive-Asset-Zero: Unified AI Agent Infrastructure
Description
Cognitive-Asset-Zero: A provider-agnostic AI orchestration framework on Debian VPS. Implements a triple-layer memory architecture (soul, memory, skills) via Aider and OpenRouter for seamless context preservation across LLM providers. Engineered for high-density logic retention, operational continuity, and enterprise-grade scalability.

Core Architecture
This system decouples the reasoning engine (LLM) from the strategic and operational context:

soul.md: Strategic intent and behavioral constraints.

memory.md: Historical ledger of decisions and project evolution.

skills.md: Codified technical workflows and specialized procedures.

Master Protocol (Single Source of Truth)
To ensure absolute behavioral consistency across all AI interfaces (Aider, Claude, etc.), the framework utilizes a centralized global rulebook.

Central Brain: /home/debian/CLAUDE.md — All global rules, coding conventions, and mission-critical facts reside here.

Context Automation: .aider.conf.yml — Automatically mounts CLAUDE.md as read-only context in every session.

Benefit: Unified instruction set for both CLI-based development and strategic chat interfaces.

Operational Launch Command
Bash
aider --model openrouter/anthropic/claude-3.5-sonnet \
--no-show-model-warnings \
--chat-history-file /home/debian/MASTER_MEMORY/global_soul.md \
--read soul.md \
--read memory.md \
--read skills.md
