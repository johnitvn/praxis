# Bayesian Reasoning

## Purpose
Update beliefs about hypotheses in light of new evidence using Bayes' theorem, producing posterior probabilities that coherently combine prior knowledge with observed data.

## When to Use
- When you have competing hypotheses and uncertain evidence
- When you need to update beliefs sequentially as new data arrives
- When prior knowledge or expert judgment is available and should be incorporated
- When you need to reason about the probability of a hypothesis given the evidence (not the reverse)
- When the cost of different errors is asymmetric and you need to weigh evidence against priors

## When Not to Use
- When evidence is deterministic or the conclusion is logically necessary — use deductive reasoning instead
- When you have no defensible way to set priors and the conclusion is highly sensitive to them
- When the hypothesis space is too large to enumerate and compute over
- When probabilities are fabricated rather than grounded in data or domain expertise
- When the problem requires controlling long-run error rates rather than quantifying belief

## Problem Signals
- The problem asks "how likely is X given what we've observed?"
- The user describes updating beliefs after seeing new information
- There are multiple competing explanations and evidence is partial
- The problem involves sequential decision-making under uncertainty
- The user mentions "base rate," "prior probability," or "posterior"

## Inputs
- A set of mutually exclusive and exhaustive hypotheses
- A prior probability distribution over those hypotheses
- Likelihood functions: P(evidence | hypothesis) for each hypothesis
- The observed evidence

## Procedure

### Step 1: Define the Hypothesis Space
Enumerate all hypotheses under consideration. Ensure they are mutually exclusive and collectively exhaustive. If this is not possible, add a catch-all hypothesis.

### Step 2: Elicit Priors
Assign a prior probability to each hypothesis. Sources of priors in order of preference:
1. Empirical base rates from relevant data
2. Domain expert elicitation with calibration
3. Uniform priors as a last resort (acknowledge the assumption)

### Step 3: Compute Likelihoods
For each hypothesis, compute P(E|H) — the probability of observing the evidence if the hypothesis were true. This is the generative step: the hypothesis predicts the data.

### Step 4: Apply Bayes' Theorem
Compute the posterior for each hypothesis:
P(H|E) = P(E|H) * P(H) / P(E)
where P(E) = sum over all H of P(E|H) * P(H)

### Step 5: Interpret the Posterior
- Compare posterior probabilities across hypotheses
- Identify which hypothesis gained or lost probability mass
- Report the posterior distribution, not just the maximum a posteriori estimate
- Acknowledge remaining uncertainty

### Step 6: Sensitivity Check
Vary the priors within a reasonable range and observe whether the conclusion changes. If the posterior is highly sensitive to the prior, the evidence is weak — report this.

## Output
- A posterior probability distribution over all hypotheses
- The Bayes factor (ratio of posterior odds to prior odds) for key comparisons
- A sensitivity analysis showing how conclusions change with different priors

## Strengths
- Coherent: obeys the laws of probability and avoids Dutch book vulnerabilities
- Explicit: all uncertainty is quantified and visible
- Sequential: can incorporate new evidence without recomputing from scratch
- Handles missing data naturally through marginalization

## Limitations
- Prior sensitivity: conclusions can be dominated by the prior when evidence is weak
- Computational complexity: exact inference is intractable for large hypothesis spaces
- Requires the hypothesis space to be specified in advance — cannot discover new hypotheses
- Model dependence: results are only as good as the likelihood model

## Common Failure Modes
- **Prior fabrication**: using arbitrary priors and treating the posterior as authoritative. Always check sensitivity.
- **Inverse fallacy**: confusing P(E|H) with P(H|E). The prosecutor's fallacy is the classic example.
- **Hypothesis space omission**: failing to include the true hypothesis, making all posterior probabilities misleading.
- **Overconfidence**: treating the maximum a posteriori hypothesis as certain when other hypotheses still have substantial probability.
- **Base rate neglect**: ignoring prior probabilities entirely, which is equivalent to Bayesian reasoning with uniform priors on a poorly chosen hypothesis space.

## Verification
- Do the posterior probabilities sum to 1?
- Does the evidence update beliefs in the direction a reasonable person would expect? If not, check the likelihoods.
- Test edge cases: what posterior does the model produce with no evidence (should equal the prior)? With decisive evidence (should converge to a single hypothesis)?
- Compare against a sensitivity grid: vary priors across a plausible range and confirm the qualitative conclusion is stable.

## Combine With
- **Sensitivity Analysis**: to assess prior dependence
- **Evidence Triangulation**: to combine multiple independent sources of evidence
- **Causal Graph Reasoning**: when evidence has causal structure that affects likelihoods
- **Hypothesis Testing**: for complementary frequentist validation

## Conflicts With
- **Frequentist Reasoning**: when the question is about long-run error rates rather than belief updating. Bayesian and frequentist answers can differ for the same data.
- **Deductive Reasoning**: when premises are certain, Bayesian updating adds unnecessary complexity.

## Example
A medical diagnostic problem: a disease has a base rate of 1% in the population. A test is 95% sensitive (true positive rate) and 90% specific (true negative rate). A patient tests positive.

- H1: patient has the disease (prior = 0.01)
- H2: patient does not have the disease (prior = 0.99)
- P(positive | H1) = 0.95
- P(positive | H2) = 0.10
- P(H1 | positive) = (0.95 * 0.01) / (0.95 * 0.01 + 0.10 * 0.99) = 0.0095 / 0.1085 = 0.0876

The posterior probability of disease is ~8.8%, not 95%. The prior base rate dramatically changes the interpretation of the test result.

## Selection Metadata
```
id: bayesian-reasoning
category: probabilistic
best_for: [uncertain evidence, competing hypotheses, sequential updating]
requires: [hypotheses, prior beliefs, evidence likelihoods]
produces: [posterior probabilities]
strengths: [explicit uncertainty, sequential updating, coherent]
limitations: [prior sensitivity, computational complexity]
combine_with: [sensitivity-analysis, evidence-triangulation, causal-graph-reasoning, hypothesis-testing]
avoid_when: [evidence is deterministic, probabilities are fabricated, priors are arbitrary]
```