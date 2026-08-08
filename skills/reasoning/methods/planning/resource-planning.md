# Resource Planning

## Purpose
Match limited resources (people, budget, equipment, time) to demands in a way that satisfies constraints and achieves the plan's objectives. This method identifies bottlenecks, overallocations, and feasible allocations before execution begins.

## When to Use
- When resources are constrained and cannot be assumed unlimited
- When multiple tasks or projects compete for the same pool of resources
- When the plan's feasibility depends on who or what is available at specific times
- When resource bottlenecks are likely to determine the critical path

## When Not to Use
- When resources are abundant relative to demand — do not optimize what is not constrained
- When resource availability is unknowable (e.g., a startup with uncertain funding)
- When the plan is too vague to estimate resource requirements for individual tasks
- When the primary constraint is not resources but sequencing, dependencies, or quality

## Problem Signals
- The user mentions limited headcount, budget caps, or equipment constraints
- The plan includes phrases like "we need to figure out who can do this" or "we don't have enough X"
- Multiple tasks are described as needing the same specialized person or tool
- The user describes a plan that seems ambitious relative to the stated resources

## Inputs
- A set of tasks, each with a resource requirement (type, quantity, duration)
- An inventory of available resources with their capacities and availability windows
- Allocation constraints (a person cannot work on two tasks simultaneously, a machine has a maximum throughput)
- The objective: minimize cost, minimize duration, maximize utilization, or a weighted combination

## Procedure
1. **Inventory resources.** List every resource type and every instance of each type. Be specific: "3 senior backend engineers (Alice, Bob, Carol)" not "engineering capacity." For each resource, note its availability window and any constraints (Alice is on leave next week, Bob works half-time).
2. **Estimate task demands.** For each task, specify: which resource types it requires, how many units of each, and for what duration. Distinguish between exclusive-use resources (one task at a time) and shareable resources (multiple tasks can draw simultaneously).
3. **Identify the binding constraint.** Compare total demand to total supply for each resource type. The resource type with the highest demand-to-supply ratio is the binding constraint. If all ratios are below 1.0, resources are not the bottleneck — focus on scheduling or scope instead.
4. **Allocate to the binding constraint first.** Assign the most constrained resource to tasks in priority order. This determines the shape of the entire allocation. If the binding constraint's allocation fails, the plan is infeasible — you must either increase supply, reduce demand, or change the scope.
5. **Allocate remaining resources.** With the binding constraint allocated, assign the remaining resources. These allocations are constrained by the binding constraint's schedule (a task cannot start until all its resources are available).
6. **Detect overallocations.** After allocation, check every resource for periods where demand exceeds capacity. Flag these as infeasible. Check for resource contention where two high-priority tasks need the same resource at the same time.
7. **Level the allocation.** If overallocations exist, try: delaying lower-priority tasks, splitting tasks that can be interrupted, substituting alternative resources, or increasing capacity (overtime, contractors, additional equipment).
8. **Validate the allocation.** Confirm that the plan's objectives are still met after leveling. If the leveled allocation violates deadlines or budget, the plan is not feasible with the given resources.

## Output
- A resource allocation table mapping each resource to tasks over time
- Identification of the binding constraint
- Overallocation flags and their resolutions
- Feasibility assessment: can the plan be executed with the available resources?

## Strengths
- Surfaces infeasibility early, before resources are committed
- Identifies the single constraint that determines the plan's throughput
- Enables trade-off decisions: "we can hit the deadline if we hire a contractor, otherwise we must descope"
- Provides an objective basis for resource negotiations

## Limitations
- Resource estimates are often inaccurate, especially for novel tasks
- Static allocation assumes fixed resource availability; real availability changes
- Does not account for resource quality variation (two senior engineers are not interchangeable with two junior engineers)
- Resource leveling can produce allocations that are technically feasible but practically fragile (no slack)

## Common Failure Modes
- **Abstract resource modeling**: using "engineering weeks" instead of named individuals, which hides the fact that only one person knows the relevant codebase
- **Ignoring ramp-up costs**: assigning a person to a task without accounting for the time needed to become productive
- **100% utilization fallacy**: allocating resources at full capacity, leaving no slack for unexpected delays, sick days, or context switching overhead
- **Binding constraint misidentification**: treating the wrong resource as the bottleneck, optimizing around it, and discovering the real constraint too late
- **Static snapshot**: producing a single allocation and not updating it as tasks complete early or late, resource availability changes, or new tasks emerge

## Verification
- Is every task assigned the resources it needs to start and complete?
- Are there any periods where a resource is allocated to more than its capacity?
- Has the binding constraint been identified and is the allocation built around it?
- Is there slack in the allocation (at least 10-20%) to absorb variability?

## Combine With
- scheduling for sequencing tasks within the resource allocation
- constrained-optimization (from optimization category) for mathematically optimal allocations
- trade-off-analysis (from optimization category) for evaluating resource-vs-scope decisions
- hierarchical-planning for allocating resources at the sub-goal level

## Conflicts With
- satisficing: resource planning seeks optimal or near-optimal allocation; satisficing accepts the first adequate one
- Approaches that assume resources are fungible or unlimited

## Example
**Scenario**: A team of 3 engineers (Alice, Bob, Carol) must complete 4 features for a release in 2 weeks. Alice is the only one familiar with the payment module. Bob and Carol are full-stack. Bob is on leave for 3 days.

**Resource inventory**:
- Alice: 10 days available, specialized in payments
- Bob: 7 days available (3 days leave), full-stack
- Carol: 10 days available, full-stack

**Task demands**:
1. Payment API refactor: requires Alice (exclusive), 6 days
2. User dashboard: requires 1 full-stack engineer, 8 days
3. Notification service: requires 1 full-stack engineer, 5 days
4. Authentication update: requires 1 full-stack engineer, 4 days

**Binding constraint**: Alice's time. She is the only one who can do the payment refactor (6 of her 10 days), and she is also a full-stack engineer. The total full-stack demand is 8+5+4 = 17 days, but available full-stack capacity is Alice's remaining 4 + Bob's 7 + Carol's 10 = 21 days. The payment refactor is the binding constraint.

**Allocation**:
- Alice: Payment API refactor (days 1-6), then assists with dashboard (days 7-10)
- Bob: Dashboard (days 1-7, accounting for his leave days 3-5)
- Carol: Authentication update (days 1-4), then Notification service (days 5-9)

**Feasibility**: Dashboard receives 4 days from Bob + 4 days from Alice = 8 days. All features complete within 10 days. The plan is feasible with 1 day of slack.

## Selection Metadata
```
id: resource-planning
category: planning
best_for: [resource-constrained projects, capacity planning, allocation]
requires: [resources, demands, constraints]
produces: [feasible allocation]
strengths: [handles constraints, identifies bottlenecks]
limitations: [requires accurate estimates, static]
combine_with: [constrained-optimization, scheduling]
avoid_when: [resources are abundant, constraints are loose]
```