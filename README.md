# Agent skills

Personal agent skills maintained by seikosantana for Claude Code and Codex.

## Skills

| Skill | Purpose |
| --- | --- |
| [herdr/hc](herdr/hc/SKILL.md) | Persistent terminals, authorized agent coordination, efficient handoffs, and context compaction with herdr-core's `hc` CLI. |

## Personal permission policy

**The hc skill includes permission-bypass flags by personal preference:**

- Claude Code: `--dangerously-skip-permissions` bypasses permission prompts.
- Codex: `--yolo` bypasses approval prompts and sandbox restrictions.

These flags are not required by hc. Review and adapt this policy before using the skill in your own environment. The flags do not authorize work beyond the user's assigned scope.

Codex also uses `--no-daemon`. This serves a different purpose: hc's current manual requires it to keep Codex commands under its terminal management.

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
