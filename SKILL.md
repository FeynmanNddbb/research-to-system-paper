---
name: multi-agent-research-to-system-paper
description: Coordinate multiple specialized agents to turn a thesis proposal, opening report, project brief, or research requirements into a validated research plan, implementable software system, reproducible experiments, and evidence-grounded master's thesis materials. Use for Chinese or English requests such as 根据开题报告做系统和论文、从科研需求搭建项目、研究方案到代码与论文、multi-agent thesis project, or continuing an existing research repository into system and paper deliverables.
---

# Research-to-System-and-Paper Skill

## Purpose

Use this skill as a project coordinator. Convert an opening report or research requirement into four connected products:

1. A traceable research and engineering plan.
2. A working system whose data, algorithm, interface, and deployment decisions are explicit.
3. Reproducible experiments that test the research claims.
4. A master's thesis package whose methods, results, and conclusions are supported by evidence.

The skill is domain-agnostic. Infer the domain, data modality, technical stack, evaluation metrics, deployment context, and university formatting rules from the input. Do not assume a particular model, framework, database, or scientific claim.

## Invocation Modes

Select the smallest mode that matches the request:

- `bootstrap`: start from an opening report, proposal, task brief, or idea and create the project foundation.
- `continue`: inspect an existing repository and advance the next unfinished phase without destroying user work.
- `system-only`: derive, implement, test, and document the research software system; keep a minimal experiment and thesis traceability record.
- `paper-only`: build the argument map, evidence table, chapter structure, and grounded prose from supplied results and sources; do not invent implementation.
- `integrated`: run the complete chain from requirements through system, experiments, and thesis materials.
- `audit`: review an existing project for requirements traceability, reproducibility, scientific validity, software quality, and thesis consistency.

Use `integrated` when the user says “从开题报告得到系统和论文” or asks for the complete project. Use `continue` when project files and previous agents already exist. If the request is ambiguous, inspect the workspace and choose the mode that avoids unnecessary work.

## Non-Negotiable Rules

- Read the current project `AGENTS.md` and relevant `.codex/context/` files before changing files. User and repository instructions have priority over this skill.
- Preserve existing user changes. Inspect before editing, use the repository's conventions, and keep changes scoped.
- Separate confirmed facts, assumptions, open questions, literature evidence, implementation decisions, and measured results.
- Do not fabricate sample counts, field names, thresholds, model scores, citations, system capabilities, or completed experiments.
- Use configuration or a clearly marked `TBD` item for missing information that does not block progress. Escalate missing information that changes architecture, safety, data validity, or the thesis claim.
- Establish contracts before implementation: input schema, output schema, data split, model interface, API behavior, experiment metrics, and thesis claims.
- Prevent leakage: split by the relevant unit before fitting learned preprocessing, feature selection, hyperparameters, or meta-learners. Do not use test data to make design choices.
- Never write a result paragraph before its result can be traced to a run, table, figure, log, or verified source.
- Treat a predicted or simulated result as such; do not call it an industrial measurement or validation without evidence.
- Do not publish, deploy, delete data, initialize external services, or send external messages unless the user explicitly authorizes it.

## Workflow

### Phase 0: Intake and workspace inventory

Assign the coordinator/planner agent to:

1. Read the proposal and extract the research problem, objectives, research questions, expected innovations, data, methods, constraints, system users, deliverables, and academic requirements.
2. Inventory the repository, existing code, datasets, notebooks, models, figures, paper drafts, tests, and current worktree changes.
3. Record what is known, unknown, contradictory, already completed, and out of scope.
4. Select the invocation mode and create a short execution plan with dependencies and gates.

If the source is PDF, DOCX, spreadsheet, or another structured artifact, use the appropriate document/spreadsheet/PDF skill or parser and preserve source locations for later citation.

### Phase 1: Research canon and requirement traceability

Run requirements analysis and domain research in parallel when possible. Consolidate their results before design.

Create or update:

- `00_scope.md`: problem, users, boundaries, research questions, success criteria, and non-goals.
- `01_research_canon.md`: confirmed facts, source references, assumptions, and forbidden claims.
- `02_requirements_traceability.md`: each requirement mapped to a design element, code module, test, experiment, and thesis section.
- `03_evidence_table.md`: claim, evidence, source/run ID, confidence, and allowed wording.

For each requirement, distinguish research requirements from product requirements. A sentence such as “improve prediction” must become a measurable comparison, data split, metric, baseline, and acceptance rule.

### Phase 2: Argument, architecture, and contracts

After the canon is stable, assign architecture, data, algorithm, and experiment agents to produce:

- An argument map: problem -> gap -> method -> evidence -> contribution.
- A data contract: entities, fields, units, identifiers, target variables, missingness, split strategy, and provenance.
- A feature/model contract: feature lineage, preprocessing, training interface, inference schema, versioning, and failure behavior.
- A system architecture: modules, data flow, API boundaries, roles, long-running jobs, persistence, observability, and deployment assumptions.
- An experiment registry: research question, hypothesis, factors, baselines, metrics, random seeds, budget, artifacts, and stopping rules.
- A thesis outline whose sections consume named evidence rather than promises.

