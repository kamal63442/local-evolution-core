# Research Plan

## 1. Motivation

Modern AI agents operate inside persistent scaffolds: system prompts, memory, tools, routing logic, evaluation rules, reusable skills, and task-specific workflows. Those components can change even when the underlying frontier model remains fixed.

Local Evolution Core (LEC) studies whether this scaffold-level adaptation can produce durable, generalizable improvements while preserving observability, reversibility, evaluation integrity, and human control.

The project deliberately separates **local recursive / iterative improvement** from model-weight self-modification. The frontier model is treated as immutable; all candidate improvements are external, inspectable artifacts.

## 2. Research questions

1. Do persistent local improvements produce genuine out-of-sample gains rather than memorizing previously observed tasks?
2. Can an agent distinguish a real improvement from a change that exploits weaknesses in its evaluator?
3. How often do evaluator families disagree about whether a candidate is beneficial?
4. Do useful improvements transfer across tasks, agents, or model families?
5. Which safety gates best prevent regressions or unsafe promotion without eliminating useful learning?
6. How quickly do gains saturate, and what failure modes emerge over repeated generations?

## 3. Working hypotheses

These are hypotheses to be tested, not established results.

- **H1:** Persistent scaffold-level improvements can outperform a no-memory/no-persistence baseline on unseen tasks.
- **H2:** Held-out evaluation reduces false promotion compared with self-evaluation alone.
- **H3:** Cross-model judging exposes correlated evaluator bias that is invisible in same-family evaluation.
- **H4:** Explicit quarantine, rollback, and provenance reduce the cost of failed candidate promotion.
- **H5:** Improvement quality will eventually plateau, while evaluator exploitation and overfitting pressures increase with repeated optimization.

## 4. Experimental design

A minimal experiment compares three conditions:

### Baseline

The agent solves tasks without retaining candidate-generated improvements between trials.

### Persistent local improvement

The agent may generate reusable local artifacts and apply them to later tasks.

### Controlled local improvement

Candidate artifacts may persist only after passing predefined evaluation and safety gates, with final human approval.

Trials should use bounded software-engineering or reasoning environments with reproducible inputs and explicit success criteria.

## 5. Baselines

Useful baselines include:

- fixed prompt / fixed tooling
- fixed prompt with ordinary task memory
- persistence without held-out evaluation
- persistence with same-model evaluation only
- persistence with cross-model evaluation

These comparisons help separate the effect of persistence from the effect of stricter evaluation.

## 6. Cross-model evaluation

When the same model family proposes and evaluates an improvement, shared biases can make weak candidates appear stronger than they are.

A cross-model design can assign different roles to independent frontier-model families:

- proposer
- independent evaluator
- adversarial critic
- replication agent

Agreement is useful evidence, but disagreement is also a research signal. The system should record disagreement rather than silently collapse it into a single score.

## 7. Generalization tests

Candidates should be tested on tasks that were not available during proposal generation.

Potential test classes:

- held-out tasks from the same distribution
- distribution-shifted tasks
- adversarial variants
- tasks with changed wording but equivalent goals
- transfer to a second model family
- transfer to a different tool environment

## 8. Ablations

Planned ablations may remove one control at a time:

- no quarantine
- no provenance tracking
- no cross-model evaluator
- no rollback
- no human promotion gate
- no held-out tests
- no resource ceilings

Ablations should reveal which controls materially affect safety or performance.

## 9. Failure modes of interest

- evaluator exploitation / reward hacking
- test-set overfitting
- hidden regression on previously solved tasks
- excessive resource consumption
- brittle strategies that fail under minor distribution shift
- unsafe transfer between contexts
- artifacts that improve evaluator scores without improving underlying task quality
- correlated proposer/evaluator bias

## 10. Planned metrics

No metric below should be interpreted as an existing result unless accompanied by published experimental data.

| Metric | Purpose |
|---|---|
| Task success | Primary outcome quality |
| Regression rate | Harm introduced to prior capability |
| Token usage | Reasoning-cost efficiency |
| Tool-call count | Operational efficiency |
| Evaluator disagreement | Cross-model uncertainty |
| Transfer performance | Generalization across settings |
| Failed-promotion rate | Candidate quality / gate selectivity |
| Rollback frequency | Post-promotion instability |
| OOD performance | Robustness under distribution shift |

## 11. Limitations

Important limitations include:

- evaluator models may share training-data or benchmark biases
- API-model behavior can change over time
- finite task suites cannot prove global safety
- improvements to scaffolding may be difficult to separate from ordinary prompt engineering
- independent research budgets constrain replication scale
- human review itself can introduce subjective bias

## 12. Future work

Potential later work includes:

- larger cross-model replication studies
- formal promotion policies
- stronger adversarial evaluator testing
- provenance graphs for multi-generation artifacts
- automatic detection of evaluator-targeted behavior
- publication-quality benchmark suites
- external replication by independent researchers

## Research integrity

This repository separates **implemented infrastructure**, **planned experiments**, and **validated results**. Claims of recursive or self-improving behavior should only be made after reproducible evidence supports them.