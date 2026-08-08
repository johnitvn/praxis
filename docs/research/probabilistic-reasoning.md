# Probabilistic Reasoning — Research Notes

## Canonical Sources

- **Bayes, T.** (1763) — An Essay towards solving a Problem in the Doctrine of Chances
- **Laplace, P.S.** (1814) — A Philosophical Essay on Probabilities
- **de Finetti, B.** (1937) — Subjective probability and exchangeability
- **Jaynes, E.T.** (Probability Theory: The Logic of Science, 2003) — Maximum entropy, Bayesian inference
- **Fisher, R.A.** — Frequentist statistics, maximum likelihood, experimental design
- **Neyman, J. & Pearson, E.** — Hypothesis testing framework
- **Gelman, A. et al.** (Bayesian Data Analysis, 2013) — Modern Bayesian methods

## Key Findings

### Bayesian Reasoning
- Bayes' theorem: P(H|E) = P(E|H)P(H)/P(E)
- Key advantage: coherent updating with sequential evidence
- Prior sensitivity is the most common criticism — but all reasoning has priors; Bayesian reasoning makes them explicit
- Conjugate priors enable tractable computation
- AI agents commonly fail at: (1) base rate neglect, (2) prosecutor's fallacy, (3) not updating incrementally
- The "Dutch book" argument: non-Bayesian beliefs are exploitable

### Frequentist Reasoning
- p-value: P(data at least as extreme | H0) — NOT P(H0|data)
- Most misunderstood concept in statistics: p < 0.05 does not mean "95% probability the alternative is true"
- Confidence intervals: if repeated, 95% of intervals contain the true parameter — NOT "95% probability the parameter is in this interval"
- Multiple comparisons problem: p-hacking, garden of forking paths
- AI agents commonly misinterpret p-values and confidence intervals

### Statistical Reasoning
- Estimand definition: what are you trying to estimate?
- Model selection: bias-variance tradeoff, not just fit
- Assumption checking: residuals, influence, multicollinearity
- The "null ritual": mechanically applying significance tests without understanding what they mean
- Gelman's "garden of forking paths": researcher degrees of freedom inflate false positive rates

### Uncertainty Quantification
- Aleatoric vs. epistemic uncertainty: randomness vs. lack of knowledge
- Monte Carlo methods: propagate uncertainty through simulation
- Sensitivity analysis: which uncertainties matter most?
- Common failure: quantifying only the uncertainties you can measure, ignoring the ones you can't

## Method Boundaries

- **Bayesian vs. Frequentist**: Bayesian reasoning is about belief updating; frequentist reasoning is about error control. Use Bayesian when you have prior information; use frequentist when you need objective error rates.
- **Statistical vs. Causal**: Statistical reasoning identifies associations; causal reasoning identifies mechanisms. Confusing them is the most common error in data analysis.
- **Uncertainty Quantification vs. Risk Analysis**: UQ provides the uncertainty inputs; risk analysis evaluates consequences. Both are needed for risk-informed decisions.

## References

- Jaynes, E.T. (2003). Probability Theory: The Logic of Science. Cambridge University Press.
- Gelman, A. et al. (2013). Bayesian Data Analysis (3rd ed.). CRC Press.
- de Finetti, B. (1937). La prévision: ses lois logiques, ses sources subjectives. Annales de l'Institut Henri Poincaré.
- Fisher, R.A. (1925). Statistical Methods for Research Workers.
- Neyman, J. & Pearson, E. (1933). On the problem of the most efficient tests of statistical hypotheses.
- Gelman, A. & Loken, E. (2013). The garden of forking paths.