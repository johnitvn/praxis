# Hierarchical Planning

## Purpose
Decompose a complex goal into a tree of sub-goals, plan each sub-goal independently, and then compose the sub-plans into a coherent overall plan. This method manages complexity by pushing detail to lower levels of abstraction.

## When to Use
- When the goal has natural decomposition boundaries (phases, modules, layers)
- When sub-goals can be planned semi-independently with well-defined interfaces between them
- When the problem is too large to reason about monolithically in a single pass
- When different parts of the plan require different expertise, time horizons, or levels of granularity

## When Not to Use
- When the goal is simple enough to plan in a single step
- When sub-goals are tightly coupled with circular dependencies that prevent modular decomposition
- When the decomposition itself is the hard part and you lack domain knowledge to do it correctly
- When the cost of integrating sub-plans exceeds the benefit of decomposing

## Problem Signals
- The user describes a goal with nested "and then" or "which requires" clauses
- The plan spans multiple time horizons (immediate, short-term, long-term)
- The problem statement mentions "breaking down," "phases," "layers," or "levels"
- The user cannot articulate the whole plan at once and describes it in pieces

## Inputs
- A top-level goal stated as a clear, verifiable outcome
- Domain knowledge sufficient to identify natural decomposition boundaries
- The set of constraints that span across sub-goals (cross-cutting concerns)

## Procedure
1. **State the top-level goal** as a single, verifiable success condition. If you cannot state it in one sentence, you are not ready to decompose.
2. **Identify decomposition dimensions.** Common dimensions: temporal (phases), structural (modules/components), functional (capabilities), or abstraction (strategy/tactics/operations). Pick the dimension that minimizes coupling between sub-goals.
3. **Decompose into sub-goals.** Each sub-goal must be a necessary condition for the top-level goal. No sub-goal should depend on internal details of another sub-goal — only on its output or completion.
4. **Define interfaces between sub-goals.** For each sub-goal, specify: what it requires as input (from parent or siblings), what it produces as output, and its completion criterion.
5. **Detect cross-cutting constraints.** Identify constraints that affect multiple sub-goals (resource limits, deadlines, quality standards). These must be managed at the parent level, not within individual sub-plans.
6. **Plan each sub-goal.** Apply the same method recursively if a sub-goal is still complex, or switch to a more granular method (scheduling, resource-planning) if it is simple enough.
7. **Validate composition.** Walk the plan tree bottom-up: check that each sub-plan's outputs satisfy the inputs required by its sibling sub-plans and the parent. Verify that cross-cutting constraints are met.
8. **Add integration steps.** Insert explicit coordination steps where sub-plans hand off to each other. These are often the highest-risk points.

## Output
- A plan tree with the top-level goal at the root, sub-goals as children, and leaf-level tasks at the bottom
- Interface specifications for each sub-goal (inputs, outputs, completion criteria)
- Cross-cutting constraint register
- Integration points between sub-plans

## Strengths
- Scales to arbitrarily complex goals by recursive decomposition
- Sub-plans are reusable across different top-level goals
- Different levels of the hierarchy can be planned at different levels of abstraction
- Makes it clear which parts of the plan can be executed in parallel

## Limitations
- A wrong decomposition creates a plan that looks coherent but fails at integration
- Interactions between sub-goals can be missed if the decomposition is too rigid
- The top-level goal may need redefinition as lower-level details reveal new constraints
- Sub-plan optimization may produce locally optimal but globally suboptimal results

## Common Failure Modes
- **Premature decomposition**: decomposing before the goal is well-understood, producing a plan tree that solves the wrong problem
- **Over-decomposition**: breaking into too many sub-goals, creating integration overhead that exceeds the complexity of the original goal
- **Interface neglect**: planning sub-goals in isolation without defining interfaces, leading to integration failures
- **Level confusion**: mixing abstraction levels (e.g., strategic and tactical decisions at the same level), which obscures dependencies
- **Cross-cutting blindness**: failing to identify constraints that span sub-goals, then discovering them late when they force rework

## Verification
- Can every sub-goal be traced to the top-level goal as a necessary condition?
- Are the interfaces between sub-goals explicit and complete?
- Does the plan tree have consistent abstraction levels at each depth?
- Have cross-cutting constraints been identified and allocated to the correct level?

## Combine With
- decomposition (from first-principles category) for finding the right decomposition dimensions
- contingency-planning for adding resilience at each level
- scheduling for ordering leaf-level tasks
- resource-planning for allocating constrained resources across sub-goals

## Conflicts With
- satisficing: hierarchical planning invests in structure; satisficing accepts the first adequate solution
- Approaches that assume a flat, non-decomposable solution space

## Example
**Goal**: Migrate a production database to a new infrastructure provider with less than 5 minutes of downtime.

**Decomposition dimension**: temporal (phases).

**Sub-goals**:
1. *Preparation phase*: provision new infrastructure, replicate data, validate schema compatibility. Interface: produces a ready, synchronized target database.
2. *Rehearsal phase*: execute a dry-run migration, measure downtime, tune the cutover procedure. Interface: produces a validated cutover script with measured timing.
3. *Cutover phase*: stop writes, finalize replication, switch traffic, validate. Interface: requires the ready target and validated script from previous phases; produces a live, validated new database.
4. *Rollback capability*: maintain the old database in read-only mode for 24 hours, with a documented revert procedure. Interface: requires the old database to remain accessible; produces a safety net.

**Cross-cutting constraint**: the 5-minute downtime budget applies to the cutover phase but constrains design decisions in every phase. The rehearsal phase must validate that the combined cutover steps fit within the window.

## Selection Metadata
```
id: hierarchical-planning
category: planning
best_for: [complex goals, decomposable objectives, multi-level planning]
requires: [goal, decomposition]
produces: [plan hierarchy]
strengths: [handles complexity, reusable sub-plans]
limitations: [decomposition may be wrong, interactions between levels]
combine_with: [decomposition, contingency-planning]
avoid_when: [goal is simple, decomposition is not possible]
```