# Decision Theory — Research Notes

## Canonical Sources

- **von Neumann, J. & Morgenstern, O.** (Theory of Games and Economic Behavior, 1944) — Expected utility axioms
- **Savage, L.J.** (The Foundations of Statistics, 1954) — Subjective expected utility
- **Kahneman, D. & Tversky, A.** (1979, 1992) — Prospect theory, heuristics and biases
- **Keeney, R.L. & Raiffa, H.** (Decisions with Multiple Objectives, 1976) — Multi-attribute utility theory
- **Simon, H.A.** (1955, 1956) — Bounded rationality, satisficing
- **Ellsberg, D.** (1961) — Ambiguity aversion (Knightian uncertainty)

## Key Findings

### Expected Utility Theory
- von Neumann-Morgenstern axioms: completeness, transitivity, continuity, independence
- A rational agent maximizes expected utility — if the axioms hold
- But the axioms are descriptive, not prescriptive: real agents violate them systematically
- The Allais paradox and Ellsberg paradox demonstrate axiom violations
- For AI agents: expected utility is a useful framework when probabilities and utilities are well-defined
- Not appropriate when utilities are incommensurable or probabilities are Knightian

### Multi-Criteria Decision Analysis
- Keeney & Raiffa: structure objectives hierarchically, assess trade-offs explicitly
- Weight elicitation methods: direct rating, swing weighting, AHP, trade-off method
- Key insight: weights are not "importance" — they depend on the range of each criterion
- The additive model assumes preferential independence (often violated)
- AI agents should use MCDA when: multiple objectives, trade-offs exist, stakeholders disagree

### Decision Under Uncertainty
- Five classical criteria: maximin, maximax, minimax regret, Hurwicz, Laplace
- Maximin: choose the option with the best worst-case outcome (most conservative)
- Minimax regret: minimize maximum regret (compares to what you could have gotten)
- Appropriate when probabilities are unavailable (Knightian uncertainty)
- AI agents commonly default to expected value thinking when probabilities are fabricated

### Cost-Benefit Analysis
- Net present value: future costs/benefits discounted to present
- Discount rate is normative: higher rates favor present; lower rates favor future
- Monetization of non-market goods is controversial but necessary
- Distributional effects: who benefits and who bears costs?
- The "counterfactual": what would have happened without the intervention?

### Satisficing
- Simon's key insight: optimization is computationally intractable; satisficing is realistic
- Set aspiration levels; choose the first option that meets them
- Under time pressure, satisficing is often better than optimizing
- The "secretary problem": optimal stopping when options are sequential

## References

- von Neumann, J. & Morgenstern, O. (1944). Theory of Games and Economic Behavior.
- Savage, L.J. (1954). The Foundations of Statistics. Wiley.
- Kahneman, D. & Tversky, A. (1979). Prospect theory. Econometrica.
- Keeney, R.L. & Raiffa, H. (1976). Decisions with Multiple Objectives.
- Simon, H.A. (1955). A behavioral model of rational choice. Quarterly Journal of Economics.
- Ellsberg, D. (1961). Risk, ambiguity, and the Savage axioms. Quarterly Journal of Economics.