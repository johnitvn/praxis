# Counterfactual Reasoning

## Purpose
Counterfactual reasoning answers questions about what would have happened under different conditions — specifically, what would the outcome have been for a particular unit if the treatment or exposure had been different from what it actually was. It is the foundation of attribution, blame, and "what if" analysis.

## When to Use
- When you need to attribute an outcome to a specific cause: "Was it the new feature that caused the increase in signups, or would signups have increased anyway?"
- When evaluating fairness: "Would this applicant have been approved if they belonged to a different demographic group?"
- When analyzing a past event: "If we had rolled back the deployment sooner, would the outage have been shorter?"
- When you need individual-level causal claims, not just population-level average effects.

## When Not to Use
- When the counterfactual is ill-defined — "what if things were different" is too vague to formalize.
- When you lack a causal model strong enough to support counterfactual inference.
- When the question is about a population-level causal effect — use intervention analysis or causal graph reasoning instead.
- When the counterfactual scenario is physically impossible or logically inconsistent.

## Problem Signals
- The problem asks "what if," "would have," "could have," "had we done X instead of Y."
- The user wants to attribute responsibility: "Was it the change we made, or something else?"
- The problem involves a specific case or individual, not an average over a population.
- The user is doing a post-mortem and wants to know what would have changed the outcome.

## Inputs
- A causal model (structural causal model, or at minimum a causal graph with functional relationships).
- The actual outcome for the unit(s) of interest.
- The actual treatment or exposure for the unit(s) of interest.
- The counterfactual treatment or exposure: what would have been different.

## Procedure
1. **Define the unit of analysis.** Counterfactuals are about specific units (a person, a system, an event). Which unit are you reasoning about?
2. **Define the actual scenario.** What treatment did the unit actually receive? What outcome did they actually experience?
3. **Define the counterfactual scenario.** What is the alternative treatment? Be precise: "the deployment was rolled back at 14:00 instead of 15:00."
4. **Specify the causal model.** You need a structural causal model that relates the treatment to the outcome, including all relevant background variables. The model must be strong enough to support counterfactual inference — it needs functional relationships, not just a graph.
5. **Compute the counterfactual outcome using the three-step process:**
   - **Abduction:** Use the actual outcome and treatment to infer the values of unobserved (exogenous) variables. What must the background conditions have been to produce the observed outcome?
   - **Action:** Modify the causal model to reflect the counterfactual treatment (the do-operator: set the treatment variable to its counterfactual value).
   - **Prediction:** Using the modified model and the inferred background conditions, compute the predicted outcome.
6. **Compute the counterfactual contrast.** The difference between the actual outcome and the counterfactual outcome is the individual treatment effect.
7. **Assess model sensitivity.** How sensitive is the counterfactual conclusion to the causal model's assumptions? If the model is wrong, the counterfactual is wrong.

## Output
- The counterfactual outcome: what would have happened for this specific unit under the alternative treatment.
- The counterfactual contrast: the difference between actual and counterfactual outcomes.
- The inferred background conditions: what must have been true about the unit to produce the actual outcome.
- A sensitivity caveat: how the conclusion depends on the causal model.

## Strengths
- Answers "what if" questions at the individual level — the most precise form of causal attribution.
- Essential for fairness analysis: determining whether a decision would have been different under different circumstances.
- Provides the conceptual foundation for mediation analysis: what is the direct vs. indirect effect of a treatment?
- Integrates naturally with structural causal models for formal computation.

## Limitations
- Requires a strong causal model — much stronger than what is needed for average causal effects.
- Untestable in most cases: you cannot observe the counterfactual outcome, so the inference cannot be directly validated.
- Highly sensitive to model specification: small errors in the causal model produce large errors in counterfactual predictions.
- The "fundamental problem of causal inference": you can never observe both the actual and counterfactual outcomes for the same unit.

## Common Failure Modes
- **Confusing counterfactuals with predictions.** A counterfactual is about what would have happened to a specific unit under a different treatment, given what we know about the unit. It is not a prediction about what will happen to a new unit.
- **Weak causal model.** Using a causal graph without functional relationships. A graph tells you what affects what, but counterfactuals require knowing how much and in what direction.
- **Ill-defined counterfactual.** "What if we had a different architecture?" is too vague. "What if we had used a message queue instead of a synchronous call?" is specific.
- **Ignoring mediation.** If the treatment affects the outcome through multiple paths, the counterfactual depends on which path is being modified. Be explicit about whether you are computing a total effect, direct effect, or indirect effect.
- **Deterministic thinking.** Treating the counterfactual computation as a single point estimate when it is inherently uncertain. Always report the sensitivity to model assumptions.

## Verification
- Is the counterfactual scenario well-defined and specific?
- Is the causal model strong enough to support counterfactual inference (functional relationships, not just qualitative structure)?
- Does the three-step process (abduction, action, prediction) produce a consistent result?
- What would the counterfactual be under a different but plausible causal model? If it changes sign, the conclusion is not robust.

## Combine With
- **Causal-graph reasoning** — use the causal graph to identify which variables must be in the model and which can be ignored.
- **Intervention analysis** — use intervention analysis to estimate population-level effects, then counterfactual reasoning to attribute individual outcomes.
- **Bayesian reasoning** — use Bayesian methods to propagate uncertainty through the counterfactual computation.
- **Sensitivity analysis** — systematically vary the causal model assumptions to assess robustness.

## Example
**Problem:** A developer deployed a performance optimization at 10:00. Response time dropped from 500ms to 200ms. The developer claims the optimization caused the improvement. But traffic also dropped at 10:00 because of a calendar event. What was the actual effect of the optimization?

**Application:**
1. Unit: The production system at 10:00 on the deployment day.
2. Actual scenario: Optimization deployed. Actual outcome: 200ms response time.
3. Counterfactual scenario: Optimization NOT deployed at 10:00 (everything else same).
4. Causal model: ResponseTime = f(Optimization, Traffic, BackgroundLoad, ...). The functional relationship must be specified: response time increases with traffic, decreases with optimization.
5. Three-step process:
   - Abduction: Given actual outcome (200ms) and actual treatment (optimization = yes), infer the background conditions (traffic was low, background load was normal).
   - Action: Set optimization = no in the model.
   - Prediction: Using the inferred background conditions (low traffic) and no optimization, the model predicts response time would have been 350ms.
6. Counterfactual contrast: The optimization reduced response time from 350ms to 200ms — a 150ms improvement, not the 300ms improvement the raw comparison suggests.
7. Sensitivity: If the traffic-response function is wrong, the estimate changes. Report the range under plausible alternative functions.

## Selection Metadata
```
id: counterfactual-reasoning
category: causal
best_for: [what-if analysis, attribution, fairness]
requires: [causal model, actual outcome]
produces: [counterfactual outcomes]
strengths: [answers "what if" questions, precise attribution]
limitations: [requires strong causal model, untestable in many cases]
combine_with: [causal-graph-reasoning, intervention-analysis]
avoid_when: [causal model is weak, counterfactual is ill-defined]
```