# Trade-Off Analysis

## Purpose
Systematically compare options across multiple dimensions to identify what must be sacrificed to gain more of something else, and eliminate options that are worse on all dimensions.

## When to Use
When choosing among options that differ along multiple dimensions of value. When you need to make the cost of a choice visible — what you give up by choosing A over B. When stakeholders disagree about which dimension matters most and you need to frame the conversation around trade-offs rather than absolutes. When you suspect some options are dominated (strictly worse than another option on all dimensions). When designing a system and you need to understand how architectural choices affect quality attributes.

## When Not to Use
When there is only one dimension of value (just compare the numbers). When all options are roughly equal and no meaningful trade-offs exist. When the dimensions are incommensurable in a way that makes comparison misleading — for example, comparing "lives saved" to "aesthetic quality." When the problem is best solved by formal optimization rather than structured comparison.

## Problem Signals
The problem description contains phrases like "on one hand... on the other hand," "we can't have both," "there's a tension between X and Y," "what are we giving up?" Options are being compared on multiple dimensions without a clear winner. Stakeholders are advocating for different options based on different criteria.

## Inputs
- **Options**: the candidate solutions or designs to compare
- **Dimensions**: the attributes or criteria along which options differ
- **Measurements**: how each option performs on each dimension (can be quantitative scores, qualitative ratings, or ordinal rankings)
- **Direction**: for each dimension, whether higher is better or lower is better

## Procedure
1. **List options**: enumerate all candidate solutions you are considering.
2. **Identify dimensions**: list every attribute that matters for the decision. Keep the list focused — 5 to 10 dimensions is typical. More than 15 suggests the dimensions are not independent.
3. **Score options**: evaluate each option on each dimension. Use consistent scales. Prefer quantitative measures where possible. For qualitative dimensions, use a consistent ordinal scale (e.g., 1-5) with explicit anchors.
4. **Identify dominated options**: an option is dominated if there exists another option that is at least as good on every dimension and strictly better on at least one. Eliminate dominated options from further consideration.
5. **Analyze trade-offs among non-dominated options**: for each pair of remaining options, identify what you gain and what you sacrifice by choosing one over the other. State trade-offs in concrete terms: "Option A improves latency by 30ms but costs $200/month more than Option B."
6. **Identify the efficient frontier**: the set of non-dominated options defines the trade-off surface.
7. **Apply weights** (if available): if relative importance of dimensions is known, apply multi-criteria decision methods to rank the non-dominated options.

## Output
A list of options with their scores on each dimension. A set of dominated options (eliminated). A set of non-dominated options forming the efficient frontier. For each pair of non-dominated options, an explicit trade-off statement. A recommendation if weights are available.

## Strengths
Makes trade-offs explicit and discussable. Eliminates options that are clearly worse, reducing the decision space. Does not require weights or a single objective function — works with multiple incommensurable dimensions. Supports stakeholder alignment by framing disagreements as differences in weights rather than differences in facts.

## Limitations
Requires dimensions to be comparable in a meaningful sense. The scoring process can introduce noise and bias. The analysis is only as good as the dimensions identified — missing an important dimension can lead to the wrong conclusion. The efficient frontier may still contain many options, requiring further narrowing.

## Common Failure Modes
Eliminating an option as "dominated" when it is actually better on a dimension that was not included in the analysis. Scoring options inconsistently — using different standards for different options. Treating ordinal scores as cardinal and performing arithmetic on them. Adding weights too early, before the trade-off structure is understood. Ignoring that some trade-offs are qualitatively different and cannot be compared on a common scale. Presenting the analysis as objective when the scores are subjective judgments.

## Verification
Check that every option classified as dominated is genuinely worse or equal on all dimensions. Confirm that the dimensions are independent — changing one does not automatically change another. Verify that the scoring is consistent across options. Test whether the conclusions change if a dimension is added or removed. Ask whether the analysis would change a stakeholder's mind — if not, it may not be surfacing real trade-offs.

## Combine With
- **multi-criteria-decision**: to rank non-dominated options when weights are available
- **multi-objective-optimization**: to generate the Pareto frontier for continuous design spaces
- **sensitivity-analysis**: to test how conclusions change when scores or weights vary
- **constraint-analysis**: to identify which constraints are driving the trade-offs

## Conflicts With
- **cost-benefit-analysis**: reduces all dimensions to a single monetary metric; trade-off analysis preserves multiple dimensions
- **constrained-optimization**: seeks a single optimum; trade-off analysis presents a menu of non-dominated options
- **satisficing**: stops at the first acceptable option; trade-off analysis compares all options

## Example
A team is choosing a database for a new service. Options: PostgreSQL, MongoDB, DynamoDB, CockroachDB. Dimensions: query flexibility, operational overhead, latency at scale, cost, ecosystem maturity. Scoring reveals that DynamoDB dominates MongoDB (better or equal on all dimensions). PostgreSQL and CockroachDB are non-dominated: PostgreSQL sacrifices horizontal scalability for query flexibility and ecosystem maturity; CockroachDB sacrifices ecosystem maturity for horizontal scalability. The trade-off is now framed as: "Do we value query flexibility more than seamless horizontal scaling?" The team can now have a focused discussion.

## Selection Metadata
```
id: trade-off-analysis
category: optimization
best_for: [conflicting objectives, design decisions, stakeholder negotiation, option comparison]
requires: [options, dimensions, measurements]
produces: [trade-off curves, dominated options, efficient frontier]
strengths: [clarifies choices, removes dominated options, supports stakeholder alignment]
limitations: [requires comparable dimensions, scoring noise, missing dimensions]
combine_with: [multi-criteria-decision, multi-objective-optimization, sensitivity-analysis, constraint-analysis]
avoid_when: [objectives are not comparable, single dimension of value, formal optimization is better]
```