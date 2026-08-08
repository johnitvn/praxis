# Intervention Analysis

## Purpose
Intervention analysis predicts the effect of deliberately setting a variable to a specific value in a system — what happens when you act on the system rather than merely observe it. It distinguishes the causal effect of doing X from the associational relationship of seeing X.

## When to Use
- When evaluating a proposed action or policy change: "What happens if we set the price to $10?"
- When designing experiments: "What should we randomize to estimate the causal effect?"
- When comparing the expected outcomes of different actions.
- When you need to distinguish between correlation and causation — between what you see and what you get if you intervene.

## When Not to Use
- When the intervention is not well-defined — "improve the system" is not a specific intervention.
- When confounding is uncontrolled and cannot be adjusted for.
- When the intervention changes the causal structure itself (non-modular system) — standard intervention analysis assumes the causal graph is invariant under intervention.
- When you cannot observe the outcome after the intervention — interventions require feedback to validate.

## Problem Signals
- The problem asks: "What is the effect of doing X?" or "Should we do X or Y?"
- The user is considering a specific action and wants to predict its consequences.
- The problem is framed as a choice between interventions: "Which approach will produce better results?"
- The user wants to know if an observed correlation is actually causal.

## Inputs
- A causal model or graph of the system.
- The intervention specification: which variable to set to what value, and how (the do-operator).
- Data on the system's behavior under observational conditions.
- Optionally, data from previous interventions or experiments.

## Procedure
1. **Define the intervention precisely.** What variable is being set? To what value? How is it being set? "Set price to $10 for all customers" is an intervention. "Observe customers who paid $10" is not.
2. **Identify the causal estimand.** What is the quantity you want to estimate? Common estimands: the Average Treatment Effect (ATE), the Average Treatment Effect on the Treated (ATT), the Conditional Average Treatment Effect (CATE).
3. **Check identifiability.** Using the causal graph, determine whether the estimand can be expressed in terms of observable quantities (the do-calculus). If the estimand is not identifiable, the intervention effect cannot be estimated from the available data.
4. **Identify the adjustment set.** Use the backdoor criterion to find variables that must be controlled for to estimate the causal effect. Include all variables that block backdoor paths and are not descendants of the treatment.
5. **Design the estimation strategy.** Choices include:
   - **Randomized experiment:** Randomly assign the intervention. Gold standard when feasible.
   - **Natural experiment:** Exploit an exogenous source of variation (instrumental variables, regression discontinuity).
   - **Observational adjustment:** Control for confounders using regression, matching, or stratification.
   - **Difference-in-differences:** Compare treated and control groups before and after the intervention.
6. **Estimate the effect.** Apply the chosen strategy to the data. Compute the effect size and its uncertainty.
7. **Diagnose threats to validity.** Check for: unmeasured confounding, selection bias, measurement error, spillover effects (the intervention affecting untreated units), and Hawthorne effects (units changing behavior because they are being studied).
8. **Report the effect with uncertainty.** State the estimated effect, the confidence interval, and the key assumptions.

## Output
- The estimated causal effect of the intervention, with uncertainty bounds.
- The estimation strategy used and justification for why it is valid.
- Diagnostics: tests for balance, placebo tests, sensitivity analyses.
- Caveats: what assumptions could be violated and how that would affect the conclusion.

## Strengths
- Produces actionable conclusions: "If you do X, expect Y to change by Z."
- Distinguishes causation from correlation — the core problem of empirical inference.
- Supports experimental design by identifying what must be randomized or controlled.
- Integrates with causal graph reasoning for formal identifiability analysis.

## Limitations
- Requires valid instruments, randomization, or strong ignorability assumptions for observational studies.
- Confounding may remain even after adjustment — unmeasured confounders are always a threat.
- External validity: the effect estimated in one context may not generalize to another.
- The intervention must be well-defined and feasible — interventions that cannot be implemented cannot be studied.

## Common Failure Modes
- **Confusing observation with intervention.** "Users who see feature X have higher engagement" is an observation. "If we show feature X to all users, engagement will increase" is an intervention claim. The first does not imply the second.
- **Ignoring unmeasured confounding.** Controlling for measured confounders is not enough if unmeasured confounders exist. Always report the unmeasured confounding assumption.
- **Controlling for post-treatment variables.** Variables affected by the intervention should not be controlled for — they are mediators or colliders. Controlling for them introduces bias.
- **Overgeneralizing the effect.** An intervention effect estimated in one population, time period, or context may not hold in another. Report the scope of the estimate.
- **Ignoring spillover.** If the intervention affects untreated units, the estimated effect is biased. Consider whether the Stable Unit Treatment Value Assumption (SUTVA) holds.

## Verification
- Is the causal estimand identifiable from the available data and causal model?
- Does the adjustment set satisfy the backdoor criterion? Have you checked for colliders?
- Are there placebo tests you can run? An intervention should have no effect on outcomes that occurred before the intervention or on units that were not treated.
- Does the estimated effect change substantially under different plausible adjustment sets? If so, the estimate is not robust.

## Combine With
- **Causal-graph reasoning** — use the causal graph to determine identifiability and choose the adjustment set.
- **Counterfactual reasoning** — extend population-level intervention effects to individual-level counterfactuals.
- **Experimental design** — use intervention analysis to design experiments that can estimate causal effects.
- **Sensitivity analysis** — assess how sensitive the estimated effect is to unmeasured confounding.

## Example
**Problem:** A product team wants to know whether adding a onboarding tutorial (X) increases user retention (Y). They have historical data showing that users who completed the tutorial have higher retention. But tutorial completion is voluntary — more motivated users are more likely to complete it. What is the causal effect of making the tutorial mandatory?

**Application:**
1. Intervention: Set tutorial completion to "yes" for all new users (mandatory tutorial).
2. Causal estimand: ATE — the difference in average retention if all users complete the tutorial vs. if none do.
3. Causal graph: Motivation (U) → Tutorial Completion (X) and Motivation (U) → Retention (Y). Tutorial (X) → Retention (Y).
4. Identifiability: Backdoor path X ← U → Y. Controlling for U (motivation) would block it, but U is unmeasured. The ATE is not identifiable from observational data alone.
5. Estimation strategy: Since they cannot adjust for motivation, they need a randomized experiment. Randomly assign new users to mandatory tutorial vs. no tutorial. This breaks the arrow U → X, removing confounding.
6. Run the experiment: 5,000 users per arm. Tutorial group retention: 45%. Control group retention: 40%. ATE: 5 percentage points (95% CI: 3-7pp).
7. Diagnostics: Check that randomization worked — are the groups balanced on observed covariates? Yes. Spillover check: did control users access the tutorial anyway? No.
8. Conclusion: The tutorial causes a 5pp increase in retention. The earlier observational estimate (which showed a 15pp difference) was heavily confounded by motivation.

## Selection Metadata
```
id: intervention-analysis
category: causal
best_for: [policy evaluation, experiment design, action planning]
requires: [causal model, intervention specification]
produces: [predicted intervention effects]
strengths: [actionable conclusions, distinguishes correlation from causation]
limitations: [requires valid instruments or randomization, confounding may remain]
combine_with: [causal-graph-reasoning, experimental-design]
avoid_when: [intervention is not well-defined, confounding is uncontrolled]
```