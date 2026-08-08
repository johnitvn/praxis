# Temporal Reasoning

## Purpose
Temporal reasoning analyzes the ordering, duration, overlap, and constraints of events in time. It determines what can happen when, what must happen before or after what, and whether a set of temporal constraints is consistent.

## When to Use
- When events have ordering constraints (A must happen before B, B and C can happen in parallel).
- When deadlines, durations, or time windows constrain what is possible.
- When analyzing schedules, sequences, or processes for consistency and feasibility.
- When reasoning about concurrency, synchronization, or race conditions.

## When Not to Use
- When temporal constraints are absent or so loose that any ordering is valid.
- When the problem is purely atemporal — when timing and ordering are irrelevant.
- When the problem is about rates or frequencies rather than ordering (use statistical reasoning).
- When the number of events and constraints is so large that manual temporal reasoning is intractable.

## Problem Signals
- The problem contains "before," "after," "during," "while," "until," "when," "first/then," "simultaneously."
- The user asks about scheduling: "Can we finish all of this by Friday?"
- The problem involves dependencies: "Task C depends on A and B completing first."
- The user describes a sequence of events with constraints and asks if it is possible.
- The problem involves concurrency: "Can these two operations happen at the same time?"

## Inputs
- A set of events, tasks, or time points.
- Temporal relations between them: before, after, during, overlaps, meets, starts, finishes (Allen's interval algebra).
- Duration constraints: minimum and maximum durations for events.
- Deadline or time-window constraints: events must occur within specific intervals.

## Procedure
1. **Enumerate all events.** List every event, task, or time point. Name them clearly.
2. **Classify temporal relations.** For each pair of events, determine the temporal relation. Use Allen's 13 interval relations if events have duration: before, meets, overlaps, starts, during, finishes, equals, and their inverses.
3. **Build a temporal constraint graph.** Represent events as nodes and constraints as directed edges. An edge A → B means A must occur before B.
4. **Check for cycles.** A cycle in the constraint graph means the constraints are inconsistent — something must be both before and after itself. This is the most common temporal reasoning failure.
5. **Compute transitive closure.** If A is before B and B is before C, then A is before C. Infer all implied constraints.
6. **Identify critical paths.** For scheduling problems, compute the longest path through the constraint graph — this is the minimum possible duration.
7. **Check deadlines.** For each event with a deadline, verify that the earliest possible time it can occur is before the deadline.
8. **Identify flexibility.** Which events have slack? Which orderings are unconstrained and could be changed?

## Output
- A determination of consistency: are the temporal constraints satisfiable?
- The transitive closure: all implied temporal relations.
- For scheduling: the earliest and latest possible time for each event.
- The critical path: the sequence of events that determines the minimum total duration.
- A valid total ordering (schedule) if one exists that satisfies all constraints.

## Strengths
- Handles concurrency and parallelism explicitly.
- Detects cyclic constraints that make a schedule impossible.
- Computes the critical path — identifies which events cannot be delayed.
- Formal and checkable: temporal constraint satisfaction is a well-understood problem.

## Limitations
- Combinatorial explosion: the number of constraints grows quadratically with events.
- Requires precise constraints — vague temporal relations ("roughly after") are hard to formalize.
- Assumes deterministic durations — real-world durations are often uncertain.
- Allen's interval algebra is complete for qualitative relations but does not handle metric constraints natively.

## Common Failure Modes
- **Missing transitive constraints.** The agent checks only explicit constraints and misses implied ones. Always compute transitive closure.
- **Ignoring duration.** Treating events as instantaneous when they have duration. Use interval relations, not point relations, when events take time.
- **Confusing concurrency with simultaneity.** "A and B happen at the same time" is rarely true for intervals — they may overlap, or one may contain the other.
- **Overlooking resource constraints.** Temporal reasoning alone does not model resource limitations. Two tasks may be temporally independent but cannot happen concurrently because they share a resource.
- **Cycle blindness.** Not checking for cycles in the constraint graph. A cycle means the problem is impossible — the agent should report this, not propose a schedule.

## Verification
- Is the constraint graph acyclic? If there is a cycle, the constraints are inconsistent.
- For each event, is its earliest possible time consistent with its deadline?
- Does the critical path duration match the sum of durations along the longest path?
- Are there any implied constraints that contradict explicit constraints? This indicates an error.

## Combine With
- **Constraint reasoning** — use formal constraint solvers for complex temporal problems.
- **Scheduling** — use temporal reasoning to verify schedule feasibility, then scheduling methods to optimize.
- **Resource planning** — combine temporal constraints with resource constraints to find feasible allocations.
- **Risk analysis** — use temporal reasoning to identify where delays would cascade into deadline misses.

## Example
**Problem:** A deployment pipeline has: Build (10 min), Test (15 min, must start after Build completes), Deploy-Staging (5 min, must start after Test completes), Deploy-Prod (5 min, must start after Deploy-Staging completes). Smoke tests (8 min) can run any time after Deploy-Staging starts. The release window is 45 minutes. Is the pipeline feasible? What is the critical path?

**Application:**
1. Events with durations: Build(10), Test(15), Deploy-Staging(5), Deploy-Prod(5), Smoke(8).
2. Constraints: Build < Test, Test < Deploy-Staging, Deploy-Staging < Deploy-Prod, Deploy-Staging starts before Smoke starts (or Smoke starts after Deploy-Staging starts).
3. Constraint graph: Build → Test → Deploy-Staging → Deploy-Prod. Smoke is parallel to Deploy-Staging+Deploy-Prod.
4. No cycles — constraints are consistent.
5. Critical path: Build(10) + Test(15) + Deploy-Staging(5) + Deploy-Prod(5) = 35 minutes.
6. Smoke tests (8 min) run in parallel with Deploy-Staging(5) + Deploy-Prod(5) = 10 min, so they are not on the critical path.
7. Total minimum time: 35 minutes. Release window is 45 minutes. Feasible with 10 minutes of slack.

## Selection Metadata
```
id: temporal-reasoning
category: logical
best_for: [sequencing, scheduling, deadline analysis]
requires: [temporal constraints, ordering relations]
produces: [valid sequences]
strengths: [handles concurrency, detects cycles]
limitations: [requires precise constraints, combinatorial explosion]
combine_with: [constraint-reasoning, scheduling]
avoid_when: [temporal constraints are loose]
```