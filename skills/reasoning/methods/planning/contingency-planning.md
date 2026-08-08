# Contingency Planning

## Purpose
Identify plausible disruptions to a base plan and prepare pre-defined responses so that when a disruption occurs, the response is ready rather than improvised. This method builds resilience by converting surprises into known branches.

## When to Use
- When the environment contains significant uncertainty that cannot be reduced by further analysis
- When the cost of disruption is high and the cost of preparing a contingency is low
- When response time matters — the disruption must be handled quickly and there is no time to plan from scratch
- When the base plan has identifiable single points of failure or critical assumptions

## When Not to Use
- When the environment is stable and disruptions are predictable enough to handle in the base plan
- When the cost of preparing contingencies exceeds the expected cost of disruption
- When the number of possible disruptions is so large that contingency planning becomes unbounded (use scenario-planning instead)
- When the base plan itself is not yet defined — contingency planning requires a baseline to deviate from

## Problem Signals
- The user describes a plan and then asks "what if X happens?" or "what could go wrong?"
- The plan involves dependencies on external systems, people, or events beyond the planner's control
- The language includes "assuming," "hoping," or "expecting" for critical path items
- The user describes a high-stakes plan where failure is not an option

## Inputs
- A base plan with identifiable steps, dependencies, and assumptions
- A list of candidate disruptions, each with a trigger condition and estimated impact
- Criteria for which disruptions are worth planning for (probability threshold, impact threshold, or both)

## Procedure
1. **Map the base plan.** List every step, dependency, and critical assumption. Pay special attention to external dependencies (vendors, APIs, people) and assumptions (the server will be available, the budget will be approved).
2. **Generate disruption candidates.** For each step and dependency, ask: what if this fails? What if it takes twice as long? What if the output is wrong? Use the premortem method (from the risk category) to generate a richer set of candidates.
3. **Filter by impact and plausibility.** Score each candidate on two dimensions: likelihood of occurrence and severity of impact. Focus on high-impact disruptions regardless of likelihood; for low-impact disruptions, only include them if they are highly likely.
4. **Define trigger conditions.** For each selected disruption, specify the observable signal that indicates it has occurred. A trigger must be unambiguous and detectable early enough to act.
5. **Design the contingency response.** For each disruption, define: what action to take, who or what executes it, what resources it requires, and how long it takes to execute. The response should aim to restore the plan to a viable path, not necessarily to the original path.
6. **Assess resource overlap.** Check whether multiple contingencies compete for the same resources. If two contingencies both require the same reserve capacity, the plan is not truly resilient.
7. **Integrate into the base plan.** Add monitoring for trigger conditions. Pre-allocate resources for contingency responses. Document contingency responses alongside the base plan so they are accessible when needed.

## Output
- A prioritized list of disruption scenarios with trigger conditions and response plans
- Resource reservations for contingency responses
- Monitoring points embedded in the base plan
- A residual risk register for disruptions that were considered but not planned for

## Strengths
- Reduces response time during disruptions from hours/days to minutes
- Makes the plan's assumptions explicit and testable
- Provides psychological readiness: the team knows what to do when things go wrong
- Can be combined with the base plan's execution without adding decision-making overhead

## Limitations
- Cannot cover every possible disruption — there will always be unplanned surprises
- Contingency plans must be maintained as the base plan evolves, creating a maintenance burden
- Over-planning can create a false sense of security if the contingencies are not tested
- The most damaging disruptions are often the ones nobody thought of (unknown unknowns)

## Common Failure Modes
- **Contingency theater**: creating contingency plans that are too vague to be actionable ("if the server goes down, we will fix it"), providing comfort without resilience
- **Trigger ambiguity**: defining triggers that are subjective ("if performance is bad") rather than measurable ("if response time exceeds 500ms for 5 minutes"), leading to delayed responses
- **Resource double-counting**: assuming the same reserve resources can handle multiple simultaneous contingencies
- **Contingency drift**: the base plan evolves but the contingency plans are not updated, so they reference steps that no longer exist
- **Implausible filtering**: dismissing high-impact disruptions as "unlikely" without rigorous probability assessment

## Verification
- Does every contingency have a specific, measurable trigger condition?
- Has each contingency response been resourced (people, time, budget)?
- Are the trigger monitoring points integrated into the base plan's execution?
- Would the contingency responses still work if the base plan has changed since they were written?

## Combine With
- premortem (from risk category) for generating disruption candidates
- scenario-planning (from strategic category) for environments with too many disruptions to plan individually
- risk-analysis (from risk category) for prioritizing disruptions by impact and likelihood
- hierarchical-planning for adding contingencies at each level of the plan tree

## Conflicts With
- Methods that assume a single deterministic path through the plan
- Over-optimization: a highly optimized plan often has no slack for contingencies

## Example
**Base plan**: Deploy a new payment service to production on Friday at 10:00.

**Disruption candidates and responses**:
1. *Disruption*: deployment fails with an unrecoverable error. *Trigger*: deployment pipeline returns a non-zero exit code after 3 retries. *Response*: roll back to the previous version using the automated rollback script. Notify the on-call engineer. Reschedule deployment for Monday.
2. *Disruption*: payment service is live but processes charges incorrectly. *Trigger*: monitoring detects error rate > 1% or charge amount mismatch in reconciliation. *Response*: immediately disable the payment endpoint via feature flag. Route traffic to the fallback payment processor. Investigate with the reconciliation log.
3. *Disruption*: third-party payment gateway is unreachable. *Trigger*: health check to the gateway returns 5xx for 30 seconds. *Response*: queue payment requests locally. Display a "payment processing delayed" message to users. Retry the gateway every 30 seconds. If down for more than 15 minutes, escalate to the gateway vendor.

**Resource overlap check**: The fallback payment processor (contingency 2) and the local queue (contingency 3) both require database capacity. Ensure the database has enough headroom to handle both simultaneously.

## Selection Metadata
```
id: contingency-planning
category: planning
best_for: [uncertain environments, high-stakes plans, resilience]
requires: [base plan, possible disruptions]
produces: [contingency plans]
strengths: [robust to disruptions, prepared for surprises]
limitations: [cannot cover everything, maintenance burden]
combine_with: [scenario-planning, risk-analysis]
avoid_when: [environment is stable, disruptions are predictable]
```