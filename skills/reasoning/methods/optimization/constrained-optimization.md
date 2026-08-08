# Constrained Optimization

## Purpose
Find the best solution to a formalized problem subject to explicit constraints on what is allowed.

## When to Use
When the problem has a well-defined objective function that can be maximized or minimized, and a set of constraints that define the feasible region. When trade-offs between options are governed by measurable quantities. When resource budgets, capacity limits, or regulatory bounds bound the solution space. When the problem is a scheduling, allocation, routing, or design problem with a clear fitness metric.

## When Not to Use
When the objective cannot be expressed as a function of decision variables. When constraints are vague, contested, or cannot be formalized. When the problem has multiple conflicting objectives that cannot be reduced to a single metric (use multi-objective optimization instead). When the solution space is too large or ill-defined for formal modeling.

## Problem Signals
The problem description mentions maximizing or minimizing a quantity (cost, time, throughput, utilization). There are explicit limits: budgets, deadlines, capacity ceilings, minimum requirements. The question is "what is the best possible X given Y constraints?" The problem is a scheduling, allocation, or design problem with a single clear metric.

## Inputs
- **Decision variables**: the knobs you can turn to change the solution
- **Objective function**: the quantity to maximize or minimize, expressed in terms of decision variables
- **Constraints**: equalities or inequalities that restrict the values decision variables can take
- **Domain** (optional): whether variables are continuous, integer, or binary

## Procedure
1. **Identify decision variables**: list every parameter you can control. Name them explicitly.
2. **Define the objective**: express the goal as a function of those variables. State whether it is to be maximized or minimized.
3. **Enumerate constraints**: list every restriction as an equality or inequality. Distinguish hard constraints (must hold) from soft constraints (preferences).
4. **Check feasibility**: determine whether any solution exists that satisfies all constraints. If not, identify which constraints conflict and relax the least critical.
5. **Solve**: apply the appropriate algorithm for the problem class (linear programming, integer programming, dynamic programming, constraint satisfaction). For small discrete problems, exhaustive enumeration may be practical.
6. **Verify**: confirm the solution satisfies all constraints and achieves the claimed objective value.
7. **Sensitivity check**: vary key parameters (constraint bounds, objective coefficients) to see how the solution changes. Identify which constraints are binding — tightening them would change the solution.

## Output
An optimal solution (values for all decision variables) and the optimal objective value. A list of binding constraints. A sensitivity analysis showing how much parameters can change before the solution changes.

## Strengths
Finds the provably best solution when one exists. Makes trade-offs explicit and quantitative. The formal structure is auditable and reproducible. Well-developed algorithms exist for common problem classes.

## Limitations
Requires the problem to be fully formalizable, which is rare in open-ended reasoning. The model is only as good as its formulation — a poorly chosen objective optimizes the wrong thing. Local optima can trap gradient-based solvers. The optimal solution may be fragile to small changes in assumptions.

## Common Failure Modes
Optimizing a proxy metric that does not capture the real goal. Formulating constraints that are too tight, making the problem infeasible. Formulating constraints that are too loose, producing trivial solutions. Ignoring that the optimal solution may be impractical for unmodeled reasons. Assuming linearity when the real system is nonlinear. Confusing a local optimum with the global optimum. Spending more effort on optimization than the value of the improvement.

## Verification
Confirm the solution satisfies every constraint. Check that no other feasible solution improves the objective (for small problems, enumerate; for large, verify optimality conditions). Test whether the solution is robust to small perturbations in parameters. Confirm the objective function actually captures the real goal.

## Combine With
- **sensitivity-analysis**: to understand how robust the optimum is
- **trade-off-analysis**: when constraints are negotiable and trade-offs need exploration
- **multi-criteria-decision**: when the objective must be decomposed into weighted criteria

## Conflicts With
- **satisficing**: constrained optimization seeks the best; satisficing stops at good enough
- **design-thinking**: formal optimization assumes well-defined objectives; design thinking assumes objectives emerge through iteration

## Example
A delivery company needs to assign 50 packages to 10 drivers to minimize total travel time. Decision variables: which driver takes which package, and in what order. Objective: minimize sum of travel times. Constraints: each package assigned to exactly one driver, each driver's route under 4 hours, driver capacity limits. The problem is a vehicle routing problem — a well-studied constrained optimization class. After solving, the binding constraint is driver capacity on 3 routes; relaxing it by adding one driver reduces total time by 12%.

## Selection Metadata
```
id: constrained-optimization
category: optimization
best_for: [resource allocation, scheduling, design optimization, routing]
requires: [objective function, constraints, decision variables]
produces: [optimal solution, optimal objective value, binding constraints]
strengths: [finds best solution, handles constraints, auditable]
limitations: [requires formal model, local optima, fragile to assumptions]
combine_with: [sensitivity-analysis, trade-off-analysis, multi-criteria-decision]
avoid_when: [problem is not formalizable, objectives conflict, solution space is ill-defined]
```