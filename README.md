# Tier 1-2-3 Skill System

A skill is reusable operational knowledge, not a random prompt snippet or a session diary.

The rule: pick the lightest tier that reliably solves the problem.

## Short Version

- Tier 1 teaches the agent what to do.
- Tier 2 gives the agent deterministic machinery to do it.
- Tier 3 gives the agent a new sense organ or specialist capability.

## The Three Tiers

| Tier | Shape | Use When | Upgrade Trigger |
|---|---|---|---|
| 1. Text-only | `SKILL.md` | The value is judgment, policy, sequencing, style, philosophy, or a checklist. Native agent tools are enough. | Agents repeatedly rewrite glue code or make mechanical mistakes. |
| 2. Text + Script | `SKILL.md` + `scripts/` | The workflow has deterministic steps: parse, validate, convert, audit, launch, package, benchmark, or export. | Prompting/scripts cannot provide the missing perception, ranking, scoring, detection, or domain inference. |
| 3. Text + Script + ML Pipeline | `SKILL.md` + `scripts/` + training/eval/model artifacts | The agent needs a capability not native to the base model or host app: classifier, detector, reranker, scorer, evaluator, verifier, or specialist model. | The ML specialist becomes stable enough to package as a tool, MCP server, CLI, or standalone product with its own model card. |

## Tier 1: Text-only Skill

Use this for workflows dominated by judgment, sequencing, policy, taste, or communication style.

Typical structure:

```text
skill-name/
  SKILL.md
```

Good fits:

- Review philosophy
- Writing voice
- Research synthesis strategy
- Design principles
- Operational checklists
- Skill packaging standards

What belongs in the text:

- Trigger conditions: when to use the skill
- Decision rules: how to choose between options
- Pitfalls: common ways the agent screws it up
- Verification checklist: what proves the task is done
- One or two concrete examples

Do not turn everything into a script. If the hard part is taste, policy, or reasoning, text is enough.

## Tier 2: Text + Script

Use this when the agent would otherwise keep inventing similar code every run.

Typical structure:

```text
skill-name/
  SKILL.md
  scripts/
    primary_tool.py
  references/
    details.md
```

Good fits:

- Skill validation and packaging
- PDF/docx/pptx/xlsx conversion helpers
- Context-bloat audits
- Desktop-state backups
- Benchmark aggregation
- Report generation
- Repeated parsers, exporters, formatters, and sanity checks

Rules:

- `SKILL.md` explains when, why, and how to call the script.
- The script performs the deterministic mechanical work.
- Scripts should be idempotent where practical.
- Scripts should expose flags or environment variables instead of requiring edits.
- Scripts should verify success before exiting 0.
- Scripts should avoid logging secrets.
- Bulky rationale, edge cases, or examples go in `references/`, not the main skill body.

The test: if you catch the agent writing the same glue code twice, promote the workflow to Tier 2.

## Tier 3: Text + Script + ML Pipeline

Use this when the base model lacks a measurable capability and ordinary scripts cannot fill the gap.

Typical structure:

```text
skill-name/
  SKILL.md
  scripts/
    train.py
    evaluate.py
    infer.py
  references/
    task-spec.md
    eval-plan.md
    model-card.md
  models/      # optional; often external or gitignored
  data/        # optional; usually samples or metadata only
```

Good fits:

- Wakeword or audio detection
- Screenshot or layout scoring
- UI/theme coherence judging
- Search reranking
- Patch-risk classification
- Fact-consistency verification
- Domain-specific extraction
- Anomaly detection

Rules:

- Define inputs, outputs, metrics, and baselines before training.
- Include hard negatives and failure cases.
- Keep inference compact and machine-readable, preferably JSON.
- Explain when to trust the specialist and when to abstain.
- Explain how the specialist output changes the agent's next action.
- Include an eval plan and a model card once the specialist becomes shareable.

The test: if the missing piece is perception, ranking, scoring, detection, classification, or domain inference, it may be Tier 3.

## Hierarchical Skill Pattern

When several skills share a domain, consolidate them into one router skill with on-demand subdocs.

Preferred shape:

```text
domain-skill/
  SKILL.md      # lean router and workflow
  shared/
  variant-a/
  variant-b/
  scripts/
  templates/
  assets/
```

The main `SKILL.md` should route the agent:

- Which subdoc to load
- Which script to run
- Which verification path applies

It should not duplicate every detail from the subdocs.

## Skill Hygiene

Good skills:

- Reduce future steering from the user.
- Capture real pitfalls, exact commands, verification steps, and judgment calls.
- Stay lean in the main `SKILL.md`.
- Move bulky detail into references or scripts.
- Consolidate related workflows instead of fragmenting into overlapping entries.
- Make source and ownership obvious.

Avoid:

- Creating skills from theory alone when the workflow has not been battle-tested.
- Creating a huge `SKILL.md` when references or scripts would be cleaner.
- Hiding local conventions inside third-party skill packs.
- Logging secrets or baking private machine paths into shareable docs.

## Decision Checklist

Before writing or editing a skill, ask:

1. Is this durable operational knowledge?
2. Will it reduce future steering?
3. Which tier is the lightest reliable fit?
4. Can related skills be consolidated instead of adding another one?
5. Is repeated mechanical work better handled by a script?
6. Is the missing capability actually ML-shaped and measurable?
7. What verification proves the skill works?

## Promotion Rules

- Start at Tier 1 if the value is judgment.
- Promote to Tier 2 when repeated deterministic work appears.
- Promote to Tier 3 only when there is a measurable capability gap that needs perception, ranking, scoring, detection, classification, or specialist inference.

Do not overbuild. The strongest skill system is lean at the top, mechanical where needed, and ML-backed only when the payoff is real.
