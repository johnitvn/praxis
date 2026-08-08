# Risk Analysis

## Purpose
Identify, assess, and prioritize potential adverse events by evaluating their likelihood and impact, producing a structured basis for mitigation decisions.

## When to Use
When a decision, project, or system faces uncertain outcomes with downside consequences. When you need to decide where to allocate limited mitigation resources. When stakeholders require a structured justification for risk-related decisions. When comparing the risk profiles of different options. When regulatory or safety standards require formal risk documentation. When the cost of failure is high and you need to understand the risk landscape before committing.

## When Not to Use
When risks are already well-known and understood — no new analysis is needed. When the stakes are negligible and the cost of analysis exceeds the cost of any plausible failure. When the uncertainty is so deep that neither likelihood nor impact can be estimated (use scenario-planning or decision-under-uncertainty instead). When the only question is "will this specific thing happen?" — that is a forecasting question, not a risk analysis question.

## Problem Signals
The problem description mentions "what could go wrong," "how risky is this," "we need to prioritize our security/reliability investments," "what are the top risks?" Multiple stakeholders have different intuitions about what the biggest risks are. A decision is being made with significant downside uncertainty.

## Inputs
- **Scope**: the system, project, or decision being analyzed
- **Threats or hazards**: what could go wrong
- **Vulnerabilities or exposures**: what makes the system susceptible
- **Impact estimates**: what happens if the threat materializes (severity, cost, consequence)
- **Likelihood estimates**: how probable each threat is (can be qualitative or quantitative)

## Procedure
1. **Define scope**: establish the boundary of the analysis. What system, decision, or time horizon is being analyzed?
2. **Identify risks**: systematically generate a list of potential adverse events. Use structured techniques: checklists, brainstorming, historical data, expert elicitation, or threat modeling outputs. Do not filter or prioritize at this stage.
3. **Assess likelihood**: for each risk, estimate the probability or frequency of occurrence. Use historical data where available, expert judgment where not. Be explicit about uncertainty in these estimates.
4. **Assess impact**: for each risk, estimate the consequence if it materializes. Consider multiple impact dimensions: financial, operational, reputational, safety, regulatory.
5. **Prioritize**: combine likelihood and impact into a risk rating. The standard tool is a risk matrix (5x5 grid mapping likelihood against impact). Identify risks in the "high" zone that require immediate action.
6. **Identify mitigations**: for each high-priority risk, propose actions that reduce likelihood, reduce impact, or transfer the risk.
7. **Evaluate residual risk**: after mitigations are applied, reassess likelihood and impact. Confirm that residual risk is acceptable.

## Output
A risk register listing each risk with its likelihood, impact, and priority rating. A risk matrix showing the distribution of risks. A prioritized list of risks requiring mitigation. Mitigation recommendations with residual risk assessments.

## Strengths
Structured and systematic approach to an inherently messy problem. Produces a prioritized list that guides resource allocation. The risk matrix is widely understood and communicates effectively to stakeholders. Separates identification from assessment, reducing premature filtering.

## Limitations
Cannot identify unknown unknowns — risks you did not think to list. Likelihood and impact estimates are often subjective and subject to cognitive biases (overconfidence, availability bias, anchoring). The risk matrix can create an illusion of precision. Interdependent risks are hard to capture — two medium risks may combine to produce a catastrophic outcome. The analysis is a snapshot and degrades as conditions change.

## Common Failure Modes
Filling the risk matrix with generic risks that could apply to any project, producing a document that nobody acts on. Estimating likelihood and impact without evidence, anchoring on recent events or vivid examples. Treating the risk matrix as the end product rather than the risk mitigations. Ignoring risks that fall in the "medium" zone even when they are highly correlated. Confusing risk analysis with risk management — analysis identifies risks; management does something about them. Not updating the analysis as new information emerges.

## Verification
Check that every high-priority risk has a corresponding mitigation. Verify that likelihood and impact estimates are based on evidence, not intuition alone. Confirm that the risk register covers the full scope — no major category of risk is missing. Test whether the analysis would have identified a known past failure in a similar system. Review whether residual risks are genuinely acceptable to stakeholders.

## Combine With
- **uncertainty-quantification**: to produce calibrated likelihood and impact estimates
- **decision-under-uncertainty**: when the risk analysis feeds into a decision among options
- **premortem**: to generate risks that might be missed by analytical methods
- **fault-tree-analysis**: to decompose top-level risks into component failure paths
- **scenario-planning**: to explore how risks interact under different futures

## Conflicts With
- **expected-utility**: risk analysis typically uses qualitative ratings; expected utility requires precise probabilities and utilities
- **optimism-bias**: the analytical framing of risk analysis can suppress the imaginative "what if" thinking that premortem provides

## Example
A team is planning a database migration from on-premises to cloud. The risk analysis identifies 12 risks: data corruption during transfer (high likelihood, critical impact), extended downtime (medium likelihood, high impact), schema incompatibility (medium likelihood, medium impact), credential exposure (low likelihood, critical impact), and 8 others. The risk matrix places data corruption in the top-right (high-high) zone. Mitigation: run migration in parallel, validate checksums, maintain rollback capability. After mitigation, data corruption residual risk drops to low likelihood, medium impact — acceptable to proceed.

## Selection Metadata
```
id: risk-analysis
category: risk
best_for: [uncertain outcomes, safety-critical decisions, investment decisions, resource allocation for mitigation]
requires: [threats, vulnerabilities, impacts, likelihood estimates]
produces: [risk matrix, risk priorities, mitigation recommendations, residual risk assessment]
strengths: [structured, prioritizes, communicates effectively, guides resource allocation]
limitations: [unknown unknowns, subjective estimates, illusion of precision, static snapshot]
combine_with: [uncertainty-quantification, decision-under-uncertainty, premortem, fault-tree-analysis, scenario-planning]
avoid_when: [risks are well-known, stakes are negligible, uncertainty is too deep for estimation]
```