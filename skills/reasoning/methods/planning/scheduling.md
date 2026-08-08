# Scheduling

## Purpose
Order tasks in time, respecting dependencies, resource constraints, and deadlines, to produce a feasible timeline for execution. This method identifies the critical path — the sequence of tasks that determines the minimum project duration.

## When to Use
- When tasks have precedence constraints (A must finish before B can start)
- When deadlines are fixed and you need to know whether the plan can meet them
- When multiple tasks can run in parallel and you need to decide which to start when
- When delays in one task cascade to others and you need to understand the cascade

## When Not to Use
- When tasks are independent and can be done in any order — ordering adds no value
- When timing is flexible and deadlines are not binding
- When the plan is too coarse for temporal ordering to be meaningful (e.g., strategic planning with multi-year horizons)
- When the dominant constraint is resource availability, not time — use resource-planning first

## Problem Signals
- The user describes tasks with "before," "after," "while," "meanwhile," or "depends on"
- The user mentions a fixed deadline and asks "can we make it?" or "when will this be done?"
- The user describes a plan with many parallel workstreams and asks about coordination
- The user mentions that a delay in one area is blocking several other areas

## Inputs
- A set of tasks, each with an estimated duration
- Precedence constraints: which tasks must be completed before which other tasks can begin
- Resource constraints (optional): which resources are needed for which tasks and in what quantity
- Deadline constraints: fixed dates by which certain tasks or the entire plan must be complete

## Procedure
1. **List all tasks with durations.** Be specific about what constitutes completion. Use ranges (best case / expected / worst case) if durations are uncertain.
2. **Map precedence constraints.** For each task, identify its immediate predecessors — tasks that must be completed before this task can begin. Draw a directed graph: nodes are tasks, edges represent "must precede."
3. **Check for cycles.** Traverse the graph. If a cycle exists (A must precede B, B must precede A), the schedule is infeasible. Cycles often indicate a missing decomposition step — one of the tasks in the cycle is really two tasks that can be partially ordered.
4. **Compute the critical path.** Perform a forward pass to compute the earliest start and finish time for each task, assuming all predecessors complete on time. Perform a backward pass from the deadline to compute the latest start time. The tasks where earliest start equals latest start are on the critical path — any delay to them delays the entire project.
5. **Identify float (slack).** For each non-critical task, compute total float = latest start - earliest start. Tasks with large float can be delayed without affecting the deadline. Tasks with zero float are on the critical path.
6. **Apply resource constraints (if applicable).** If resources are limited, some tasks that could run in parallel must be serialized. Apply resource leveling: delay tasks that would exceed resource capacity, even if they have predecessors complete. This may extend the critical path.
7. **Compress the schedule (if needed).** If the computed duration exceeds the deadline, consider: adding resources to critical path tasks (crashing), overlapping tasks that are normally sequential (fast-tracking), or reducing scope. Each option has cost and risk implications.
8. **Generate the schedule.** Produce a timeline showing when each task starts and finishes, which tasks are on the critical path, and where the float lies.

## Output
- A timeline with start and finish dates for each task
- The critical path (the sequence of tasks that determines project duration)
- Float values for non-critical tasks
- Feasibility assessment: can the deadline be met?
- Schedule compression options if the deadline is not met

## Strengths
- Identifies the tasks that actually determine the project duration, so effort can be focused where it matters
- Quantifies how much slack exists in non-critical paths, enabling informed trade-offs
- Handles complex dependency networks systematically
- Surfaces infeasibility early — if the critical path is longer than the available time, no amount of working harder on non-critical tasks will help

## Limitations
- Duration estimates are often inaccurate, especially for novel tasks
- The critical path can shift during execution as tasks complete early or late
- Does not account for variability in a single pass — use PERT (Program Evaluation and Review Technique) or Monte Carlo simulation for probabilistic schedules
- Resource constraints can dramatically change the critical path; the resource-constrained critical path may differ from the precedence-constrained one

## Common Failure Modes
- **Missing dependencies**: forgetting that a task requires a decision, approval, or input that is not captured as a formal predecessor
- **Student syndrome**: teams delay starting non-critical tasks because they have float, then those tasks become critical when something goes wrong
- **Critical path fixation**: optimizing only the critical path while ignoring that near-critical paths can become critical with small delays
- **Duration padding**: each estimator adds a safety margin, and the schedule inherits all of them, producing an unrealistically long timeline. Conversely, aggressive estimates without padding produce a timeline that is certain to slip.
- **Ignoring merge delays**: assuming that when multiple parallel tasks complete, their outputs can be integrated instantly, when in practice integration takes significant time

## Verification
- Is the precedence graph free of cycles?
- Does every task have accurate predecessors identified?
- Has the critical path been computed correctly with a forward and backward pass?
- Are there near-critical paths (float < 10% of duration) that deserve attention?
- Does the schedule include integration and handoff time between tasks?

## Combine With
- resource-planning for adding resource constraints to the schedule
- temporal-reasoning (from logical category) for handling complex temporal constraints (overlaps, windows, deadlines)
- contingency-planning for adding buffer time and response plans for schedule slippage
- hierarchical-planning for scheduling at the sub-goal level and rolling up to the top-level timeline

## Conflicts With
- Methods that ignore time constraints entirely (e.g., pure resource allocation without temporal ordering)
- satisficing: scheduling invests in optimization; satisficing accepts the first adequate order

## Example
**Tasks for a website launch**:
- A: Design mockups (3 days), no predecessors
- B: Backend API (5 days), no predecessors
- C: Frontend development (6 days), requires A and B
- D: Content creation (4 days), no predecessors
- E: Integration testing (3 days), requires C and D
- F: Deployment (1 day), requires E

**Precedence graph**: A and B and D can start immediately. C requires A and B. E requires C and D. F requires E.

**Forward pass**:
- A: days 1-3; B: days 1-5; D: days 1-4
- C: starts day 6 (after both A and B), finishes day 11
- E: starts day 12 (after C and D), finishes day 14
- F: starts day 15, finishes day 15

**Critical path**: B -> C -> E -> F (14 days). A (3 days) has 2 days of float. D (4 days) has 7 days of float.

**Analysis**: If the deadline is 12 days, the schedule is 2 days over. Options: (a) crash B by adding a developer (reduce to 3 days), (b) fast-track C to start 2 days after B begins instead of after B finishes, (c) descope features to reduce C's duration. Option (a) brings the critical path to 12 days, meeting the deadline.

## Selection Metadata
```
id: scheduling
category: planning
best_for: [time-constrained tasks, dependencies, deadline management]
requires: [tasks, durations, dependencies]
produces: [schedule, critical path]
strengths: [identifies critical path, handles dependencies]
limitations: [duration uncertainty, resource constraints]
combine_with: [resource-planning, temporal-reasoning]
avoid_when: [tasks are independent, timing is flexible]
```