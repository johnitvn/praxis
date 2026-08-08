# Router: Problem Classification

Classify the problem to determine which reasoning methods are appropriate.

## Purpose

Map a problem description to the reasoning categories, methods, and patterns that are most likely to be useful.

## Procedure

### Step 1: Identify the Problem Type

Ask these classification questions:

| Question | If Yes | If No |
|----------|--------|-------|
| Is the problem about what IS true? | Logical, Probabilistic | — |
| Is the problem about what CAUSED something? | Causal | — |
| Is the problem about what WILL happen? | Forecasting, Probabilistic | — |
| Is the problem about what TO DO? | Decision, Strategic | — |
| Is the problem about HOW to achieve something? | Planning, Optimization | — |
| Is the problem about WHY something happens? | Causal, Systems | — |
| Is the problem about what COULD be? | Creative, Strategic | — |
| Is the problem about what is RIGHT? | Argumentation, Decision | — |
| Is the problem about risk or safety? | Risk | — |
| Is the problem about interconnected parts? | Systems | — |
| Is the problem about breaking down complexity? | First-Principles | — |
| Is the problem about evaluating claims? | Argumentation | — |

### Step 2: Identify the Uncertainty Profile

| Uncertainty Type | Implies |
|-----------------|---------|
| Aleatoric (random) | Probabilistic, Statistical |
| Epistemic (knowable unknown) | Research, Information Gathering |
| Knightian (immeasurable) | Decision Under Uncertainty, Scenario Planning |
| No significant uncertainty | Deductive, Logical |

### Step 3: Identify the Stakes

| Stakes Level | Implies |
|-------------|---------|
| High, irreversible | Full method chain, Adversarial Review, Premortem |
| Medium, reversible | Structured method, lighter verification |
| Low, easily reversible | Satisficing, fast decision |

### Step 4: Identify the Domain

See `ontology/domains.yaml` for domain-specific method recommendations.

### Step 5: Identify the Problem Structure

| Structure | Implies |
|-----------|---------|
| Well-defined, closed | Deductive, Optimization |
| Ill-defined, open | Creative, Systems, First-Principles |
| Adversarial | Game Theory, Threat Modeling |
| Dynamic, evolving | Systems, Feedback Analysis |
| Multi-stakeholder | Multi-Criteria Decision, Dialectic |
| Time-critical | Satisficing, Decision Under Uncertainty |

## Output

A classification tuple:
- **problem_type**: [list of applicable categories]
- **uncertainty_profile**: [aleatoric | epistemic | knightian | none]
- **stakes**: [high | medium | low]
- **reversibility**: [reversible | irreversible]
- **domain**: [domain id]
- **structure**: [well-defined | ill-defined | adversarial | dynamic | multi-stakeholder | time-critical]
- **candidate_categories**: [list of method categories]
- **candidate_methods**: [list of specific method ids]

## Example

**Problem**: "We need to choose a database for our new distributed system. We have 5 engineering teams, strict latency requirements, and the decision will be hard to reverse."

**Classification**:
- problem_type: [what-to-do, how-to-achieve]
- uncertainty_profile: epistemic
- stakes: high
- reversibility: irreversible
- domain: software-engineering
- structure: multi-stakeholder
- candidate_categories: [decision, risk, optimization, systems]
- candidate_methods: [multi-criteria-decision, trade-off-analysis, risk-analysis, premortem, constraint-analysis]