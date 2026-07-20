# Artifact Contracts

## Purpose

These artifacts make a multi-agent project cumulative rather than conversational. Use an existing project location when one exists. Do not duplicate a repository's established documentation structure just to match these names.

## Foundation artifacts

### `00_scope.md`

Record:

- problem and users;
- research questions and hypotheses;
- system capabilities and non-goals;
- data and resource boundaries;
- expected system, experiment, and thesis deliverables;
- success criteria and unresolved decisions.

### `01_research_canon.md`

Use a table with `Item`, `Type` (fact/assumption/question/constraint), `Source`, `Confidence`, `Owner`, and `Last checked`. Include forbidden claims and terminology decisions.

### `02_requirements_traceability.md`

Each row should contain:

```text
REQ-ID | requirement | source | design/module | code path | test ID
      | experiment ID | thesis section | status | evidence path
```

Requirements without a code, test, experiment, or thesis destination must be explicitly marked as deferred or out of scope.

### `03_evidence_table.md`

Use:

```text
CLAIM-ID | claim | claim type | source/run ID | artifact/table/figure
         | strength | allowed wording | dependent assumptions
```

Keep literature evidence and project-generated evidence distinguishable.

### `04_argument_map.md`

Map `problem -> gap -> research question -> method -> experiment -> result -> contribution`. Mark each edge as supported, planned, or missing. Do not write the final conclusion while the result edge is planned.

### `05_contracts.md`

Link the data contract, model/algorithm contract, API contract, experiment contract, and thesis section contract. Each contract must define inputs, outputs, units/types, versioning, failure behavior, and validation.

### `state.md`

Record current mode, phase, gate status, artifact versions, active agents, risks, blockers, last verified command, and next action. Keep it concise enough to update after every meaningful handoff.

## Recommended system artifacts

- `docs/architecture.md`: components, data flow, deployment, roles, jobs, persistence, and observability.
- `docs/api.md`: resources, request/response schemas, errors, authentication, and examples.
- `docs/data-dictionary.md`: fields, units, provenance, validation, and target definitions.
- `docs/test-plan.md`: functional, integration, permission, performance, and algorithm regression tests.
- `algorithm/` or the repository's equivalent: reusable domain logic isolated from the UI.
- `experiments/registry/`: machine-readable configurations and run metadata.

## Recommended thesis artifacts

- `paper/outline.md`: chapter and section contracts.
- `paper/figure-index.md`: figure/table ID, source run, script, conclusion, and status.
- `paper/citation-map.md`: claim-to-source mapping.
- `paper/drafts/`: prose only after the relevant evidence or method contract exists.

## Versioning rule

Every model, result, figure, recommendation, and thesis number should point to a data version, code version, configuration, and run ID. If version control is unavailable, record file hashes and generation timestamps. Never overwrite a published result without preserving the prior source.
