# Paper Review Skill

A reusable Codex skill for close-reading research papers one section at a time and turning them into clear, structured, and critical review notes.

The skill reads the target paper as the primary source, explains equations and methods in context, separates author claims from interpretation and reviewer concerns, and adapts its output to the conventions already present in the workspace.

## What it supports

- Section-by-section paper walkthroughs
- System model and equation explanations
- Method and algorithm reconstruction
- Related-work comparisons
- Experiment and ablation analysis
- Paper-specific terminology research
- Reviewer-oriented consistency checks
- Gated chapter progression that waits for the reader before advancing
- Formula-complete review of system models, optimization problems, algorithms, and simulations

The default output language is Traditional Chinese. Existing repository conventions take precedence.

## Structure

```text
paper-review/
├── SKILL.md
├── agents/
│   └── openai.yaml
├── references/
│   ├── section-guide.md
│   └── technical-review.md
├── LICENSE
└── README.md
```

`SKILL.md` contains the shared workflow. `references/section-guide.md` is loaded only when a detailed chapter or full-paper review needs section-specific guidance.
`references/technical-review.md` adds a strict completeness audit for formula-heavy and simulation-heavy sections.

## Install locally

Clone or copy this repository into the Codex skills directory:

```text
$CODEX_HOME/skills/paper-review
```

If `CODEX_HOME` is not set, use the skills directory under your local `.codex` home.

Invoke it explicitly with a prompt such as:

```text
Use $paper-review to explain the system model of this paper in Traditional Chinese.
```

The skill also allows implicit invocation for paper-review tasks.

## Publish or upload

The project root is already a complete skill directory. It can be archived as a ZIP without changing the folder structure. The [OpenAI Skills API](https://developers.openai.com/api/reference/python/resources/skills/methods/create) accepts a skill directory upload or a ZIP file.

## Design principles

- The paper remains the primary source.
- External research is used for verification and paper-specific terminology, not as a substitute for the paper.
- Equations are explained semantically, including variables, constraints, physical meaning, and possible inconsistencies.
- Paper statements, reasonable interpretations, and reviewer concerns are kept distinct.
- Notes are incremental and preserve previously completed work.
- The agent stops at the current section and advances only after explicit reader confirmation.

## License

MIT
