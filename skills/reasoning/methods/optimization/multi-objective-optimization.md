# Multi-Objective Optimization

## Purpose
Explore the trade-off surface between multiple conflicting objectives, identifying the set of solutions where no objective can be improved without degrading another.

## When to Use
When a problem has two or more objectives that pull in opposite directions — improving one necessarily worsens another. When you need to understand the shape of the trade-off space before committing to a weighting. When the relative importance of objectives is not known in advance, or when different stakeholders value objectives differently. When presenting decision-makers with a menu of non-dominated options is more useful than a single "optimal" solution.

## When Not to Use
When there is a single clear objective (use constrained optimization instead). When objectives are not quantifiable. When objectives can be combined into a single metric legitimately (e.g., through a known conversion rate or market price). When the problem is so simple that the Pareto frontier is trivial.

## Problem Signals
The problem description contains phrases like "we want both X and Y but they conflict," "maximize quality while minimizing cost," "speed versus accuracy," "there's no single right answer because different stakeholders care about different things." The question is "what are the trade-offs?" or "what is possible?" rather than "what is best?"

## Inputs
- **Objective functions**: at least two measurable quantities, each to be maximized or minimized
- **Decision variables**: the parameters that can be adjusted
- **Constraints** (optional): hard bounds on the solution space
- **Stakeholder preferences** (optional): relative importance of objectives, if known

## Procedure
1. **Define objectives**: list each objective as a function of decision variables. State whether each is to be maximized or minimized. Confirm that at least two objectives genuinely conflict.
2. **Define the decision space**: identify decision variables and any hard constraints.
3. **Check for dominance**: for each pair of candidate solutions, check whether one is at least as good on all objectives and strictly better on at least one. If so, the worse solution is dominated.
4. **Generate the Pareto frontier**: identify the set of non-dominated solutions. For continuous problems, use scalarization (weighted sum with varying weights), epsilon-constraint (optimize one objective while constraining others), or evolutionary algorithms. For discrete problems, enumerate and filter.
5. **Characterize the frontier**: describe the shape — is it convex, concave, or disconnected? Identify knees (points where a small sacrifice in one objective yields a large gain in another). Identify extreme points (best on each single objective).
6. **Present options**: show the Pareto frontier as a set of distinct trade-off profiles. Do not reduce to a single score unless weights are genuinely known.
7. **Select** (if weights are available): apply a multi-criteria decision method to pick from the frontier.

## Output
A Pareto frontier — the set of non-dominated solutions. A characterization of the trade-off surface (shape, knees, extremes). A list of dominated solutions. If weights are provided, a recommended solution from the frontier.

## Strengths
Reveals the full trade-off landscape without requiring artificial weighting upfront. Separates the technical question (what is possible) from the value question (what is preferred). Supports negotiation by showing what each stakeholder must give up to get more of what they value.

## Limitations
Computational cost grows with the number of objectives — beyond three objectives, the frontier is hard to visualize and interpret. The frontier may contain many points, overwhelming decision-makers. The method assumes objectives are measurable, which is not always true. The shape of the frontier depends on the formulation of the objectives.

## Common Failure Modes
Presenting a single "optimal" solution from a weighted sum without showing the frontier. Using arbitrary weights and treating the result as objective. Ignoring that some points on the frontier may be practically unreachable due to unmodeled constraints. Generating the frontier but never using it to make a decision. Reducing the problem to two objectives by combining others when the combination is not justified. Confusing a knee point with a universal optimum.

## Verification
Confirm that every solution on the frontier is non-dominated by checking against other feasible solutions. Verify that the frontier spans the full range of each objective. Check that dominated solutions are correctly excluded. Test whether the frontier is stable under small perturbations of the objective functions.

## Combine With
- **trade-off-analysis**: to interpret the frontier and select among options
- **multi-criteria-decision**: to pick from the frontier when weights are available
- **sensitivity-analysis**: to test the robustness of the frontier to parameter changes
- **scenario-planning**: to understand how different futures affect the trade-off landscape

## Conflicts With
- **constrained-optimization**: assumes a single objective; MOO embraces multiple objectives
- **satisficing**: stops at adequate; MOO maps the full possibility space
- **cost-benefit-analysis**: reduces everything to a single metric; MOO preserves multiple dimensions

## Example
A cloud service must choose instance types for a workload. Objectives: minimize cost (dollars/month) and minimize latency (milliseconds). Decision variables: instance count, type, and region. The Pareto frontier reveals that below 50ms latency, cost rises exponentially — each additional millisecond of improvement costs 3x more than the previous. The knee point is at 75ms / $1,200/month. The architecture team can now decide: is the latency gain worth the cost premium, or is the knee point acceptable?

## Selection Metadata
```
id: multi-objective-optimization
category: optimization
best_for: [conflicting objectives, trade-off exploration, design space exploration, stakeholder negotiation]
requires: [multiple objectives, decision variables]
produces: [Pareto frontier, non-dominated solutions, trade-off characterization]
strengths: [reveals trade-offs, no artificial weighting, separates facts from values]
limitations: [computational complexity, frontier interpretation, requires quantifiable objectives]
combine_with: [multi-criteria-decision, trade-off-analysis, sensitivity-analysis, scenario-planning]
avoid_when: [single objective exists, objectives are not quantifiable, problem is trivial]
```