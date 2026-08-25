# Technical Section Completeness Audit

Read this reference for System Model, Problem Formulation, Method/Algorithm, and Simulation/Experiments. The goal is close reading and reproducible understanding, not compact coverage.

## Formula and definition inventory

Before drafting, list every equation, formal definition, assumption, algorithm, figure, and table in the active section. Use this inventory internally to prevent accidental omission.

For every material equation, capture:

- Its equation number or nearest label.
- The quantity it defines or constrains.
- Every new symbol, index, set, and unit when inferable.
- Which quantities are observed, predicted, fixed parameters, or decision variables.
- The physical or algorithmic meaning of each term.
- Directional behavior: what changes when a key term rises or falls.
- Its dependency on earlier equations and its consumers later in the current section.

Retain the original formula when it carries information. A prose summary is not a substitute for a model equation.

## System model audit

Trace one task or sample end to end across entities. Verify:

- Entity sets, indices, time scales, topology, and association rules.
- Task generation, partitioning, transmission, execution, and result return.
- Computation, communication, latency, energy, storage, and mobility models.
- Whether all pipeline stages described in prose appear in the equations.
- Whether local constraints and aggregate shared-resource constraints are both present.
- Boundary cases such as no offloading target, full local execution, insufficient capacity, or expired connectivity.
- Simplifying assumptions and the conditions under which they may fail.

## Problem formulation audit

Reconstruct the optimization problem explicitly:

1. Objective and optimization horizon.
2. Decision variables and their domains.
3. Given state and fixed parameters.
4. Each constraint's mathematical and physical meaning.
5. Coupling among variables, users, resources, and time slots.
6. Claimed problem class, such as mixed-integer, non-convex, stochastic, or NP-hard.
7. Any decomposition, relaxation, or approximation and what is preserved or lost.

Check index consistency, missing association multipliers, incorrect or incomplete summations, redundant or absent constraints, undefined symbols, mismatches between notation tables and equations, and claims that do not follow from the formulation. Explain the intended reading before labeling a concern.

## Algorithm audit

Translate each algorithm into an executable mental model:

- Inputs, required state, outputs, and initialization.
- Order of operations, loops, branches, and stopping conditions.
- Offline training versus online inference or adaptation.
- Objective, reward, loss, update rule, solver, or selection rule.
- Update frequency and time scale of every decision.
- Information exchanged among actors and whether it is local or global.
- Feasibility enforcement and behavior when no feasible action exists.
- Stated complexity and what variables it scales with.
- Formal guarantees and the assumptions required for them.

Cross-check pseudocode against the surrounding equations and prose. Do not assume a named algorithm supplies missing implementation details.

## Simulation and experiment audit

Extract enough information to understand what was actually tested:

- Simulator, testbed, dataset, trace, scenario geometry, and randomization.
- Hardware and network assumptions.
- Workloads, model architectures, task arrival process, and mobility model.
- All material parameter values, ranges, defaults, and units.
- Training and evaluation split, episodes, epochs, time slots, seeds, repetitions, and uncertainty reporting when stated.
- Baseline name, original source, adaptation to this paper, and tuning fairness.
- Metric formula or success criterion, aggregation method, and whether higher or lower is better.
- Meaning of every material figure axis, curve, table, and shaded region.
- Ablations that isolate each claimed contribution.

For each result, separate:

1. **Claim:** what the authors say the result demonstrates.
2. **Evidence:** the figure, table, metric, trend, or exact value supporting it.
3. **Interpretation:** why the mechanism could produce that result.
4. **Limitation:** what remains untested or confounded.

Flag missing reproducibility details rather than inventing defaults. Check whether the tested parameter range matches the motivating real-world setting and whether trajectory, convergence, overhead, sensitivity, and no-component comparisons are present when needed by the paper's claims.

## Section gate

Conclude with unresolved questions and reading notes for the active section. Then stop. Continue discussing and revising this section until the user explicitly asks to advance; do not begin extracting or summarizing the next section on your own.
