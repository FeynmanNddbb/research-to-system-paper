# Agent Contracts

## Coordination model

The coordinator/planner owns the state file, phase transitions, shared contracts, and final merge. Specialist agents own analysis or implementation within a named boundary. A reviewer is independent of the agent that produced the artifact. No agent may silently change a shared contract to make its own task easier.

## Roles

| Role | Primary question | Typical outputs |
|---|---|---|
| Coordinator/planner | What is the next verified unit of work? | plan, dependencies, state, decisions |
| Requirements analyst | What exactly must be built or demonstrated? | scope, requirement IDs, acceptance rules |
| Domain researcher | What does prior evidence support? | literature matrix, evidence table, gap analysis |
| Data agent | Can the data answer the question reliably? | data contract, audit, feature/data pipeline |
| Algorithm agent | What method is implemented and how is it evaluated? | model/algorithm code, config, metrics |
| Architecture agent | How do components interact in a maintainable system? | architecture, API and persistence contracts |
| Backend agent | How is the domain capability exposed safely? | services, APIs, jobs, auth, tests |
| Frontend agent | How does a user complete the workflow? | pages, states, permissions, UI tests |
| Experiment agent | What evidence can confirm or reject the claims? | registry, runs, tables, figures, logs |
| Academic writer | How do facts become a defensible thesis argument? | outline, sections, citations, claim map |
| Reviewer agent | What could make the result invalid or unsafe? | findings, risk list, gate decision |

## Delegation prompt

Every delegation should include this compact contract:

```text
Role: <specialist role>
Task: <one measurable objective>
Context: <relevant canon and existing artifact paths>
Inputs: <versions, schemas, references, constraints>
Allowed changes: <files/modules the agent may edit>
Must not change: <shared contracts or unrelated files>
Outputs: <artifacts, tests, evidence IDs>
Acceptance: <checks or metrics>
Unknowns: <items to report instead of guessing>
```

## Handoff format

Each agent returns:

1. `Status`: complete, partial, blocked, or needs-review.
2. `Artifacts`: exact paths and version identifiers.
3. `Decisions`: choices made and their rationale.
4. `Evidence`: tests, runs, citations, screenshots, or source locations.
5. `Risks`: remaining limitations and likely downstream impact.
6. `Next`: the smallest next action and its dependency.

Narrative summaries do not replace artifacts. If an agent has no evidence, it must say so.

## Conflict resolution

When agents disagree, classify the conflict:

- **Fact conflict**: return to the source data, proposal, standard, or user confirmation.
- **Contract conflict**: stop downstream work and update the canonical contract once.
- **Implementation choice**: compare tests, maintenance, reproducibility, and scope.
- **Research interpretation**: preserve both interpretations until evidence or user decision resolves them.

The coordinator records the decision and affected artifact versions. The reviewer rechecks any changed downstream claim.
