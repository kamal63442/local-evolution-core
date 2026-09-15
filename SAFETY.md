# Safety Model

Local Evolution Core (LEC) is designed to study iterative agent improvement under explicit control boundaries. The project is not intended to create unrestricted autonomous self-modification.

## Safety objectives

The system should keep candidate changes:

- **bounded** — resource and scope limits are explicit
- **observable** — actions and promotion evidence are recorded
- **inspectable** — improvements exist as human-readable or reviewable artifacts where practical
- **reversible** — promoted changes can be rolled back
- **attributable** — provenance links candidates to their source and evaluation history
- **human-controlled** — final promotion is not automatic

## Explicit exclusions

The research does not require or endorse:

- model-weight self-modification
- bypassing model-provider security controls
- quota or billing bypass
- credential theft or unauthorized access
- unrestricted external side effects
- uncontrolled replication or propagation
- automatic self-promotion based solely on the proposing agent's own judgment

## Candidate quarantine

A candidate improvement should not immediately enter the active runtime.

Instead, it moves through a quarantined state where it can be:

1. inspected,
2. evaluated on held-out tasks,
3. compared with the current baseline,
4. checked for regressions,
5. reviewed for integrity and scope,
6. explicitly promoted or rejected.

## Separation of roles

Where feasible, proposal and evaluation should be separated.

A stronger design uses distinct roles such as:

- proposer
- evaluator
- adversarial critic
- objective test harness
- human reviewer

Cross-model evaluation is useful because proposer and evaluator systems from the same model family may share correlated failure modes.

## Resource ceilings

Each experiment should define explicit limits on resources such as:

- number of iterations
- token budget
- wall-clock time
- tool calls
- filesystem scope
- network scope
- concurrency

Exceeding a ceiling should terminate or quarantine the experiment rather than silently expanding its authority.

## Provenance and telemetry

Candidate artifacts should retain enough metadata to answer:

- What generated this change?
- Which version did it modify?
- Which evaluations were run?
- What passed or failed?
- Who approved promotion?
- What version replaced it later?

Telemetry should support audit and comparison without requiring hidden reasoning traces.

## Integrity protection

Protected components should not be silently rewritten by the same process that benefits from passing evaluation.

Examples include:

- sealed tests
- immutable reference baselines
- promotion policy
- integrity checks
- provenance history
- audit records

The goal is to make evaluator tampering materially harder than ordinary candidate generation.

## Rollback

Promotion is not proof of permanent safety.

Every promoted artifact should have a documented predecessor so regression can trigger rollback. Rollback criteria should be defined before deployment where possible.

## Human promotion gate

Final promotion should remain an explicit human decision during the research phase.

A model may recommend promotion, but recommendation and authorization are distinct actions.

## External actions

Research trials should prefer bounded software-engineering, reasoning, or simulated environments. External actions that could affect real users, accounts, systems, or finances require additional authorization and should not be treated as ordinary evaluation steps.

## Safety evidence

Safety claims should be proportional to evidence. Passing a finite test suite demonstrates performance on that suite; it does not establish universal safety.

This repository therefore avoids claims that LEC has solved recursive self-improvement safety or alignment. The goal is narrower: develop and evaluate controls that make scaffold-level iterative improvement easier to inspect, test, constrain, and reverse.