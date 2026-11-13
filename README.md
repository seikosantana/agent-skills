# Agent skills

Personal agent skills maintained by seikosantana for Claude Code and Codex.

## Skills

| Skill | Purpose |
| --- | --- |
| [herdr/hc](herdr/hc/SKILL.md) | Persistent terminals, authorized agent coordination, efficient handoffs, and context compaction with herdr-core's `hc` CLI. |

## Permission setup

The maintainer's recommended choice is **Yes** to automatic permission mode:

- Claude Code: `--dangerously-skip-permissions` bypasses permission prompts.
- Codex: `--yolo` bypasses approval prompts and sandbox restrictions.

These flags are optional and are not required by hc. During agent-assisted installation or first use, the skill asks for an explicit choice unless the user has already provided one. A plain SKILL.md cannot execute an installation prompt itself. Copying this skill does not enable bypass mode automatically; an unanswered setup question uses normal permission controls.

The agent saves the answer in `~/.config/agent-skills/hc.json`:

```json
{"automatic_permissions": true}
```

Use false to retain normal permission controls. This preference is machine-local; copying the skill does not copy consent. Users may change their choice at any time. These flags never authorize work beyond the assigned scope.

Codex always uses `--no-daemon` under hc, independently of this choice, to keep commands under terminal management as required by hc's current manual.

## Install

Clone this repository, then copy the skill into the discovery directory for the agent you use:

```bash
git clone https://github.com/seikosantana/agent-skills.git
cd agent-skills

# Codex (adjust if CODEX_HOME is set)
mkdir -p "${CODEX_HOME:-$HOME/.codex}/skills/hc"
cp herdr/hc/SKILL.md "${CODEX_HOME:-$HOME/.codex}/skills/hc/SKILL.md"

# Claude Code
mkdir -p "$HOME/.claude/skills/hc"
cp herdr/hc/SKILL.md "$HOME/.claude/skills/hc/SKILL.md"
```

Back up an existing skill before replacing it. Start a new agent session to discover the installed skill. Copies do not update automatically; pull this repository and copy the revised skill when updating.

## Maintenance

This repository is the source of truth for these skills. The installed `hc --skill` manual remains authoritative for CLI behavior; the skill adds workflow guidance and personal preferences rather than copying the full manual. Validate changes against the installed CLI before distributing them.
