# Feedback Analysis

## Purpose
Identify and characterize feedback loops within a system to explain dynamic behavior — growth, collapse, oscillation, stability — and to locate intervention points that change the system's trajectory.

## When to Use
- When a system exhibits growth that accelerates or decelerates over time.
- When a system oscillates, overshoots, or collapses despite stable inputs.
- When you need to explain why an intervention produced a weaker or opposite effect than expected.
- When you have identified loops in a systems map and need to analyze their dynamics.
- When you are asked to predict whether a system is stable, will grow, or will collapse.

## When Not to Use
- When the system is static with no meaningful feedback.
- When the only feedback loops are trivial (e.g., a thermostat that works as designed).
- When you lack information about the direction and strength of relationships.

## Problem Signals
- "We fixed it, but it came back worse."
- A system that seems to have a mind of its own, resisting every intervention.
- Boom-and-bust cycles that repeat despite efforts to stabilize.
- Exponential growth that suddenly hits a limit and collapses.
- "The more we do X, the more we need to do X."

## Inputs
- A relationship map (ideally from systems-thinking).
- For each relationship: direction of influence (positive/same-direction or negative/opposite-direction), strength, and any delays.
- The time horizon of interest.

## Procedure
1. Trace every closed loop in the system. A loop exists when you can follow relationships from a component back to itself.
2. Classify each loop as reinforcing or balancing:
   - Count the number of negative (opposite-direction) links in the loop.
   - An even number of negative links (including zero) = reinforcing (amplifies change, produces exponential growth or collapse).
   - An odd number of negative links = balancing (resists change, produces equilibrium or oscillation).
3. Name each loop. The name should describe what the loop does: "Success to the Successful," "Shifting the Burden," "Limits to Growth," "Fixes that Fail."
4. For each loop, assess dominance: which loop currently controls the system's behavior? Dominance can shift over time — a reinforcing loop may dominate during growth, then a balancing loop takes over near a limit.
5. Identify delays in each loop. A delay determines how long it takes for an action to produce its effect. Long delays in balancing loops cause overshoot and oscillation. Long delays in reinforcing loops can mask growth until it is too late to stop.
6. Predict behavior: for the dominant loop, describe the expected trajectory (exponential growth, goal-seeking, oscillation, S-shaped growth with overshoot).
7. Identify intervention points: to dampen a reinforcing loop, weaken the positive links. To strengthen a balancing loop, shorten delays or increase the strength of corrective action. To shift dominance, target the links that determine which loop is active.

## Output
- A catalog of feedback loops, each labeled with type (reinforcing/balancing), name, components, and delays.
- The currently dominant loop and its expected trajectory.
- A prediction of system behavior over the time horizon.
- A ranked list of intervention points with expected effects on loop dynamics.

## Strengths
- Provides a structural explanation for dynamic behavior that static analysis misses.
- Reveals why obvious interventions fail: they often strengthen the feedback loop that maintains the problem.
- Makes delays explicit, which is critical for anticipating overshoot and oscillation.

## Limitations
- Requires accurate information about relationship direction and strength; guesses produce misleading loop classifications.
- Does not handle systems where relationships change qualitatively (e.g., a positive link that becomes negative above a threshold).
- Real systems have many loops; identifying which one dominates is a judgment call.

## Common Failure Modes
- **Loop enumeration without analysis**: the agent lists every loop but never identifies dominance or predicts behavior. A catalog is not an analysis.
- **Misclassifying loops**: miscounting negative links (common in loops with many components) and labeling a reinforcing loop as balancing or vice versa.
- **Ignoring delays**: treating all loops as instantaneous, which masks the oscillatory behavior that delays produce.
- **Focusing only on reinforcing loops**: agents often gravitate toward the dramatic (exponential growth) and miss the balancing loops that actually govern the system's stable state.

## Verification
- Are all loops correctly classified? Re-count the negative links in each loop.
- Is the dominant loop identified, and is the rationale for dominance stated?
- Are delays explicitly documented for loops where they matter?
- Does the predicted behavior match the observed behavior that prompted the analysis?

## Combine With
- **systems-thinking**: for the relationship map that feedback analysis requires.
- **causal-graph-reasoning**: for formalizing causal relationships when data is available.
- **emergence-analysis**: when feedback loops produce macro-level patterns that the component rules alone do not predict.
- **scenario-planning**: to explore how feedback dynamics play out under different conditions.

## Conflicts With
- **static analysis**: assuming the system is at equilibrium and ignoring the dynamics that feedback analysis reveals.
- **linear extrapolation**: projecting current trends without considering the feedback loops that will change the trend.

## Example

**Problem**: A startup's user growth is stalling despite increasing marketing spend.

**Loop analysis**:
- R1 (reinforcing): Users -> word-of-mouth referrals -> new users. This drove early growth.
- R2 (reinforcing): Marketing spend -> new users -> revenue -> more marketing spend. This is the current strategy.
- B1 (balancing): Users -> server load -> performance degradation -> user churn -> fewer users. This is now dominant.
- B2 (balancing): Marketing spend -> user acquisition cost (rising as the easy users are already acquired) -> fewer new users per dollar.

**Dominance**: B1 and B2 have overtaken R1 and R2. The system is in a "Limits to Growth" archetype.

**Prediction**: Without intervention, marketing spend efficiency will continue to decline. If performance degrades further, churn will accelerate and user count will decline.

**Intervention**: The leverage is in B1 (reduce churn by fixing performance) and B2 (shift marketing to channels with lower acquisition costs or improve the product so viral coefficient R1 strengthens). More marketing spend in the current channel will produce diminishing returns.

## Selection Metadata
```
id: feedback-analysis
category: systems
best_for: [dynamic systems, growth/decay patterns, stability analysis, oscillation, policy resistance]
requires: [feedback loops, relationship directions, delay estimates, time horizon]
produces: [loop catalog, dominance assessment, trajectory prediction, intervention points]
strengths: [explains counterintuitive behavior, identifies leverage, makes delays explicit]
limitations: [requires accurate relationship data, cannot handle qualitative changes in relationships, dominance is judgment-based]
combine_with: [systems-thinking, causal-graph-reasoning, emergence-analysis, scenario-planning]
avoid_when: [system is static, feedback is negligible, relationship directions are unknown]
```