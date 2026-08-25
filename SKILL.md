---
name: paper-review
description: Read research papers incrementally, one section at a time, and turn equations, models, algorithms, simulations, terminology, and reviewer concerns into rigorous Traditional Chinese review notes. Use for chapter-by-chapter paper walkthroughs, paper-specific term explanations, or critical paper review; do not use for a generic literature search without a target paper.
---

# Paper Review

Produce notes that help the reader understand, explain, and critique the target paper without repeatedly rereading the source.

## Establish the local convention

Before writing, inspect the target paper, existing notes, and nearby instructions. Reuse the repository's naming, language, depth, citation style, and output locations. When no convention exists, use these defaults:

- Write section notes to `POINT/<Section Name>.md`.
- Write paper-specific terminology to `PROPER_NOUN/<Section Name>.md`.
- Use Traditional Chinese; retain English only for standard technical terms, acronyms, variable names, and wording whose translation would lose precision.
- Do not reproduce the English section verbatim unless the user asks or exact wording is needed for analysis.

Treat the paper as the primary source. External sources provide background or verification; they must not silently replace the paper's definitions.

## Use gated, section-by-section reading

Treat the user's current section as the active reading scope. Follow the paper in order by default—Abstract, Introduction, Related Work, System Model, Method, Simulation, and Conclusion—but do not advance merely because the current note is complete.

- Read and analyze only the requested section.
- Inspect a later page only when necessary to locate the section boundary, recover a continued formula, or resolve an explicit cross-reference. Do not summarize or pre-process the later section.
- After writing the current note, stop and let the user question, challenge, or revise the interpretation.
- Update the current note when discussion resolves an ambiguity or exposes a mistake.
- Enter the next section only after the user explicitly requests it or clearly confirms readiness to continue.

The output of each turn should support close reading, not maximize coverage. Never turn a request for one chapter into a whole-paper summary.

## Read before explaining

Locate the complete requested section, including text continued across pages, figures, tables, algorithms, footnotes, and referenced equations. PDF extraction can scramble columns, symbols, subscripts, or reading order; cross-check adjacent pages and visual structure when the extracted text is ambiguous.

Identify the section's argumentative role before summarizing it:

- What problem or decision does this section introduce?
- What are its inputs, outputs, assumptions, and constraints?
- How does it connect to the preceding and following sections?
- What must a reader understand here to follow the rest of the paper?

For a substantial chapter, read [references/section-guide.md](references/section-guide.md) and apply only the current section's guidance. For System Model, Problem Formulation, Method/Algorithm, or Simulation/Experiments, also read [references/technical-review.md](references/technical-review.md) and use its completeness audit.

## Explain at the right depth

Lead with a one-sentence takeaway. Organize the explanation by concepts and dependencies rather than mirroring every source paragraph.

For each important mechanism, explain:

1. What it does in this paper.
2. Why the paper needs it.
3. What information it consumes and what decision or result it produces.
4. How it interacts with the other components.

Use a small example when symbols alone obscure the operation. Use tables only for repeated mappings, such as variables, baselines, constraints, or method comparisons.

Scale detail to complexity. Abstracts, introductions, and conclusions may use compact synthesis. System models, problem formulations, algorithms, and simulations require close reading: retain their operative definitions, formulas, decision rules, experimental settings, and dependencies even when the resulting note is substantially longer.

## Explain equations semantically

In technical sections, first inventory the numbered and unnumbered formulas before drafting. Preserve every equation that defines a variable, system relationship, objective, constraint, loss, update rule, allocation rule, complexity result, or evaluation metric. Omit only algebraic repetition that adds no new definition, and say when a derivation is intentionally compressed. For each retained equation:

- State its purpose in plain language.
- Define variables at first use, including units when inferable.
- Explain how increasing or decreasing key terms changes the result.
- Connect it to the physical system or algorithm.
- Explain the role of each constraint, not merely restate it.

Likewise, preserve formal definitions, assumptions, algorithm inputs and outputs, pseudocode decision branches, simulation parameters, baseline definitions, and metric definitions. Do not replace these with a high-level narrative.

Do not fabricate missing notation or silently repair the paper. If a formula, notation table, prose definition, or constraint appears inconsistent, first explain the intended interpretation, then label the discrepancy as a reading note.

## Separate explanation from critique

Maintain three evidence levels:

- **Paper statement:** directly supported by the paper.
- **Interpretation:** a reasonable explanation inferred from the model or context.
- **Review concern:** a possible inconsistency, omission, unsupported claim, or evaluation gap.

Never present an interpretation as an explicit author claim. Keep ordinary chapter notes readable; place detailed concerns in a clearly named section such as `閱讀時需注意` or in the repository's review-question file when that convention exists.

Check at least the task-relevant items below:

- Objective, decision variables, and constraints agree with the prose.
- Per-node limits also enforce aggregate capacity when multiple users share a resource.
- Timing assumptions agree across the system model and algorithm.
- Claimed end-to-end cost includes all described pipeline stages, or omissions are disclosed.
- Variables described as dynamic are actually updated at the stated frequency.
- The method's claimed novelty is tested by suitable baselines and ablations.
- Experimental metrics support the claims made in the introduction and conclusion.

Do not turn every modeling simplification into a flaw. Explain its purpose, what it excludes, and when it could affect validity.

## Explain proper nouns in paper context

When the user requests terminology research, browse authoritative or primary sources. Prefer original papers, publisher pages, standards, and official documentation. Explain only the term's role in the target paper:

- Give a compact definition.
- Describe the paper-specific actors, inputs, outputs, and timing.
- State what problem it solves here and what it does not do.
- Relate it to neighboring components in one short flow when useful.
- Add direct source links near a short reference list.

Avoid a broad textbook history unless requested. For example, a diffusion model used for decision trajectories should be explained as a planner or generator of decisions, not mainly as an image generator.

## Write incrementally and preserve prior work

Handle the requested section only unless the user asks for a full-paper pass. Create or update the corresponding note rather than rewriting completed notes. Preserve useful existing content and avoid duplicating definitions already available in `PROPER_NOUN`; link or briefly reference them instead.

Discussion is part of the review process. When the user raises a question, answer from the current section and amend the note if the resolved understanding is reusable. Do not use the question as a cue to move forward.

Before finishing, verify that the note:

- Covers the complete requested section.
- Accounts for every material formula, definition, algorithm step, figure, table, or simulation setting in technical sections.
- Uses notation consistently with the paper.
- Makes the section understandable without the English original.
- Distinguishes paper content from commentary.
- Contains no unsupported numerical claim or citation.
- Fits the style and file organization of the existing review.
- Stops at the current section boundary.
