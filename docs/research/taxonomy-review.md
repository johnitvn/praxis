# Taxonomy Review

Adversarial review of the proposed Praxis taxonomy.

## Initial Hypothesis

The initial taxonomy proposed five layers:

```
META-REASONING → METHOD SELECTION → REASONING METHODS → PROBLEM PATTERNS → WORKFLOW
```

With method categories: logical, causal, probabilistic, first-principles, systems, creative, decision, strategic, optimization, risk, planning, learning.

## Review Process

The taxonomy was subjected to an adversarial review asking:

> "If this were intended to be a comprehensive cognitive toolkit for capable AI agents, what important reasoning disciplines, methods, frameworks, patterns, or meta-cognitive capabilities are missing?"

## Findings

### MISSING: Forecasting
The initial taxonomy had `planning/` but no `forecasting/`. Planning is about achieving goals; forecasting is about predicting outcomes. These are distinct reasoning disciplines with different methods. **Added: `forecasting/` category with 4 methods.**

### MISSING: Argumentation
The initial taxonomy had no category for evaluating claims, constructing arguments, detecting fallacies, or evaluating evidence. These are essential reasoning skills for AI agents that must evaluate information quality. **Added: `argumentation/` category with 4 methods.**

### MISSING: Mathematical Reasoning
Formal mathematical reasoning (proof, algebraic manipulation, analytic reasoning) is not covered. **Decision: Merged into logical/**. Mathematical reasoning is a special case of deductive reasoning for AI agents. Formal proof methods are noted as a known gap.

### MERGED: Complexity Thinking → Systems
Complexity thinking (emergence, adaptation, self-organization) is deeply integrated with systems thinking. **Decision: Merged into `systems/` as `emergence-analysis.md`.**

### MERGED: Safety + Reliability → Risk
Safety engineering and reliability engineering are applications of risk analysis methods. **Decision: Merged into `risk/` with `fault-tree-analysis.md` and `threat-modeling.md` covering both.**

### RECLASSIFIED: Debugging, Diagnosis, Troubleshooting
These are patterns (recurring problem structures), not methods (how to reason). They compose multiple methods (abductive + Bayesian + causal). **Decision: Moved to `patterns/` and `workflows/`.**

### RECLASSIFIED: Scientific Method
The scientific method is a workflow that composes multiple methods (hypothesis generation, experimental design, statistical testing, falsification). **Decision: Represented as a composition of methods in `relationships.yaml` rather than a standalone method.**

### RECLASSIFIED: Measurement, Calibration
Measurement is a cross-cutting concern, not a standalone method category. Calibration is meta-reasoning. **Decision: Calibration placed in both `forecasting/` and `meta/`.**

### DUPLICATE: Trade-off Analysis
Appeared in both optimization and decision categories. **Decision: Placed in `optimization/` as the canonical location; cross-referenced from `decision/`.**

### OVERLAPPING: Design Thinking and Creative Reasoning
Design thinking is a specific methodology, not a general reasoning category. **Decision: Placed in `creative/` alongside divergent, convergent, and lateral thinking.**

## Final Taxonomy

### Method Categories (13)
```
logical/          — Deductive, inductive, abductive, analogical, temporal
causal/           — Causal graphs, counterfactuals, interventions, discovery
probabilistic/    — Bayesian, frequentist, statistical, uncertainty quantification
first-principles/ — Decomposition, fundamental analysis, constraint analysis
systems/          — Systems thinking, feedback, networks, emergence
creative/         — Divergent, convergent, lateral, design thinking
decision/         — Expected utility, multi-criteria, under uncertainty, cost-benefit
strategic/        — Game theory, scenarios, strategic analysis, options
optimization/     — Constrained, multi-objective, satisficing, trade-off
risk/             — Risk analysis, premortem, threat modeling, fault trees
planning/         — Hierarchical, contingency, resource, scheduling
forecasting/      — Reference class, calibration, ensembles, superforecasting  [NEW]
argumentation/    — Argument analysis, evidence, fallacies, dialectic  [NEW]
```

### Known Gaps (Noted, Not Filled)
- Ethical reasoning (values-based, stakeholder ethics)
- Formal mathematical proof methods
- Spatial/geometric reasoning
- Negotiation methods
- Communication reasoning (rhetoric, framing)

These gaps are documented in the SKILL.md and README.md. They are not omissions — they are boundary decisions about what constitutes a "reasoning method" vs. a domain-specific application.