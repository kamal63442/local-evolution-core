# Contributing

Local Evolution Core is currently a research-oriented, documentation-first project. Contributions are welcome when they improve clarity, reproducibility, evaluation quality, or safety reasoning.

## Good contribution areas

- evaluation methodology
- benchmark/task design
- regression testing
- provenance and rollback design
- cross-model evaluation
- safety controls
- experiment reproducibility
- documentation fixes
- clearly scoped reference implementations

## Contribution principles

Please keep contributions:

- evidence-based
- reproducible where practical
- explicit about assumptions
- clear about what is implemented vs. planned
- careful not to overstate results

## Claims

Do not add claims that recursive self-improvement, alignment, or safety has been demonstrated unless the repository includes enough experimental evidence to support the statement.

Planned experiments should be labeled as planned. Preliminary findings should be labeled preliminary.

## Security and safety

Do not submit code or documentation intended to:

- bypass provider security controls
- evade quotas or billing
- expose credentials
- enable unauthorized system access
- remove human promotion controls without an explicitly bounded research justification

## Pull requests

A strong pull request should explain:

1. what changed,
2. why it improves the research or safety design,
3. how it was tested or reviewed,
4. any limitations or unresolved concerns.

For experimental code, include enough context for another contributor to reproduce the behavior where practical.