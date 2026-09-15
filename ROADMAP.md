# Roadmap

This roadmap separates infrastructure work from experimental claims. A phase should only be marked complete when supporting evidence is available.

## Phase 0 — Safety scaffolding and integrity controls

Goal: establish the minimum control surface required before live experimentation.

Scope:

- candidate quarantine
- versioned artifacts
- provenance records
- integrity checks
- rollback path
- bounded telemetry
- resource ceilings
- explicit human promotion gate

Status: **in progress / validation-oriented**. Public documentation does not treat this as proof of safe recursive improvement.

## Phase 1 — Baseline characterization

Goal: establish how the agent performs without persistent candidate-generated improvements.

Planned work:

- define task suites
- define success criteria
- measure baseline task success
- measure token/tool usage
- characterize run-to-run variance
- freeze baseline versions for later comparison

## Phase 2 — Candidate generation

Goal: allow the system to propose local improvements without automatically activating them.

Candidate classes may include:

- prompt revisions
- reusable strategies
- tool-use policies
- memory structures
- workflow templates
- evaluation helpers

All candidates remain quarantined by default.

## Phase 3 — Held-out evaluation

Goal: test whether candidate improvements generalize beyond the tasks that produced them.

Planned work:

- held-out tasks
- sealed regression tests
- repeated trials
- predefined promotion thresholds
- regression analysis

## Phase 4 — Cross-model evaluation

Goal: reduce dependence on a single model family as both proposer and judge.

Planned work:

- independent evaluator family
- adversarial critic role
- evaluator-disagreement logging
- same-family vs cross-family comparison
- replication of accepted candidates across model families

## Phase 5 — Transfer experiments

Goal: determine whether improvements remain useful outside their original context.

Potential tests:

- new task domains
- changed tool environments
- second agent runtime
- different model family
- distribution-shifted inputs

## Phase 6 — Adversarial evaluator testing

Goal: test whether the system can detect candidates that target the evaluation process rather than the underlying task.

Planned work:

- proxy-metric exploitation tests
- evaluation-file integrity checks
- parser/formatting adversarial cases
- hidden-regression scenarios
- persuasive-but-incorrect candidate critiques

## Phase 7 — Long-horizon iteration studies

Goal: study repeated generations rather than isolated candidate improvements.

Questions include:

- Do gains saturate?
- Does regression accumulate?
- Does evaluator exploitation pressure increase over time?
- Does artifact complexity grow faster than measurable benefit?
- How often is rollback needed?

## Phase 8 — Publication-quality reporting

Goal: produce reproducible research artifacts if the experiments yield meaningful results.

Expected outputs:

- frozen task/evaluation definitions
- experiment manifests
- model/version metadata where available
- aggregate metrics
- negative results
- failure-case analysis
- limitations
- reproducibility notes

## Progress policy

Roadmap labels are descriptive, not promotional. A phase being implemented does not imply its research hypothesis has been validated. Results should be reported separately from infrastructure status.