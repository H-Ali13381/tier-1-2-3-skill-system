# Tier 1-2-3 Skill System

A simple way to decide how heavy an AI-agent skill should be.

A skill is reusable knowledge for an AI agent: when a certain kind of task comes up, the skill tells the agent how to handle it well.

The main idea: do not make every skill a giant prompt, and do not overbuild every workflow into software. Use the lightest version that works.

## The three tiers

### Tier 1: Text-only

Use plain instructions when the agent mainly needs judgment.

Good for:

- Writing style
- Review checklists
- Research strategy
- Design principles
- Policy or safety rules

Tier 1 teaches the agent what to do and how to think.

### Tier 2: Text + script

Add scripts when the agent keeps doing the same mechanical work.

Good for:

- Validating files
- Converting formats
- Packaging projects
- Generating reports
- Running repeatable checks

Tier 2 gives the agent reliable machinery instead of making it rewrite glue code every time.

### Tier 3: Text + script + ML pipeline

Add an ML model or specialist pipeline only when the agent is missing a real capability.

Good for:

- Audio detection
- Screenshot scoring
- Search reranking
- Classification
- Domain-specific detection or evaluation

Tier 3 gives the agent a new sense organ.

## Rule of thumb

Start with Tier 1.

Move to Tier 2 when the work becomes repetitive and mechanical.

Move to Tier 3 only when the missing piece is measurable and needs perception, ranking, scoring, detection, or classification.

## Why this matters

This keeps skills:

- Easier to read
- Easier to share
- Less bloated
- More reliable
- Less likely to make agents improvise fragile code

Do not overbuild. The best skill system is lean at the top, scripted where useful, and ML-backed only when the payoff is real.

## For agents

`SKILL.md` contains the agent-facing version of this model.

Install directly from GitHub:

```bash
npx skills add H-Ali13381/tier-1-2-3-skill-system
```

The root `SKILL.md` is canonical. A mirror copy also lives under `.agents/skills/tier-1-2-3-skill-system/` so cross-client skill scanners can discover it without breaking strict root skill validation.

## License

MIT
