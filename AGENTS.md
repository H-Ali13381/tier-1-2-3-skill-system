# Agent Notes

This repository publishes one Agent Skill: `tier-1-2-3-skill-system`.

Canonical files:

- `SKILL.md` is the source of truth for the skill.
- `.agents/skills/tier-1-2-3-skill-system/SKILL.md` is a cross-client discovery mirror.

When editing the skill, update the root `SKILL.md` first, then copy it to the mirror path so both `SKILL.md` files stay identical.

Related skill:

- `recursive-agent-improvement`: https://github.com/H-Ali13381/recursive-agent-improvement

Installability check:

```bash
npx skills add H-Ali13381/tier-1-2-3-skill-system --list
```

Validation check:

```bash
npx skill-tools check .
```

Do not add private paths, secrets, local debug notes, or session-specific history to this public skill artifact.
