# brigada

`brigada` is a one-shot multi-agent expert council skill. It turns one concrete question into a council run: 7+ role personas research in parallel, a verifier checks load-bearing claims, an adversarial critic attacks weak points, a gap-fill round closes important holes, and a synthesizer writes one decision document.

Brigada means "brigade" or "crew". It is built for focused decisions and fast understanding, not for ordinary brainstorming or exhaustive multi-hour research.

## What It Does

- Creates a self-contained brief from the current conversation and selected artifacts.
- Assigns expert personas with sharp, checkable questions.
- Runs council members in parallel with artifact reading and web research.
- Adds verification, adversarial critique, and targeted gap-fill.
- Produces a single markdown document under a relative output path such as `./councils/<slug>/brigada-<date>.md`.

## Modes

- `decision`: for "what should we do", option selection, strategy, risk, cost, and tradeoff analysis.
- `understanding`: for a fast map of a topic, facts, schools of thought, disputes, and practical implications.

## Modifiers

- `quick` or `smoke`: smaller council for a cheap test.
- `bigger`: more roles.
- `with preview`: return the proposed role list before the full run.
- `with verification`: enable verifier in understanding mode.
- `OUTPUT_LANG='ru'`: final document and agent outputs in Russian. Default is English.

## Install

Install from the public skills marketplace:

```text
/plugin marketplace add olegpars/oleg-skills-public
```

Then invoke the skill explicitly, for example:

```text
/brigada Decide whether we should build X now or postpone it.
```

Russian trigger phrases are also supported by the skill frontmatter.

## Requirements

- A host that supports Workflow scripts with `agent`, `parallel`, `phase`, `log`, and nested `workflow` for multibrigada.
- Node.js for `engine/extract-doc.mjs`.
- Web tools available to workflow agents when current external facts matter.
- Write access to the chosen output directory.

## Files

- `.claude/skills/brigada/SKILL.md`: orchestration instructions.
- `.claude/skills/brigada/engine/brigada-template.js`: single council workflow template.
- `.claude/skills/brigada/engine/multibrigada-template.js`: batch master workflow.
- `.claude/skills/brigada/engine/extract-doc.mjs`: fallback document extractor.
- `.claude/skills/brigada/references/unattended.md`: generic permission guidance for unattended runs.

## License

MIT.
