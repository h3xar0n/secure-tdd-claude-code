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

## Optional Scanner Engines & Installation

The pre-push security gate hook supports modular scanning engines. Both scanners are **optional**:
- The hook checks which tools are available on your system `PATH`.
- If `semgrep` is not installed, the pipeline skips Stage 1 and proceeds directly to Stage 2 (`cm`).
- If neither scanner is installed, the hook logs an informational notice and allows the push to proceed normally.
- The hook engine is designed to be extended with additional scanners (such as Wiz Code for Stage 1) down the road.

### 1. Semgrep (Stage 1: Open-Source Deterministic AST Scanner)
```bash
# Via Homebrew:
brew install semgrep

# Or via pip:
pip install semgrep
```

### 2. CodeMender CLI (`cm` - Stage 2: Semantic Analysis & Remediation)
```bash
# Authenticate with Google Cloud:
gcloud auth application-default login

# Download and install binary (macOS ARM64 example):
gcloud artifacts generic download     --project=cmoc-prod     --location=us     --repository=codemender-cli-production     --package=cm     --version=stable     --name=cm-darwin-arm64.zip     --destination=./

unzip cm-*.zip && chmod +x cm && sudo mv cm /usr/local/bin/cm
cm init && cm init --verify
```

## Upstream Canonical Framework

All skills, rules, and threat models are maintained in the canonical upstream repository:  
🔗 **[h3xar0n/secure-tdd-agent-framework](https://github.com/h3xar0n/secure-tdd-agent-framework)**

## License

Licensed under the [Apache License, Version 2.0](LICENSE).
