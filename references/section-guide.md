# Section-Specific Paper Review Guide

Read this reference for a full-paper review or when producing detailed notes for one of the sections below. Apply only the relevant guidance.

## Abstract

Extract the problem, gap, method, principal mechanism, evaluation setting, and strongest quantified result. Clarify what the reported improvement is measured against when the abstract makes that information available. Avoid expanding every acronym into a separate subsection.

## Introduction

Reconstruct the argument rather than paraphrasing paragraph by paragraph:

1. Application context and practical need.
2. Technical bottleneck.
3. Existing solution families.
4. Precise unresolved gap.
5. Proposed insight and why it addresses the gap.
6. Contributions and claimed evidence.

Check whether the gap logically requires the proposed method and whether the contribution list contains genuinely distinct items.

## Related Work

Group papers by technical approach or decision scope. For each group, state what it solves, its shared limitation, and how the target paper positions itself. Identify the closest work explicitly and compare it on the dimensions that support the novelty claim. Avoid a paper-by-paper bibliography dump.

Useful comparison dimensions include decision variables, centralized versus distributed operation, temporal granularity, online cost, mobility assumptions, guarantees, feedback, and evaluation setting.

## System Model and Problem Formulation

Explain in dependency order:

1. Entities, sets, and time model.
2. Task or data lifecycle.
3. Decision variables.
4. Computation, communication, latency, energy, or cost models.
5. Objective.
6. Constraints and their physical meaning.
7. Why the problem is difficult.
8. Any decomposition used by later sections.

Include a compact scenario example. Do not omit definitions or formulas for brevity. Check units, indices, summation domains, binary versus continuous variables, aggregate capacity, feasibility when no server is selected, and whether all described pipeline stages appear in the objective. Use the technical completeness audit in [technical-review.md](technical-review.md).

## Method or Algorithm

Start with the end-to-end flow. Then explain each stage by its input, transformation, output, update frequency, and dependency on other stages. Translate pseudocode into an operational sequence rather than repeating every line.

For learning methods, distinguish offline training, online inference, online adaptation, reward or loss, and the source of training data. For optimization methods, distinguish the original problem, relaxation or decomposition, solver, guarantees, and runtime complexity.

Check that training-time information is available at deployment time and that claimed distributed behavior does not secretly require global state. Preserve algorithm inputs, outputs, loops, decision branches, losses, update rules, stopping conditions, and stated complexity. Use the technical completeness audit in [technical-review.md](technical-review.md).

## Theoretical Analysis

State each theorem or property in plain language, list its assumptions, and explain why it matters to the proposed system. Summarize the proof idea unless a line-by-line derivation is requested. Distinguish formal guarantees from empirical observations.

## Simulation or Experiments

Organize notes around the claim-evidence relationship:

- Environment, datasets or traces, hardware, workloads, and parameter ranges.
- Baselines and what component each comparison isolates.
- Metrics and how success is defined.
- Main results, sensitivity analyses, ablations, convergence, overhead, and statistical variation.
- Whether the tested conditions match the motivating scenario.

Record exact numbers only when supported by a figure, table, or text. Check for missing no-component variants, unfair tuning, unclear baseline provenance, absent trajectory or qualitative evidence, narrow parameter sweeps, and claims not isolated by an ablation.

Do not summarize the section only as “the proposed method performs best.” Preserve the simulator or testbed, datasets or mobility traces, model workloads, hardware assumptions, parameter values and ranges, training protocol, baseline implementations, metric definitions, figure axes, and ablation settings. Explain each material result as claim, evidence, and limitation. Use the technical completeness audit in [technical-review.md](technical-review.md).

## Conclusion

Summarize the achieved result, not the introduction again. Compare the conclusion's claims with the demonstrated evidence. Note limitations or future work only when stated by the authors or clearly labeled as reviewer interpretation.

## Reusable Final Checklist

- Can the reader state the paper's problem, gap, method, and evidence in one minute?
- Can the reader trace one task from input through execution to output?
- Can the reader explain every optimized variable and major constraint?
- Is the closest baseline clearly distinguished from the proposed method?
- Are assumptions, omissions, and possible inconsistencies visible without overwhelming the explanation?
- Are all external explanations tailored to this paper rather than generic definitions?
- Has the review stopped at the requested section instead of advancing automatically?
