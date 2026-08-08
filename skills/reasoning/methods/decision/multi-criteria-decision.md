# Multi-Criteria Decision

## Purpose
Evaluate and rank options across multiple, potentially conflicting objectives by making trade-offs explicit and transparent. This method structures preference judgments so that stakeholders can see how different criteria weights lead to different recommendations.

## When to Use
- When options must be compared across multiple dimensions that cannot be reduced to a single metric (e.g., cost, quality, speed, environmental impact)
- When stakeholders disagree about the relative importance of different criteria
- When the decision must be transparent and defensible to parties who were not involved in making it
- When you need to document the rationale for choosing one option over others
- When the number of options is manageable (typically 5-20) and the number of criteria is tractable (3-15)

## When Not to Use
- When a single criterion clearly dominates and the others are irrelevant (use simpler comparison)
- When options are indistinguishable on all criteria (the analysis will produce noise, not signal)
- When criteria are so interdependent that scoring them independently is misleading (use systems-thinking or trade-off-analysis)
- When you lack the domain knowledge to score options on the criteria (scoring with no evidence produces false precision)
- When the decision is purely about risk under uncertainty (use expected-utility or decision-under-uncertainty)

## Problem Signals
- The user presents a table of options with multiple attributes or "factors to consider"
- The user says "it depends" or "there are trade-offs" when asked about a decision
- The user describes stakeholders who disagree about what matters most
- The problem involves vendor selection, technology choice, hiring, or site selection
- The user asks for a "structured way to compare" or "a framework to make this decision"

## Inputs
- A set of options (alternatives, candidates, choices)
- A set of criteria (objectives, attributes, dimensions) on which options will be evaluated
- Weighting of criteria: either elicited from the decision maker or explored parametrically
- Scores for each option on each criterion: either quantitative (measurements) or qualitative (assessments)
- Decision context: who the decision maker is and what constraints apply

## Procedure
1. Define the decision frame: what is being decided, by whom, and with what constraints.
2. Identify the options. Ensure the set is complete and includes a "do nothing" or "status quo" option where appropriate.
3. Elicit criteria from the decision maker. Use open-ended questions first, then prompt for completeness. Criteria should be independent, measurable, and non-redundant.
4. Structure the criteria into a hierarchy if needed (e.g., "performance" with sub-criteria "latency" and "throughput").
5. Assign weights to criteria. Use one of: direct rating ("cost is twice as important as speed"), swing weighting (how much would you give up on criterion A to go from worst to best on criterion B?), or pairwise comparison (AHP). Document the method used.
6. Score each option on each criterion. Use a consistent scale across options. For quantitative criteria, define a value function mapping measurements to scores. For qualitative criteria, use a defined ordinal scale with clear anchor descriptions.
7. Compute weighted scores: for each option, sum over criteria of (weight * score).
8. Rank options by total weighted score.
9. Perform sensitivity analysis: vary the weights of the most contested criteria. If the ranking changes, flag the decision as sensitive.
10. Report the ranking, the sensitivity analysis, and the key trade-offs that drive the result.

## Output
- A ranked list of options with weighted scores
- A sensitivity analysis showing which weight changes alter the ranking
- Identification of the key trade-offs: which criteria are in conflict and which options represent different trade-off profiles
- A clear record of the criteria, weights, scores, and rationale for each

## Strengths
- Transparent: every step is documented and can be audited by stakeholders
- Handles multiple incommensurable objectives without forcing them into a single metric
- Supports stakeholder alignment by making disagreements about weights explicit
- Sensitivity analysis reveals whether the decision is robust or fragile
- Widely used and understood in procurement, policy, and engineering contexts

## Limitations
- Weight elicitation is cognitively demanding and prone to anchoring and framing effects
- Criteria independence is assumed but often violated; interactions between criteria are ignored
- The additive model assumes full compensation: a very bad score on one criterion can be perfectly offset by good scores on others, which may not reflect real preferences
- Scores on qualitative criteria are subjective and may embed unrecognized biases
- The structure can create an illusion of objectivity that masks the subjectivity of the inputs

## Common Failure Modes
- Including criteria that are not independent, double-counting the same underlying concern
- Using equal weights as a default without justification, which is itself a strong normative claim
- Scoring options without evidence, treating the analyst's intuition as data
- Failing to perform sensitivity analysis, treating the initial ranking as definitive
- Criteria proliferation: including every possible concern, diluting the ones that actually matter
- Anchoring the scores on the first option evaluated, then rating others relative to it

## Verification
- Check that criteria are mutually independent: can you score an option on one criterion without knowing its score on another?
- Verify that the scale direction is consistent (higher is always better, or clearly documented)
- Test whether the top-ranked option changes when the weight of any single criterion is varied across its plausible range
- Confirm that the score differences between adjacent options are larger than the scoring precision
- Review the "do nothing" option: if it ranks highly, the decision may not be worth making

## Combine With
- sensitivity-analysis: essential for testing weight robustness
- trade-off-analysis: to understand the shape of the trade-off between conflicting criteria
- evidence-evaluation: when scoring options requires assessing evidence quality
- dialectic: when stakeholders disagree about criteria weights and need structured debate

## Conflicts With
- expected-utility: MCDA preserves multiple dimensions; expected utility collapses to one
- satisficing: MCDA seeks a complete ranking; satisficing stops at the first adequate option
- constrained-optimization: MCDA compares given options; optimization searches the continuous space

## Example
A company is selecting a cloud provider among AWS, GCP, and Azure. They identify five criteria: cost (weight 30), reliability (weight 25), compliance support (weight 20), ecosystem fit (weight 15), and migration effort (weight 10). They score each provider on a 0-100 scale for each criterion using documented evidence. The weighted scores produce a ranking. Sensitivity analysis reveals that if cost weight drops below 20 (and reliability proportionally increases), the ranking changes. This finding is reported to the VP, who must decide whether the 30% cost weight reflects genuine organizational priority or anchoring on the most easily quantified criterion.

## Selection Metadata
```
id: multi-criteria-decision
category: decision
best_for: [multiple-objectives, trade-offs, stakeholder-alignment]
requires: [options, criteria, weights]
produces: [ranked-options, sensitivity-analysis, key-trade-offs]
strengths: [transparent, handles-multiple-objectives, auditable]
limitations: [weight-elicitation, criteria-interaction-blind, additive-compensation-assumption]
combine_with: [sensitivity-analysis, trade-off-analysis, evidence-evaluation, dialectic]
avoid_when: [single-criterion-dominates, criteria-are-incommensurable, scoring-without-evidence]
```