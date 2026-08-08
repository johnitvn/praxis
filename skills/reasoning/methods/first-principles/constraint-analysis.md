# Constraint Analysis

## Purpose
Identify, classify, and analyze the constraints that define the feasible solution space for a problem, distinguishing between binding constraints that limit outcomes and non-binding constraints that can be relaxed or ignored.

## When to Use
- When designing a solution and you need to know what is possible
- When evaluating whether a proposed solution is feasible
- When you need to identify which constraints, if relaxed, would yield the greatest improvement
- When multiple constraints interact and you need to understand their joint effect
- When you need to communicate to stakeholders why certain solutions are impossible
- When optimizing and you need to identify the bottleneck

## When Not to Use
- When the problem has no constraints worth analyzing — the solution space is unbounded in all relevant dimensions
- When constraints are so fluid that any analysis will be obsolete before it is used
- When the constraint structure is obvious and there is no disagreement about it
- When you are in a pure exploration phase where constraints should be deliberately ignored to generate creative ideas

## Problem Signals
- The user says "we can't do X because of Y"
- The problem involves trade-offs between competing objectives
- The user is trying to optimize and hitting diminishing returns
- The problem is described as "impossible" or "infeasible"
- The user asks "what would it take to make this work?"
- Multiple stakeholders are imposing conflicting requirements

## Inputs
- A clear statement of the objective or desired outcome
- A list of constraints (requirements, limitations, restrictions)
- For each constraint: its source, its type, and whether it is negotiable
- The current solution (if one exists) to compare against the feasible region

## Procedure

### Step 1: Collect All Constraints
List every constraint that applies to the problem. Sources of constraints:
- Physical laws (cannot be violated)
- Resource limits (budget, time, personnel, materials)
- Regulatory requirements (legal, compliance, standards)
- Technical constraints (platform limitations, compatibility, performance)
- Business constraints (strategic alignment, stakeholder requirements)
- Domain constraints (industry standards, customer expectations)

### Step 2: Classify Each Constraint
For each constraint, classify it along three dimensions:

**Hardness**:
- **Hard**: cannot be violated under any circumstances (physical laws, legal requirements, mathematical impossibility)
- **Soft**: can be violated at a cost (budget, timeline, quality targets)
- **Negotiable**: imposed by stakeholders and can be changed through negotiation

**Type**:
- **Equality**: must equal a specific value (e.g., "the system must process exactly 1,000 transactions per second")
- **Inequality**: must be less than, greater than, or within a range (e.g., "latency must be under 100ms")
- **Binary**: must or must not include a feature (e.g., "must support OAuth")

**Certainty**:
- **Known**: the constraint is well-understood and quantified
- **Estimated**: the constraint is approximate
- **Uncertain**: the constraint may or may not apply, or its value is unknown

### Step 3: Identify Interactions
Determine how constraints interact:
- **Independent**: constraints that do not affect each other
- **Reinforcing**: satisfying one makes it easier to satisfy another
- **Conflicting**: satisfying one makes it harder to satisfy another
- **Redundant**: one constraint is strictly tighter than another in all cases

### Step 4: Determine the Feasible Region
Map the constraints onto the solution space. The feasible region is the set of all solutions that satisfy all hard constraints. Visualize in 2D or 3D if possible; use constraint propagation for higher dimensions.

### Step 5: Identify Binding Constraints
A constraint is binding if the current or optimal solution lies exactly on the constraint boundary — meaning the constraint is actively limiting the outcome. Relaxing a binding constraint improves the objective; relaxing a non-binding constraint does not.

### Step 6: Analyze Slack
For each inequality constraint, compute the slack — the distance between the current solution and the constraint boundary. Large slack means the constraint is not limiting. Zero slack means the constraint is binding.

### Step 7: Explore Constraint Relaxation
For each binding constraint, ask:
- Can this constraint be relaxed? If so, at what cost?
- What is the marginal benefit of relaxing it by one unit?
- Is there a constraint elsewhere that would become binding if this one is relaxed?
- Who controls this constraint and what would it take to negotiate it?

### Step 8: Formulate Recommendations
- Identify which constraints are the true bottlenecks
- Recommend which constraints to negotiate or relax for maximum impact
- Identify which constraints are self-imposed and can be removed with no external cost
- Flag constraints that are assumed but not verified

