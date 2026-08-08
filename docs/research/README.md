# Research

Research backing for the Praxis reasoning skill taxonomy, method selection, and design decisions.

## Research Methodology

The taxonomy and methods were developed through:

1. **Disciplinary survey** — Systematic review of reasoning methods across 20+ disciplines
2. **Adversarial taxonomy review** — Challenge-based identification of omissions, duplicates, misclassifications
3. **Parallel research agents** — Deep-dive research into each method category
4. **Cross-topic consistency review** — Global review for coherence across categories
5. **Adversarial validation** — Challenge-based review of every method for misuse potential

## Research Areas

| Area | Key Sources | Methods Identified |
|------|------------|-------------------|
| [Logical Reasoning](logical-reasoning.md) | Aristotle, Peirce, Gentzen, Gentner | Deductive, inductive, abductive, analogical, temporal |
| [Causal Reasoning](causal-reasoning.md) | Pearl, Spirtes, Glymour, Rubin | Causal graphs, counterfactuals, interventions, discovery |
| [Probabilistic Reasoning](probabilistic-reasoning.md) | Bayes, Laplace, de Finetti, Jaynes | Bayesian, frequentist, statistical, uncertainty quantification |
| [Decision Theory](decision-theory.md) | von Neumann-Morgenstern, Savage, Kahneman-Tversky | Expected utility, multi-criteria, under uncertainty, cost-benefit |
| [Systems Thinking](systems-thinking.md) | Meadows, Forrester, Senge, Holland | Systems, feedback, networks, emergence |
| [Forecasting](forecasting.md) | Tetlock, Kahneman, Armstrong, Silver | Reference class, calibration, ensembles, superforecasting |
| [Risk Analysis](risk-analysis.md) | Kaplan-Garrick, Taleb, Rasmussen, Reason | Risk analysis, premortem, threat modeling, fault trees |
| [Meta-Cognition](meta-cognition.md) | Flavell, Brown, Dunlosky, Dunning-Kruger | Metacognition, bias detection, calibration, verification |

## Key Research Decisions

### Methods vs. Patterns Distinction
Methods describe *how to reason* (procedural). Patterns describe *recurring problem structures* (structural). This distinction prevents duplication and enables clean composition.

### Categories as Dirichlet Boundaries
Method categories are treated as soft boundaries — methods can and do cross-reference across categories. The categories serve navigation, not rigid classification.

### Ontology as Source of Truth
All methods are registered in the machine-readable ontology (`ontology/methods.yaml`) with structured metadata enabling automated method selection.

### Failure Modes Required
Every method documents its failure modes. This was a deliberate design choice: knowing when a method fails is as important as knowing when it works.

### Adversarial Review as Quality Gate
Every method was subjected to adversarial review: "What would make this method produce wrong results?" Methods that couldn't survive this challenge were revised or removed.