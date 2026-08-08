# Decomposition

## Purpose
Break a complex problem into its constituent parts — fundamental components, sub-problems, or causal factors — so that each can be understood and solved independently before reassembling the solution.

## When to Use
- When the problem is too large or complex to solve in one step
- When the problem spans multiple domains, each requiring different expertise or methods
- When you need to identify which parts of a system are causing observed behavior
- When you are in a novel domain and need to build understanding from the ground up
- When the problem resists direct solution and you suspect hidden structure

## When Not to Use
- When the problem is simple enough to solve directly — decomposition adds overhead
- When the components are tightly coupled and cannot be understood in isolation
- When the whole has emergent properties that are lost when the system is decomposed
- When the decomposition itself is the hard part and you lack the domain knowledge to do it correctly

## Problem Signals
- The user describes the problem as "overwhelming," "complex," or "multi-faceted"
- The problem naturally has modules, phases, or layers
- The user says "I don't know where to start"
- The problem involves a system with identifiable components
- Different people or teams are responsible for different parts of the problem

## Inputs
- A clear problem statement
- Domain knowledge about the structure of the problem space
- Any existing frameworks or taxonomies for decomposing problems in this domain

## Procedure

### Step 1: Define the Whole
State the problem as a single, clear objective. If you cannot state the problem in one sentence, you do not understand it well enough yet.

### Step 2: Identify Decomposition Dimensions
Choose a dimension along which to decompose. Common dimensions:
- **Functional**: what functions must the solution perform? (e.g., authenticate, store, retrieve, display)
- **Structural**: what are the physical or logical components? (e.g., frontend, backend, database, cache)
- **Causal**: what factors contribute to the outcome? (e.g., price, quality, marketing, competition)
- **Temporal**: what are the phases or stages? (e.g., design, build, test, deploy)
- **Hierarchical**: what are the levels of abstraction? (e.g., strategy, tactics, operations)

### Step 3: Decompose Recursively
Apply the chosen dimension to break the problem into parts. Then apply the same or different dimensions to each part. Stop when each part is:
- **Solvable**: you can address it with a known method
- **Independent**: it can be solved without solving other parts simultaneously
- **Complete**: the parts together cover the whole problem

### Step 4: Identify Interfaces
For each pair of parts that interact, specify:
- What information or resources flow between them
- What dependencies exist (X must be solved before Y)
- What constraints one part imposes on another

### Step 5: Solve Each Part
Apply the appropriate method to each sub-problem. The method for each part may differ.

### Step 6: Reassemble
Combine the sub-solutions into a complete solution. Verify that:
- The interfaces are satisfied (each part gets what it needs from others)
- No gaps exist (every aspect of the original problem is addressed)
- No conflicts exist (sub-solutions are mutually compatible)

## Output
- A decomposition tree showing the problem broken into parts and sub-parts
- An interface map showing dependencies between parts
- A solution for each leaf-level component
- A reassembled solution for the whole problem

## Strengths
- Reduces complexity: makes large problems tractable
- Enables parallel work: independent parts can be solved simultaneously
- Reveals structure: makes the problem's architecture explicit
- Reusable: sub-solutions to common sub-problems can be reused

## Limitations
- Requires the right decomposition dimension — a poor decomposition makes the problem harder
- Cannot handle emergent properties that arise only from interactions
- The decomposition itself is a design decision that constrains the solution space
- Interface mismatches can cause failure when sub-solutions are combined

## Common Failure Modes
- **Wrong decomposition dimension**: decomposing by function when the problem is structured temporally, or vice versa. The resulting parts are not independent and cannot be solved in isolation.
- **Premature decomposition**: decomposing before understanding the problem well enough. The parts are arbitrary and must be re-decomposed later.
- **Over-decomposition**: breaking the problem into too many tiny pieces, creating excessive coordination overhead. Stop when each part is solvable.
- **Ignoring interfaces**: solving each part in isolation without specifying how they interact. The sub-solutions are individually correct but incompatible when combined.
- **Incomplete decomposition**: missing a part of the problem, leaving a gap in the final solution. Verify that the parts exhaustively cover the problem.

## Verification
- Does the set of parts completely cover the original problem? Check for gaps.
- Can each part be solved independently given its inputs and interfaces? If solving one part requires simultaneously solving another, the decomposition is insufficient.
- Do the sub-solutions reassemble without conflict? Test the interfaces.
- Is the decomposition dimension appropriate? Try an alternative dimension and see if it produces a better decomposition.

## Combine With
- **Systems Thinking**: to understand interactions and emergent properties that decomposition alone may miss
- **Deductive Reasoning**: to solve each sub-problem with logical rigor
- **Fundamental Analysis**: to identify the truly fundamental components from first principles
- **Constraint Analysis**: to identify constraints that each part must satisfy

## Conflicts With
- **Holistic Methods**: when the whole has properties that are not present in any part, decomposition can mislead. Use systems thinking alongside.

## Example
Problem: Reduce customer churn by 20% in the next quarter.

Decomposition by causal factors:
1. Product quality issues → track defect rates, prioritize top 3 bugs
2. Pricing dissatisfaction → analyze competitor pricing, survey price-sensitive customers
3. Poor onboarding experience → measure time-to-first-value, identify drop-off points
4. Lack of engagement → segment users by activity level, design re-engagement campaigns
5. Customer support failures → measure response time and resolution rate

Each factor becomes a sub-problem with its own analysis, metrics, and intervention. The sub-solutions are reassembled into a churn reduction program. The interface: budget allocation across initiatives must sum to the total available budget.

## Selection Metadata
```
id: decomposition
category: first-principles
best_for: [complex problems, novel domains, fundamental understanding]
requires: [problem definition, domain knowledge]
produces: [fundamental components]
strengths: [avoids assumptions, builds from ground truth]
limitations: [requires deep domain knowledge, can be slow]
combine_with: [systems-thinking, deductive-reasoning, fundamental-analysis, constraint-analysis]
avoid_when: [problem is simple, fundamentals are not accessible]
```