## Output
- A complete constraint inventory with classifications
- A description of the feasible region
- A ranked list of binding constraints with their marginal impact
- Slack analysis for non-binding constraints
- Recommendations for constraint negotiation or relaxation

## Strengths
- Defines the problem clearly: makes explicit what is possible and what is not
- Identifies leverage points: shows which constraints, if relaxed, yield the most improvement
- Prevents wasted effort: avoids pursuing solutions that violate hard constraints
- Surfaces hidden constraints: reveals self-imposed or assumed constraints that are not real

## Limitations
- May miss hidden constraints that are not obvious or not articulated
- Constraints may change over time, making the analysis obsolete
- The interaction between multiple constraints can be complex and non-linear
- Hard constraints may be treated as softer than they are, or soft constraints as harder

## Common Failure Modes
- **Treating soft constraints as hard**: assuming a budget or timeline is fixed when it is actually negotiable. This artificially shrinks the feasible region.
- **Treating hard constraints as soft**: assuming a physical law or legal requirement can be worked around. This leads to infeasible solutions.
- **Missing hidden constraints**: constraints that "everyone knows" and therefore never articulate. Stakeholders may not mention the most obvious constraints.
- **Analyzing constraints in isolation**: ignoring interactions between constraints. Relaxing one constraint may make another suddenly binding.
- **Over-constraining**: accepting all stated constraints at face value without verifying them. Many constraints are historical, self-imposed, or based on outdated assumptions.
- **Ignoring uncertainty**: treating estimated or uncertain constraints as if they are known exactly. A constraint that is "approximately X" should be analyzed with a sensitivity range.

## Verification
- Are all constraints traceable to a source? If a constraint cannot be justified, it may be a convention rather than a real constraint.
- Does the feasible region contain at least one viable solution? If not, the problem is infeasible as stated and constraints must be renegotiated.
- Are the binding constraints actually limiting? Test by relaxing each one and observing the effect on the objective.
- Have all stakeholders verified the constraint list? Missing constraints are the most common error.
- Is the classification of each constraint as hard/soft/negotiable agreed upon? Misclassification leads to wrong conclusions.

## Combine With
- **Optimization Methods**: to find the best solution within the feasible region defined by constraints
- **Trade-off Analysis**: to evaluate solutions that lie on the Pareto frontier of multiple constraints
- **Fundamental Analysis**: to distinguish between fundamental constraints and conventional ones
- **Decomposition**: to break a complex constraint system into manageable sub-problems
- **Sensitivity Analysis**: to assess how changes in constraint values affect the solution

## Conflicts With
- **Creative Methods**: when brainstorming, constraints should sometimes be deliberately ignored. Constraint analysis can prematurely limit ideation. Use it after the divergent phase, not during it.

## Example
Problem: Deploy a new feature to production by the end of Q3.

Constraints collected:
1. Feature must pass all existing automated tests (hard, technical)
2. Deployment window is Tuesday 2-4 AM (soft, operational — negotiable)
3. Budget remaining: $50,000 (soft, financial — fixed for this quarter)
4. Must support 10,000 concurrent users (hard, performance requirement)
5. Database schema change must be backward-compatible (hard, architectural)
6. Marketing wants the launch before the competitor's conference (soft, strategic — negotiable)

Classification and analysis:
- Constraints 1, 4, and 5 are hard technical constraints. Any solution must satisfy them.
- Constraint 2 (deployment window) has slack — the team can request a special window.
- Constraint 3 (budget) is binding — the remaining scope must fit within $50,000.
- Constraint 6 (marketing deadline) may be soft but drives the timeline.

Binding constraint: the combination of budget and the hard technical requirements defines the scope that can be delivered. If the scope cannot be delivered within $50,000, either the budget must increase, the scope must decrease, or the deadline must slip.

Recommendation: Reduce scope to fit within the $50,000 budget while satisfying all hard constraints. Negotiate a special deployment window to avoid the Tuesday restriction. Communicate the scope trade-off to marketing so they can adjust their conference plans.

## Selection Metadata
```
id: constraint-analysis
category: first-principles
best_for: [design problems, optimization, feasibility assessment]
requires: [constraints, requirements]
produces: [feasible region, binding constraints]
strengths: [defines solution space, identifies critical constraints]
limitations: [may miss hidden constraints, constraints may change]
combine_with: [optimization-methods, trade-off-analysis, fundamental-analysis, decomposition, sensitivity-analysis]
avoid_when: [constraints are fluid, pure exploration phase]
```