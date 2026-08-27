# Secure TDD for Claude Code

> **Claude Code distribution of the Secure TDD framework.** Integrates Test-Driven Development (TDD) and QA with proactive security guardrails into the Claude Code CLI assistant.

This repository is a downstream distribution generated from the canonical upstream repository:
**[secure-tdd-agent-framework](https://github.com/example/secure-tdd-agent-framework)**.

---

## What's Included

- **`CLAUDE.md`**: Always-on Claude Code project instructions for the 4-phase Secure TDD workflow (Plan -> Red -> Green -> Refactor & Evolve).
- **`.claude/skills/`**: Kebab-case modular skills:
  - `threat-model-assessor`: Scopes features and maps STRIDE boundaries in `threat_model.md`.
  - `security-test-writer`: Writes failing functional QA & security boundary tests (RED).
  - `defensive-developer`: Implements clean production code and defensive patterns (GREEN).
  - `local-refactor-scanner`: Cleans code, runs regression tests, and executes local SAST scans (REFACTOR).
  - `skill-evolution-updater`: Captures systemic lessons into `CONTEXT.md` and `SKILL.md`.
  - `history-context-seeder`: Seeds context from VCS commit history on onboarding.
- **`.claude/settings.json` & `.claude/hooks/`**: Claude Code `PreToolUse` bash interceptors for `git push` (CodeMender & Semgrep).
- **`CONTEXT.md`**: Living architectural boundaries and evolved project rules.

---

## Quickstart

1. Copy `CLAUDE.md`, `CONTEXT.md`, and `.claude/` into your project root:
   ```bash
   cp CLAUDE.md CONTEXT.md /path/to/your/project/
   cp -r .claude /path/to/your/project/
   ```
2. If using Semgrep instead of CodeMender:
   ```bash
   cp .claude/settings.semgrep.json .claude/settings.json
   ```
3. Run the offline hook test suite to verify:
   ```bash
   bash .claude/hooks/tests/run_tests.sh
   ```

---

## License

Licensed under the [Apache License, Version 2.0](LICENSE).
