# Secure TDD for Claude Code

> **Secure Test-Driven Development (Secure TDD) workflow instructions, skills, and pre-tool hooks for Claude Code CLI agents.**

This repository is the dedicated Claude Code distribution of the **[Secure TDD Agent Framework](https://github.com/h3xar0n/secure-tdd-agent-framework)**.

## What's Included

- `CLAUDE.md`: System prompt instructions loaded on Claude Code session start to enforce the 4-phase inner loop (`PLAN` -> `RED` -> `GREEN` -> `REFACTOR`).
- `.claude/skills/`: Specialized kebab-case agent skills for threat modeling, security test writing, defensive coding, and refactor scanning.
- `.claude/settings.json` & `.claude/hooks/security_gate_hook.sh`: PreToolUse bash hook enforcing test-first verification before `git push` runs.
- `CONTEXT.md`: Living repository context, trust boundaries, and approved helpers.

## Getting Started

1. Open this repository in your terminal and launch Claude Code:
   ```bash
   claude
   ```
2. Claude Code automatically ingests `CLAUDE.md` and discovers skills in `.claude/skills/`.
3. Test the local pre-tool hook:
   ```bash
   bash .claude/hooks/tests/run_tests.sh
   ```

## Upstream Canonical Framework

All skills, rules, and threat models are maintained in the canonical upstream repository:  
🔗 **[h3xar0n/secure-tdd-agent-framework](https://github.com/h3xar0n/secure-tdd-agent-framework)**

## License

Licensed under the [Apache License, Version 2.0](LICENSE).
