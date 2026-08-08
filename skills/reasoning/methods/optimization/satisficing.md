# Satisficing

## Purpose
Find a solution that is good enough to meet aspiration levels, rather than searching for the optimal solution.

## When to Use
When time is limited and an adequate solution is sufficient. When the cost of finding the optimal solution exceeds the benefit of the improvement. When the problem is not fully formalizable and optimization is not feasible. When you are operating under bounded rationality — the search space is too large or ill-defined to optimize. When the decision is reversible and you can adjust later. When aspiration levels are clearer than a single objective function.

## When Not to Use
When optimality is critical — for example, safety margins, legal compliance thresholds, or competitive bids where small differences matter. When time is abundant and the search cost is low. When you have a well-formulated optimization problem and a solver is available. When the aspiration level is set so high that no acceptable solution exists, or so low that the first option is always accepted.

## Problem Signals
The problem description includes phrases like "good enough," "we just need something that works," "we don't have time to optimize this," "what's the minimum viable solution?" The decision is low-stakes or reversible. The search space is large and ill-defined. The problem is one of many competing demands, and perfection on this one is not worth the effort.

## Inputs
- **Aspiration levels**: the minimum acceptable threshold for each relevant dimension
- **Options**: the set of candidate solutions, or a mechanism to generate them
- **Search order**: the sequence in which options will be evaluated (may be random, ordered by cost, or ordered by expected quality)

## Procedure
1. **Set aspiration levels**: for each relevant dimension, define the threshold that separates "acceptable" from "unacceptable." Be specific — "latency under 200ms" not "fast enough."
2. **Define the stopping rule**: decide when to stop searching. Common rules: stop at the first acceptable option; stop after N acceptable options and pick the best among them; stop after a fixed time budget.
3. **Search**: evaluate options sequentially. For each option, check whether it meets all aspiration levels.
4. **Stop at first acceptable** (or according to your stopping rule): choose the first option that meets all thresholds. Do not continue searching for a better one.
5. **If no option meets aspiration levels**: either relax the levels (explicitly, with justification), generate more options, or escalate to a more thorough method.

## Output
A satisfactory solution that meets all aspiration levels. The aspiration levels used. The number of options evaluated before stopping. If no solution was found, a record of which aspiration levels could not be met.

## Strengths
Fast and frugal. Realistic about human and computational bounds. Avoids the paralysis of optimization when the problem is not fully specifiable. Herbert Simon's original formulation aligns with how experts actually make decisions under time pressure. Works well for reversible decisions where the cost of a suboptimal choice is low.

## Limitations
May miss substantially better solutions that would have been found with modest additional effort. The quality of the outcome depends entirely on the aspiration levels — set them too low and you accept mediocrity; set them too high and you find nothing. Does not provide information about how much better the optimum might be. The first acceptable option may be path-dependent on the search order.

## Common Failure Modes
Setting aspiration levels without understanding the distribution of possible solutions, leading to either trivial acceptance or impossible standards. Using satisficing for irreversible, high-stakes decisions where the cost of a suboptimal choice is large. Treating the first acceptable solution as optimal and defending it as such. Never revisiting the aspiration levels even when the first acceptable solution is clearly inadequate. Applying satisficing when a well-formulated optimization problem is available and the solver cost is low.

## Verification
Confirm the chosen solution meets all stated aspiration levels. Check whether the stopping rule was applied correctly — did you stop at the right point, or did you continue searching after finding an acceptable option? Verify that the aspiration levels were set before the search began, not retrofitted to the chosen solution. If the solution feels inadequate, check whether the aspiration levels were set too low.

## Combine With
- **stopping-criteria**: to formalize when to stop searching
- **decision-methods**: to evaluate the chosen solution against alternatives if time permits
- **cost-benefit-analysis**: to determine whether the search cost of further optimization is justified
- **reversible-decision** (pattern): satisficing is the natural method for reversible decisions

## Conflicts With
- **constrained-optimization**: optimization seeks the best; satisficing stops at adequate
- **multi-objective-optimization**: MOO maps the full frontier; satisficing stops at the first acceptable point
- **expected-utility**: requires full evaluation of all options; satisficing stops early

## Example
A team needs to choose a CI/CD tool. They have 15 candidates and 2 hours to decide. Aspiration levels: supports Docker builds, integrates with GitHub, costs under $500/month, has a Slack notification plugin. They evaluate tools in order of market share. The third tool (GitLab CI) meets all thresholds. They stop and adopt it, deferring a more thorough evaluation to a later quarter if needed. They do not evaluate the remaining 12 tools.

## Selection Metadata
```
id: satisficing
category: optimization
best_for: [bounded rationality, time pressure, adequate solutions, reversible decisions]
requires: [aspiration levels, options, stopping rule]
produces: [satisfactory solution, aspiration levels met, search effort]
strengths: [fast, realistic, prevents analysis paralysis]
limitations: [may miss better solutions, aspiration-dependent, path-dependent]
combine_with: [stopping-criteria, decision-methods, cost-benefit-analysis]
avoid_when: [optimality is critical, time is abundant, problem is fully formalizable]
```