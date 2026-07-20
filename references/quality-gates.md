# Quality Gates

Use these gates to decide whether the coordinator may advance. A gate is passed only when the required evidence exists; a written intention is not evidence.

## Gate 0: Input integrity

Pass when the source proposal or requirements have been read, source locations are preserved, the workspace has been inventoried, and unavailable inputs are listed. Do not infer missing data or results.

## Gate 1: Scope and research canon

Pass when research questions, system users, non-goals, constraints, deliverables, assumptions, and terminology are explicit. Requirements have IDs and a traceability destination. Contradictions are resolved or escalated.

## Gate 2: Data and feature validity

Pass when field meanings, units, identifiers, missingness, outliers, target coverage, split strategy, feature lineage, and leakage controls are documented. A deterministic small example validates important transformations.

## Gate 3: Model or algorithm validity

Pass when the implementation has a stable input/output contract, a baseline, an evaluation protocol, tests for boundary behavior, and reproducible configuration. Meta-models and learned preprocessing use only permitted training information.

## Gate 4: System integrity

Pass when core user workflows run through the intended interfaces, error and empty states are handled, roles are enforced server-side, long jobs expose state and failures, and artifacts are versioned and traceable.

## Gate 5: Experimental evidence

Pass when experiments answer named research questions using fixed data splits, fair baselines, comparable budgets, recorded seeds, raw outputs, and generated tables/figures. Negative or failed runs are retained in the record.

## Gate 6: Thesis evidence

Pass when methods match the implementation, every numerical result maps to a run/table/figure, literature claims map to sources, and conclusions do not exceed the evidence. Limitations and external-validity boundaries are stated.

## Gate 7: Delivery readiness

Pass when the system can be started or its limitation is documented, tests and experiments have reproducible commands, the requirements matrix has no unexplained high-priority gaps, and the final report lists residual risks and next steps.

## Severity and response

- `P0`: safety, data loss, credential exposure, or fabricated evidence. Stop immediately.
- `P1`: leakage, invalid evaluation, incorrect constraints, authorization bypass, or unsupported thesis conclusion. Fix before advancing.
- `P2`: missing edge case, weak reproducibility, interface drift, or significant maintainability issue. Track and fix before final delivery.
- `P3`: wording, naming, or low-impact cleanup. Track without blocking research progress unless it affects interpretation.

## Final review questions

1. Can each requirement be traced to design, code, test, experiment, and thesis location?
2. Can each thesis result be reproduced from a recorded run and source artifact?
3. Are predicted, simulated, and measured quantities clearly distinguished?
4. Would a new agent know the current state and next action from the artifacts alone?
