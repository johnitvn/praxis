# Premortem

## Purpose
Use prospective hindsight to identify failure modes in a plan or decision by imagining it has already failed and working backward to explain why.

## When to Use
When a plan or decision has been developed and the team is confident it will succeed. When overconfidence may be masking real risks. Before committing to an irreversible or high-stakes course of action. When the plan has been developed by a cohesive group that may have fallen into groupthink. When traditional risk analysis feels too abstract or fails to surface unexpected failure modes. When you need to break the "plan continuation bias" — the tendency to stick with a plan despite warning signs.

## When Not to Use
When the plan is trivial or the cost of failure is negligible. When the team is already excessively pessimistic — a premortem may deepen paralysis. When the plan is so early-stage that it is not yet a concrete plan — the method works best on a specific, articulated plan. When the team is not psychologically safe enough to voice imagined failures without fear of being seen as negative.

## Problem Signals
The plan has unanimous support and nobody is raising concerns. The timeline is aggressive and everything must go right. The team is exhibiting overconfidence — "we've done this before," "it's straightforward." There is a history of similar projects failing in ways that are being dismissed as not applicable. The plan has many interdependent steps with no slack.

## Inputs
- **A concrete plan or decision**: the premortem requires a specific, articulated plan with clear steps, timeline, and assumptions
- **A facilitator**: someone to guide the process and ensure psychological safety
- **Participants**: the team that developed the plan, plus optionally outside perspectives

## Procedure
1. **Set the scene**: the facilitator announces: "Imagine we are [time period] in the future. The [plan/decision] has been implemented, and it has been a complete disaster. It failed spectacularly. We are now conducting a postmortem to understand what went wrong."
2. **Individual generation**: each participant independently writes down reasons for the failure. No discussion yet. This prevents anchoring on the first idea. Give 5-10 minutes.
3. **Collect and cluster**: the facilitator collects all failure reasons and groups them into themes. Do not evaluate or dismiss any reason at this stage.
4. **Discuss**: for each cluster, discuss the failure mechanism in detail. What would have to happen for this failure to occur? Is this plausible? What early warning signs would have appeared?
5. **Prioritize**: identify the most plausible and consequential failure modes. Focus on those that are not already covered by existing risk mitigations.
6. **Mitigate**: for each high-priority failure mode, design a mitigation or monitoring strategy. What can be done now to prevent this failure, or detect it early enough to respond?
7. **Update the plan**: incorporate the mitigations and early warning indicators into the plan.

## Output
A list of potential failure modes, generated through prospective hindsight. A prioritization of the most plausible and consequential failures. Mitigations and early warning indicators for each high-priority failure mode. An updated plan incorporating these mitigations.

## Strengths
Counters overconfidence and plan continuation bias effectively. The prospective hindsight framing ("it has already failed") unlocks creative thinking about failure modes that analytical methods miss. The individual generation phase prevents groupthink. Fast and low-cost to run — typically 30-60 minutes. Empirically validated to improve decision quality.

## Limitations
The quality of the output depends on the participants' imagination and domain knowledge — a team may fail to imagine the failure mode that actually occurs. Can generate many low-probability failure modes that create noise rather than insight. The method identifies potential failures but does not quantify their likelihood — it must be paired with risk analysis for prioritization. May be resisted by teams with a strong "can-do" culture that views negative thinking as unproductive.

## Common Failure Modes
Running the premortem as a group discussion from the start, losing the independent generation benefit. Dismissing generated failure modes as "unlikely" without examining the mechanism. Generating only generic failures ("we ran out of time," "the requirements changed") without specifying the concrete mechanism. Treating the premortem as a box-checking exercise and not updating the plan afterward. Running it once at the start and never revisiting as the plan evolves. The facilitator not protecting psychological safety, leading to self-censorship.

## Verification
Check that every high-priority failure mode has a corresponding mitigation or monitoring strategy in the updated plan. Verify that the failure modes are concrete and specific, not generic. Confirm that the plan actually changed as a result of the premortem — if nothing changed, the exercise was not taken seriously. Review whether the early warning indicators are observable and would actually trigger a response.

## Combine With
- **risk-analysis**: to quantify and prioritize the failure modes identified by the premortem
- **scenario-planning**: to explore how different futures could produce different failure modes
- **decision-under-uncertainty**: to incorporate failure mode awareness into the decision framework
- **fault-tree-analysis**: to decompose high-level failure modes into causal chains
- **self-critique**: to extend the critical mindset beyond the premortem session

## Conflicts With
- **optimism-bias**: the premortem is designed to counter optimism; it directly conflicts with the assumption that things will go well
- **expected-utility**: the premortem generates qualitative scenarios; expected utility requires probabilities

## Example
A team has planned a major API version migration. The plan: deprecate v1 endpoints, give clients 6 months notice, monitor v1 usage, flip the switch on the deadline. The premortem facilitator announces: "It's 3 months after the deadline. The migration is a disaster. Clients are angry. What happened?" Individual generation surfaces: a major client didn't see the deprecation notice because it went to an unmonitored email alias; the monitoring dashboard showed low v1 usage but it was from a critical internal service that wasn't on the migration list; a client's integration partner went out of business and they couldn't update their code. The team adds: direct outreach to top 10 clients by revenue, an allowlist for critical internal services, and a grace period with a rate-limit rather than a hard cutoff.

## Selection Metadata
```
id: premortem
category: risk
best_for: [plan validation, overconfidence reduction, decision quality, groupthink counter]
requires: [plan or decision, imagination, psychological safety]
produces: [failure modes, mitigations, early warning indicators, updated plan]
strengths: [counters overconfidence, unlocks creative failure thinking, fast and low-cost, empirically validated]
limitations: [imagination-limited, generates noise, does not quantify likelihood, requires psychological safety]
combine_with: [risk-analysis, scenario-planning, decision-under-uncertainty, fault-tree-analysis]
avoid_when: [plan is trivial, failure is inconsequential, team is already paralyzed by pessimism]
```