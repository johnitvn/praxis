# Praxis

> Practical reasoning methods and patterns for AI agents.

## Purpose

Praxis is a reasoning infrastructure skill. It gives AI agents a structured cognitive toolkit for:

1. **Classifying problems** — What kind of problem is this?
2. **Selecting methods** — Which reasoning approach is appropriate?
3. **Composing methods** — How should methods be combined?
4. **Applying methods** — How do I execute the reasoning?
5. **Verifying results** — Am I right? How would I know if I'm wrong?
6. **Knowing when to stop** — Is this good enough?

## Operating Loop

```
Understand → Classify → Identify unknowns → Select method → Compose → Apply → Challenge → Verify → Decide
```

The loop is adaptive, not fixed. You may:
- Loop back when new information emerges
- Skip steps when the problem is simple
- Escalate depth when stakes are higher than expected
- Stop early when the answer is clear

## Skill Architecture

```
                         META-REASONING
                              │
                      Monitor, verify, challenge
                              │
                       METHOD SELECTION
                              │
                 Classify problem, select method
                              │
                  REASONING METHODS
                              │
            Specific procedures for reasoning
                              │
                     PROBLEM PATTERNS
                              │
          Recurring structures for applying methods
                              │
                         WORKFLOWS
                              │
       Composed sequences for achieving outcomes
```

## Quick Start

### 1. Classify the Problem

Use `router/classify-problem.md` to determine:
- What kind of problem is this?
- What is the uncertainty profile?
- What are the stakes?
- What domain is this in?

### 2. Select a Method

Use `router/select-method.md` to choose the appropriate reasoning method.

### 3. Apply the Method

Follow the method file in `methods/` for the step-by-step procedure.

### 4. Verify

Use `meta/verification.md` and `meta/self-critique.md` to check your work.

### 5. Decide Next Step

Use `router/choose-next-step.md` to determine: continue, switch, gather information, or stop.

## Repository Structure

```
skills/reasoning/
├── SKILL.md              ← You are here
├── README.md             ← Project overview and usage
│
├── ontology/             ← Machine-readable concept registry
│   ├── concepts.yaml     ← Core concept definitions
│   ├── methods.yaml      ← Method registry with metadata
│   ├── patterns.yaml     ← Pattern registry
│   ├── domains.yaml      ← Domain definitions and defaults
│   └── relationships.yaml← Method compositions, substitutions, conflicts
│
├── router/               ← Method selection engine
│   ├── classify-problem.md
│   ├── select-method.md
│   ├── compose-methods.md
│   ├── choose-depth.md
│   ├── choose-next-step.md
│   └── stopping-criteria.md
│
├── methods/              ← Reasoning methods (13 categories, 50+ methods)
│   ├── logical/          ← Deductive, inductive, abductive, analogical, temporal
│   ├── causal/           ← Causal graphs, counterfactuals, interventions, discovery
│   ├── probabilistic/    ← Bayesian, frequentist, statistical, uncertainty quantification
│   ├── first-principles/ ← Decomposition, fundamental analysis, constraint analysis
│   ├── systems/          ← Systems thinking, feedback, networks, emergence
│   ├── creative/         ← Divergent, convergent, lateral, design thinking
│   ├── decision/         ← Expected utility, multi-criteria, under uncertainty, cost-benefit
│   ├── strategic/        ← Game theory, scenarios, strategic analysis, options
│   ├── optimization/     ← Constrained, multi-objective, satisficing, trade-off
│   ├── risk/             ← Risk analysis, premortem, threat modeling, fault trees
│   ├── planning/         ← Hierarchical, contingency, resource, scheduling
│   ├── forecasting/      ← Reference class, calibration, ensembles, superforecasting
│   └── argumentation/    ← Argument analysis, evidence, fallacies, dialectic
│
├── patterns/             ← Problem-solving patterns
│   ├── problem-solving/  ← Hypothesis-driven diagnosis, root cause, troubleshooting, debugging
│   ├── decision-making/  ← Structured, reversible, group decisions
│   ├── research/         ← Literature review, evidence synthesis, knowledge gaps
│   ├── architecture/     ← Trade-off, constraint-driven, quality attribute analysis
│   ├── design/           ← Iterative, constraint-based, user-centered
│   ├── evaluation/       ← Option evaluation, solution assessment
│   └── synthesis/        ← Multi-source synthesis, reconciliation
│
├── meta/                 ← Meta-reasoning capabilities
│   ├── metacognition.md
│   ├── assumption-checking.md
│   ├── bias-detection.md
│   ├── uncertainty.md
│   ├── confidence.md
│   ├── self-critique.md
│   ├── alternative-generation.md
│   ├── perspective-switching.md
│   ├── consistency-check.md
│   ├── completeness-check.md
│   ├── verification.md
│   ├── falsification.md
│   ├── stopping-criteria.md
│   ├── escalation.md
│   ├── information-gathering.md
│   ├── when-to-ask.md
│   ├── when-to-search.md
│   ├── when-to-experiment.md
│   ├── when-to-delegate.md
│   └── epistemic-humility.md
│
├── workflows/            ← Composed reasoning workflows
│   ├── diagnose.md
│   ├── research.md
│   ├── decide.md
│   ├── design.md
│   ├── plan.md
│   ├── optimize.md
│   ├── troubleshoot.md
│   ├── evaluate.md
│   ├── learn.md
│   └── explain.md
│
├── examples/             ← Worked examples showing method selection
│   ├── software-architecture.md
│   ├── debugging.md
│   ├── product-decision.md
│   ├── research.md
│   ├── infrastructure.md
│   └── business-strategy.md
│
└── tests/                ← Test suites
    ├── method-selection/
    ├── pattern-selection/
    ├── method-composition/
    └── regression/
```

## Key Concepts

### Methods vs. Patterns vs. Workflows

- **Method**: How to reason. A systematic procedure. (e.g., Bayesian reasoning)
- **Pattern**: A recurring problem structure. Composes methods. (e.g., Hypothesis-driven diagnosis)
- **Workflow**: A composed sequence for achieving an outcome. (e.g., Diagnose)

### Meta-Reasoning

Meta-reasoning is reasoning about reasoning. It monitors, evaluates, and regulates the reasoning process. The most important meta-reasoning question is:

> **"What would make my current reasoning wrong?"**

### Method Selection

Methods are selected based on:
- Problem type (causal, logical, probabilistic, strategic, etc.)
- Uncertainty profile (aleatoric, epistemic, knightian)
- Stakes (low, medium, high, critical)
- Reversibility (reversible, irreversible)
- Domain (software, infrastructure, product, business, etc.)

## Usage Principles

1. **Problem first, method second**: Classify before selecting.
2. **Match depth to stakes**: Don't over-think small problems or under-think big ones.
3. **Compose deliberately**: Method composition should be intentional, not accidental.
4. **Verify**: Always check your work. The cost of verification is almost always less than the cost of being wrong.
5. **Know when to stop**: A good answer now beats a perfect answer too late.
6. **Be epistemically humble**: State your confidence, your assumptions, and what would change your mind.
7. **Adapt**: The router is a guide, not a straitjacket. Adapt to the problem.