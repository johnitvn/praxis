# Fault Tree Analysis

## Purpose
Decompose a top-level undesired event (system failure, accident) into its contributing causes and their logical relationships, enabling quantitative or qualitative analysis of failure paths.

## When to Use
When analyzing how a specific system failure could occur. When the system has known component failure modes and you need to understand how they combine. When you need to quantify system reliability from component reliability data. When safety or reliability is critical and you must demonstrate that failure probabilities are acceptably low. When investigating a past failure and you need to trace it to root causes. When designing redundancy and you need to verify that no single point of failure exists.

## When Not to Use
When the system is so simple that the failure paths are obvious. When component failure modes are unknown and cannot be estimated. When the system involves human or organizational factors that are not well-modeled by logical gates — fault trees handle technical failures well but struggle with human error and organizational dysfunction. When the top event is vague or cannot be defined precisely.

## Problem Signals
The problem description mentions "how could this system fail," "what are the failure modes," "can we prove this system is safe enough," "what is the probability of a catastrophic failure?" The system has redundancy, safety mechanisms, or multiple layers of defense. A failure has occurred and the investigation needs to trace root causes. Regulatory standards require a formal safety analysis (e.g., aerospace, nuclear, medical devices).

## Inputs
- **Top event**: the undesired system-level failure being analyzed (must be specific and observable)
- **System knowledge**: understanding of system components, their failure modes, and their interactions
- **Failure data** (optional): component failure rates or probabilities
- **Boundary conditions**: what is considered "normal" operation — what external events are in scope

## Procedure
1. **Define the top event**: state the undesired outcome precisely. "Engine fails to start" not "engine problem." The top event must be an observable, specific condition.
2. **Identify immediate causes**: for the top event, ask: what events, singly or in combination, could directly cause this? These become the inputs to a logic gate directly below the top event.
3. **Choose the logical relationship**: for each set of immediate causes, determine whether they combine via AND (all must occur together) or OR (any one is sufficient). Draw the appropriate gate symbol.
4. **Decompose recursively**: for each intermediate event, repeat steps 2-3. Continue until you reach basic events — component failures, human errors, or external conditions that cannot be further decomposed.
5. **Check for completeness**: verify that every basic event is genuinely basic (cannot be decomposed further) and that the logical gates correctly capture the causal relationships.
6. **Analyze cut sets**: find the minimal cut sets — the smallest combinations of basic events that cause the top event. For an OR gate, each input is a cut set. For an AND gate, the combination of all inputs is a cut set. Minimal cut sets reveal single points of failure (single-event cut sets).
7. **Quantify** (optional): if failure rates are available for basic events, compute the probability of the top event. For OR gates, sum probabilities (approx.). For AND gates, multiply probabilities. Apply exact methods for dependent events.
8. **Identify mitigations**: for each minimal cut set, propose design changes or safeguards that break the failure path.

## Output
A fault tree diagram with the top event, intermediate events, logic gates, and basic events. A list of minimal cut sets. Identification of single points of failure. If quantified, the probability of the top event. Mitigation recommendations.

## Strengths
Systematic and exhaustive — the recursive decomposition forces consideration of all failure paths. The logical gate structure makes the analysis auditable and reviewable. Identifies single points of failure explicitly. Supports quantitative reliability analysis when component data is available. Industry standard in safety-critical domains with decades of validated use.

## Limitations
Combinatorial explosion: a moderately complex system can produce a very large tree. The quality of the analysis depends entirely on the completeness of the decomposition — missing a failure mode can produce a falsely reassuring result. Human error and organizational factors are hard to model with logical gates. Assumes events are independent unless explicitly modeled otherwise, which is often false. Requires significant domain expertise to identify all failure modes.

## Common Failure Modes
Stopping decomposition too early, treating complex events as basic events. Missing common-cause failures — a single event that defeats multiple branches of the tree (e.g., a power failure that disables both the primary system and the backup). Using AND gates where events are actually correlated, underestimating the top event probability. Building a beautiful tree that captures 80% of failure modes and declaring success. Confusing the fault tree (how failures cause the top event) with an event tree (how the top event propagates to consequences). Assuming independence without checking.

## Verification
Check that every basic event is genuinely basic — no further decomposition is possible. Verify that logic gates correctly represent the causal relationships. Confirm that common-cause failures have been considered and modeled. Test whether the fault tree would have predicted a known past failure. Review the minimal cut sets for plausibility — if a cut set seems implausible, the tree may have a logic error.

## Combine With
- **risk-analysis**: to integrate fault tree results into a broader risk assessment
- **causal-reasoning**: to ensure the causal logic in the tree is sound
- **reliability-analysis**: to extend the quantitative analysis to system-level reliability metrics
- **root-cause-analysis** (pattern): to apply fault tree thinking to past incidents
- **premortem**: to generate failure modes that the analytic decomposition might miss

## Conflicts With
- **systems-thinking**: fault trees decompose; systems thinking emphasizes emergent behavior that is not reducible to component failures
- **inductive-reasoning**: fault tree analysis is deductive (top-down); inductive methods like FMEA work bottom-up
- **satisficing**: fault tree analysis is exhaustive; satisficing stops at adequate

## Example
A team is analyzing the reliability of a critical database service. Top event: "Database becomes unavailable for more than 5 minutes." Immediate causes: (1) Database process crashes AND automatic failover fails, OR (2) Network partition isolates the database, OR (3) Disk failure AND backup restoration takes over 5 minutes. Decomposing "automatic failover fails": the failover script has a bug OR the monitoring system doesn't detect the crash OR the standby node is not in sync. Minimal cut sets reveal a single point of failure: the monitoring system runs on the same host as the database. Mitigation: move monitoring to a separate host. After quantification with component failure rates, the top event probability is 0.001/year — acceptable for the service tier.

## Selection Metadata
```
id: fault-tree-analysis
category: risk
best_for: [reliability engineering, safety analysis, failure investigation, single-point-of-failure detection]
requires: [top event, component failure modes, logical relationships]
produces: [fault tree diagram, minimal cut sets, failure paths, top event probability]
strengths: [systematic, exhaustive, auditable, identifies single points of failure, quantitative]
limitations: [combinatorial explosion, completeness-dependent, struggles with human factors, independence assumption]
combine_with: [risk-analysis, causal-reasoning, premortem, root-cause-analysis]
avoid_when: [failure modes are unknown, system is simple, human factors dominate]
```