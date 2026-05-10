# Operational Decision Ledger

## Infrastructure Roadmap
- [Current]: Transitioned to provider-agnostic orchestration via OpenRouter to mitigate API-level volatility.
- [Current]: Implemented a Triple-Layer Memory architecture to solve the "context-drift" problem in long-term projects.

## Technical Pivots
- **Pivot**: Migration from Web-UI interfaces to CLI-based Git-integrated orchestration.
- **Reasoning**: To ensure 100% auditability and state recovery. Web interfaces lack the necessary "undo" state for enterprise-grade engineering.

## System Evolution
- Established standardized .md protocols for memory persistence.
- Hardened the Debian VPS environment for autonomous agent execution.
