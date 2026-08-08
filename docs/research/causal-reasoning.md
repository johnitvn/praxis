# Causal Reasoning — Research Notes

## Canonical Sources

- **Pearl, J.** (Causality, 2000; The Book of Why, 2018) — Causal graphs, do-calculus, structural causal models
- **Spirtes, P., Glymour, C., Scheines, R.** (Causation, Prediction, and Search, 2000) — Causal discovery algorithms
- **Rubin, D.B.** (1974) — Potential outcomes framework, counterfactuals
- **Wright, S.** (1921) — Path analysis, origin of causal diagrams
- **Morgan, S.L. & Winship, C.** (Counterfactuals and Causal Inference, 2014) — Unified framework

## Key Findings

### Causal Graph Reasoning
- Pearl's key insight: causality is not just correlation + assumptions; it requires a structural model
- The do-operator: P(Y|do(X)) ≠ P(Y|X) when confounding exists
- Three rules of do-calculus enable reasoning about interventions from observational data
- Back-door criterion: sufficient adjustment set for estimating causal effects
- AI agents commonly confuse P(Y|X) with P(Y|do(X)) — conditioning is not intervening

### Counterfactual Reasoning
- Rubin's framework: each unit has potential outcomes under treatment and control
- The fundamental problem: only one potential outcome is observed
- Counterfactuals require a causal model; they cannot be computed from data alone
- Most commonly misapplied when the causal model is wrong or incomplete
- Key distinction: counterfactuals (what would have happened) vs. interventions (what will happen)

### Intervention Analysis
- Distinct from both prediction and association
- Requires: (1) specifying the intervention, (2) identifying the causal effect, (3) estimating from data
- Instrumental variables, difference-in-differences, regression discontinuity are quasi-experimental methods
- Randomized controlled trials are the gold standard but often infeasible

### Causal Discovery
- PC algorithm (Spirtes-Glymour): learns causal structure from conditional independence tests
- FCI algorithm: handles latent confounders
- Key limitation: causal discovery produces equivalence classes, not unique graphs
- Assumptions required: causal sufficiency, faithfulness, no feedback cycles (for some algorithms)
- AI agents should treat discovered graphs as hypotheses, not facts

## Method Boundaries

- **Causal vs. Probabilistic**: Causality is about mechanisms; probability is about uncertainty. Causal reasoning requires stronger assumptions than probabilistic reasoning.
- **Causal Discovery vs. Expert Knowledge**: Causal discovery algorithms learn from data; expert knowledge provides causal structure from domain understanding. Combine when possible.
- **Counterfactuals vs. Forecasting**: Counterfactuals ask "what would have happened if"; forecasting asks "what will happen." Both require causal models for reliable answers.

## References

- Pearl, J. (2000). Causality: Models, Reasoning, and Inference. Cambridge University Press.
- Pearl, J. & Mackenzie, D. (2018). The Book of Why. Basic Books.
- Spirtes, P., Glymour, C., & Scheines, R. (2000). Causation, Prediction, and Search. MIT Press.
- Rubin, D.B. (1974). Estimating causal effects of treatments in randomized and nonrandomized studies. Journal of Educational Psychology.
- Morgan, S.L. & Winship, C. (2014). Counterfactuals and Causal Inference. Cambridge University Press.
- Wright, S. (1921). Correlation and causation. Journal of Agricultural Research.