Do not start broad implementation while these contracts contain unresolved contradictions. Continue with a narrow prototype only when its assumptions are explicit and isolated.

### Phase 3: Vertical implementation slices

Implement in slices that each produce usable evidence:

1. Data ingestion/audit and the smallest valid feature or data pipeline.
2. Baseline model or core domain computation with tests.
3. The proposed method, with ablations and comparison hooks.
4. Optimization, decision logic, or domain workflow with constraint tests.
5. Backend service and persistence around stable algorithm interfaces.
6. Frontend workflow, roles, error states, and result visualization.
7. Packaging, logging, configuration, and deployment checks.

Delegate non-overlapping slices to specialized agents. The coordinator owns shared contracts and resolves conflicts. Each slice must report changed files, tests, limitations, and evidence IDs.

### Phase 4: Experimental verification

The experiment agent runs the registry, not the implementation agent's intuition. Require:

- A fixed data and code version.
- A justified train/validation/test or cross-validation protocol.
- Comparable baselines, metrics, budgets, and repeated seeds.
- Raw predictions, optimization histories, logs, and generated figures.
- Error analysis, negative results, and known validity limits.

If the proposal claims a method is better, test that claim directly. If results do not support it, update the claim and thesis narrative rather than hiding the result.

### Phase 5: Thesis material production

Use the research writer only after evidence and argument maps exist. Produce in this order:

1. Methods and system design from the frozen contracts.
2. Experiment protocol from the experiment registry.
3. Results from generated tables and figures.
4. Discussion that separates observation, interpretation, limitations, and implications.
5. Abstract, introduction, conclusion, and contribution statements after the evidence is stable.

Every result claim must link to an experiment ID or artifact. Every literature claim must link to a source. Keep a list of claims that remain planned, unsupported, or conditional.

### Phase 6: Independent review and integration

Run a reviewer agent with the raw artifacts and relevant contracts. It must check data leakage, invalid metrics, unsupported claims, API/schema drift, authorization, error handling, reproducibility, and mismatch between code, figures, and prose.

Resolve P0/P1 issues before proceeding. For lower-risk issues, record an owner, impact, and follow-up. Re-run affected tests and experiments after any change to data splits, feature logic, model code, objective functions, or result-generation scripts.

### Phase 7: Delivery

Deliver a compact status report containing:

- Mode, current phase, and completed gates.
- System implementation and runnable entry points.
- Dataset, model, experiment, and document versions.
- Main evidence-backed findings and their boundaries.
- Tests and experiment commands with outcomes.
- Open questions, technical debt, and recommended next task.

For an incomplete project, deliver the strongest verified subset and clearly label what remains planned. Do not present a scaffold as a finished system or a proposed experiment as a result.

## Multi-Agent Coordination

Use the roles and handoff contract in `references/agent-contracts.md`. Prefer parallel work only after shared inputs are frozen:

- Parallel at intake: workspace inventory, source extraction, and literature discovery.
- Parallel after contracts: data/feature work, algorithm prototype, architecture design, experiment registry, and thesis outline.
- Parallel after interfaces: backend, frontend, tests, experiment execution, and methods writing.
- Sequential gates: canonical facts before architecture; data contract before modeling; model contract before optimization; measured results before results writing; reviewer approval before final delivery.

If the runtime provides subagents, give each one a narrow task prompt with explicit inputs and outputs, and collect artifacts rather than long narrative summaries. Do not let two agents edit the same canonical file concurrently. If subagent execution is unavailable, execute the same roles sequentially in one context and preserve the same handoff artifacts.

## Required Artifact Set

For `bootstrap` or `integrated`, create the minimum foundation described in `references/artifact-contracts.md`. Adapt paths to an existing repository instead of creating duplicate structures. At minimum, maintain:

- Scope and research canon.
- Requirements-to-code/test/experiment/paper traceability.
- Argument map and evidence table.
- Data/model/system/experiment contracts.
- A thesis outline and result-source index.
- A state file recording phase, gate status, versions, risks, and next action.

## Stop and Escalate

Pause implementation and ask the user when any of the following cannot be resolved from local artifacts:

- The proposal contains mutually incompatible objectives or target definitions.
- Required data, authorization, credentials, or external services are missing.
- A decision would change the research question, core architecture, publication claim, or data governance.
- The requested result requires fabricated measurements, citations, or performance numbers.
- No defensible split or evaluation protocol can be constructed from the available data.

Otherwise, make the smallest reversible assumption, record it, and continue.

## Reference Navigation

- Read `references/agent-contracts.md` when delegating work or merging agent outputs.
- Read `references/artifact-contracts.md` when bootstrapping a project or deciding where to store traceability artifacts.
- Read `references/quality-gates.md` before declaring a phase complete or writing a final thesis conclusion.
