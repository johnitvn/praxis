# Changelog

## [1.0.0] - 2026-08-08

### Added
- Initial release of Praxis reasoning skill
- 50+ reasoning methods across 13 categories:
  - Logical reasoning (deductive, inductive, abductive, analogical, temporal)
  - Causal reasoning (causal graphs, counterfactuals, interventions, discovery)
  - Probabilistic reasoning (Bayesian, frequentist, statistical, uncertainty quantification)
  - First principles (decomposition, fundamental analysis, constraint analysis)
  - Systems thinking (systems, feedback, networks, emergence)
  - Creative reasoning (divergent, convergent, lateral, design thinking)
  - Decision methods (expected utility, multi-criteria, under uncertainty, cost-benefit)
  - Strategic reasoning (game theory, scenarios, strategic analysis, options)
  - Optimization (constrained, multi-objective, satisficing, trade-off)
  - Risk (risk analysis, premortem, threat modeling, fault trees)
  - Planning (hierarchical, contingency, resource, scheduling)
  - Forecasting (reference class, calibration, ensembles, superforecasting)
  - Argumentation (argument analysis, evidence, fallacies, dialectic)
- 20+ problem-solving patterns across 7 categories
- 10 composed reasoning workflows
- 20 meta-reasoning capabilities
- Method selection engine (router) with 6 components
- Machine-readable ontology (concepts, methods, patterns, domains, relationships)
- 6 worked examples (software architecture, debugging, product, research, infrastructure, business strategy)
- Comprehensive documentation (SKILL.md, README.md)

### Design Decisions
- Methods are procedural, not descriptive
- Patterns are distinct from methods (methods describe how to reason, patterns describe recurring problem structures)
- Workflows compose methods and patterns without duplicating them
- Meta-reasoning is a separate layer for reasoning about reasoning
- All methods include explicit failure modes, limitations, and verification guidance
- Ontology is machine-readable for automated method selection
- Router supports single method, parallel, chain, loop, and explore-converge composition patterns