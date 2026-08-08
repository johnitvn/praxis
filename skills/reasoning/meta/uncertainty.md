# Uncertainty

Classify, quantify, and handle uncertainty in reasoning.

## Purpose

Uncertainty is not a failure of reasoning — it is a feature of the world. The goal is not to eliminate uncertainty but to recognize it, classify it, quantify it when possible, and reason appropriately given its presence.

## Types of Uncertainty

### Aleatoric Uncertainty (Statistical)
Uncertainty from inherent randomness. Cannot be reduced by more information.

**Examples**: Coin flips, quantum events, measurement noise
**Handling**: Probabilistic models, confidence intervals, Monte Carlo

### Epistemic Uncertainty (Systematic)
Uncertainty from lack of knowledge. Can be reduced by more information.

**Examples**: Unknown parameter values, missing data, model uncertainty
**Handling**: Research, measurement, Bayesian updating, sensitivity analysis

### Knightian Uncertainty (Fundamental)
Uncertainty where probabilities cannot be meaningfully assigned.

**Examples**: Unprecedented events, radical innovation, "unknown unknowns"
**Handling**: Scenario planning, robust decision-making, precautionary principle

### Model Uncertainty
Uncertainty about whether the model itself is correct.

**Examples**: Wrong functional form, omitted variables, structural breaks
**Handling**: Model comparison, cross-validation, ensemble methods

## Uncertainty Assessment

### Step 1: Identify Uncertainty Sources

For each element of your reasoning:
- What is uncertain?
- What type of uncertainty is it?
- Can it be reduced?

### Step 2: Quantify When Possible

- **Aleatoric**: Use probability distributions, confidence intervals
- **Epistemic**: Use Bayesian updating, state confidence ranges
- **Knightian**: Use scenarios, bounds, "what if" analysis

### Step 3: Propagate Uncertainty

Don't just note uncertainty at inputs — track how it affects conclusions.
- If input A is ±20% uncertain, how uncertain is the conclusion?
- Use sensitivity analysis to identify which uncertainties matter most

### Step 4: Communicate Uncertainty

- State confidence levels explicitly
- Use ranges, not point estimates, when uncertain
- Distinguish between "I don't know" and "it's inherently uncertain"
- Never fabricate precision

## Uncertainty and Decision

| Uncertainty Level | Decision Strategy |
|------------------|-------------------|
| Low | Optimize expected value |
| Moderate | Add safety margins, sensitivity analysis |
| High | Robust decision-making, multiple scenarios |
| Extreme | Precautionary principle, reversible steps, information gathering |

## Common Failure Modes

- **False precision**: Reporting 3.742 when the uncertainty is ±50%
- **Uncertainty neglect**: Ignoring uncertainty and reasoning as if certain
- **Uncertainty paralysis**: Being unable to decide because of uncertainty
- **Type confusion**: Treating epistemic uncertainty as aleatoric (giving up on learning)
- **Overconfidence**: Underestimating uncertainty systematically
- **Certainty seeking**: Demanding certainty where none is possible