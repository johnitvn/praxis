# Causal Graph Reasoning

## Purpose
Causal graph reasoning uses directed acyclic graphs (DAGs) to represent causal relationships between variables, enabling rigorous reasoning about interventions, confounding, and the propagation of effects through a system.

## When to Use
- When you have a causal model (or can construct one) showing how variables influence each other.
- When you need to predict the effect of an intervention (setting a variable to a specific value).
- When you need to identify confounders that could bias an estimate of a causal effect.
- When you need to determine what variables to control for (or not control for) to estimate a causal effect.

## When Not to Use
- When the causal structure is entirely unknown and cannot be constructed from domain knowledge.
- When the system is non-modular — interventions change the causal structure itself, not just variable values.
- When you only have two variables and no knowledge of their relationship — a graph with one edge provides no insight.
- When feedback loops are critical — DAGs cannot represent cycles directly (use dynamic causal models instead).

## Problem Signals
- The problem asks: "What is the effect of X on Y?" or "Does X cause Y?"
- The user wants to know: "What should I control for?" or "Is this estimate biased?"
- The problem involves a system with multiple interacting variables where some relationships are causal and others are merely correlational.
- The user presents a diagram or description of how things influence each other.

## Inputs
- A causal graph: nodes (variables) and directed edges (direct causal influences).
- Data or knowledge about conditional independencies that constrain the graph.
- Optionally, an intervention specification: which variable to set to what value.

## Procedure
1. **Construct the causal graph.** Start with domain knowledge. For each pair of variables (A, B), ask: Does A directly cause B? Does B directly cause A? Does a third variable cause both? Add directed edges accordingly.
2. **Verify the graph is acyclic.** If there is a cycle, the standard DAG framework does not apply. Break the cycle by introducing time indices or latent variables.
3. **Identify all paths between the exposure (cause) and outcome (effect).** A path is any sequence of edges regardless of direction.
4. **Classify each path as causal or non-causal.** A causal path follows the direction of arrows from cause to effect. A non-causal (backdoor) path contains an arrow pointing into the cause.
5. **Identify confounding.** A backdoor path between exposure and outcome that is open (not blocked by a collider) creates confounding. Variables on backdoor paths must be controlled for to estimate the causal effect.
6. **Apply the backdoor criterion.** To estimate the causal effect of X on Y, find a set of variables Z such that: (a) Z blocks all backdoor paths from X to Y, and (b) no variable in Z is a descendant of X.
7. **Check for collider bias.** A collider is a variable with two arrows pointing into it. Do NOT control for colliders — doing so opens a non-causal path and creates bias.
8. **Predict the intervention effect.** Using the backdoor-admissible set, estimate: what happens to Y when X is set to x (intervention) versus when X is observed to be x (observation)?
9. **Validate the graph.** Check implied conditional independencies against data. If the graph predicts X and Y are independent given Z, but data shows they are dependent, the graph is wrong.

## Output
- The causal graph with all nodes and directed edges.
- Identification of all backdoor paths and the minimal set of variables to control for.
- The predicted causal effect of the intervention, distinct from the observed association.
- A warning about any colliders or mediators that should NOT be controlled for.

## Strengths
- Makes causal assumptions explicit and testable.
- Distinguishes confounding from mediation — you know what to control for and what not to.
- Handles complex causal structures with multiple pathways.
- The do-calculus provides a complete set of rules for deriving causal effects from observational data when possible.

## Limitations
- Requires a causal graph — constructing one requires domain knowledge that may be unavailable.
- The graph may be incomplete or wrong, and errors propagate to all conclusions.
- DAGs cannot represent cyclic causation (feedback loops) without extension.
- Assumes no unmeasured confounders unless explicitly modeled as latent variables.

## Common Failure Modes
- **Controlling for mediators.** A mediator is on the causal path from X to Y. Controlling for it blocks the causal effect you are trying to estimate. Never control for mediators when estimating total effects.
- **Controlling for colliders.** A collider (e.g., X → Z ← Y) blocks a path by default. Controlling for Z opens it, creating spurious association. Classic example: controlling for "hospitalization" when studying the effect of a disease on mortality — this creates bias because hospitalized patients are selected on both disease severity and mortality risk.
- **Ignoring unmeasured confounders.** The backdoor criterion assumes all relevant confounders are measured. If an unmeasured variable causes both X and Y, no amount of adjustment will remove the bias.
- **Confusing the graph with reality.** The causal graph is a model. Validate it against data and domain knowledge.
- **Over-interpreting the graph.** The graph tells you what you can estimate, not the magnitude of the effect. Estimation requires data and statistical methods.

## Verification
- Is the graph acyclic? Check for feedback loops.
- Does the chosen adjustment set satisfy the backdoor criterion?
- Are there any colliders in the adjustment set? If so, the estimate is biased.
- Does the graph imply conditional independencies that are consistent with observed data?

## Combine With
- **Counterfactual reasoning** — extend the causal graph to answer "what if" questions about specific individuals.
- **Bayesian reasoning** — use Bayesian methods to estimate causal effects given the graph and data.
- **Intervention analysis** — use the graph to design and analyze interventions.
- **Causal discovery** — use causal discovery algorithms to learn the graph structure from data.

## Conflicts With
- **Statistical reasoning without causal structure** — correlations without a causal graph do not support causal claims. Do not use regression coefficients as causal effects without a causal graph.

## Example
**Problem:** A data scientist wants to estimate the effect of a new recommendation algorithm (X) on user engagement (Y). Users who see the new algorithm are more active (higher engagement). But the algorithm was rolled out to power users first. How should they estimate the causal effect?

**Application:**
1. Causal graph: User Type (U) → Algorithm Assignment (X) and User Type (U) → Engagement (Y). Algorithm (X) → Engagement (Y).
2. Paths from X to Y:
   - Causal path: X → Y (the effect we want to estimate).
   - Backdoor path: X ← U → Y (confounding by user type).
3. Backdoor path is open — user type creates a spurious association.
4. Adjustment set: Control for User Type (U). This blocks the backdoor path.
5. Do NOT control for any variable on the causal path (e.g., click-through rate) — that would be a mediator.
6. Estimate: Compare engagement between algorithm variants within each user type, then average. This estimates the causal effect uncontaminated by selection bias.

## Selection Metadata
```
id: causal-graph-reasoning
category: causal
best_for: [intervention planning, effect prediction, confounding analysis]
requires: [causal graph, conditional independence data]
produces: [causal effects, intervention predictions]
strengths: [explicit causal structure, handles confounding]
limitations: [requires causal graph, graph may be incomplete]
combine_with: [counterfactual-reasoning, bayesian-reasoning]
avoid_when: [causal structure is unknown, system is non-modular]
```