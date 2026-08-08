# Cost-Benefit Analysis

## Purpose
Determine whether an action, project, or policy is worth undertaking by comparing its total expected costs against its total expected benefits, both expressed in comparable (typically monetary) units over a defined time horizon. The method produces a net present value and benefit-cost ratio that support go/no-go and resource allocation decisions.

## When to Use
- When deciding whether to invest in a project, policy, or initiative with quantifiable costs and benefits
- When comparing multiple investment options that compete for a limited budget
- When the decision requires a clear, defensible economic justification for stakeholders
- When benefits and costs accrue over time and need to be discounted to present value
- When the decision is primarily about resource allocation and efficiency

## When Not to Use
- When key costs or benefits are fundamentally unquantifiable in monetary terms (human dignity, biodiversity, cultural heritage)
- When distributional effects matter more than total net benefit (who gains and who loses, not just by how much)
- When the decision involves ethical constraints that override efficiency considerations (use multi-criteria-decision)
- When uncertainty is so deep that costs and benefits cannot be estimated even within orders of magnitude (use decision-under-uncertainty)
- When the project is trivial and the cost of analysis exceeds the stakes

## Problem Signals
- The user asks "is this worth doing" or "what's the ROI" of a project or policy
- The problem involves a budget allocation decision across competing projects
- The user describes quantifiable costs (dollars, hours, resources) and quantifiable benefits (revenue, time saved, risk reduced)
- The decision involves a regulatory requirement to demonstrate that benefits justify costs
- The user needs to build a business case or funding proposal

## Inputs
- A clear definition of the project, policy, or action being evaluated
- A baseline or counterfactual: what happens if the action is not taken
- Cost estimates: one-time costs, recurring costs, opportunity costs, and externalities
- Benefit estimates: direct benefits, indirect benefits, and positive externalities
- Time horizon: over what period will costs and benefits accrue
- Discount rate: the rate at which future costs and benefits are converted to present value
- Optionally, a range or distribution for each cost and benefit estimate to support sensitivity analysis

## Procedure
1. Define the scope: what is included, what is excluded, and what is the counterfactual (the "without project" scenario).
2. Identify all relevant costs. Include direct costs (materials, labor, capital), indirect costs (overhead, training, disruption), opportunity costs (what is foregone), and negative externalities (costs borne by third parties). Be explicit about costs that are excluded and why.
3. Identify all relevant benefits. Include direct benefits (revenue, cost savings, productivity gains), indirect benefits (network effects, learning, reputation), and positive externalities. Be explicit about benefits that are excluded.
4. Assign monetary values to each cost and benefit. Where market prices exist, use them. Where they do not, use revealed preference methods (what people pay for related goods), stated preference methods (contingent valuation), or shadow pricing. Document the valuation method for each item.
5. Define the time horizon. It should be long enough to capture all material costs and benefits but not so long that discounting renders distant values negligible.
6. Select a discount rate. For private investments, use the cost of capital. For public projects, use the social discount rate (typically 2-7%). Justify the choice. Consider using a declining discount rate for very long time horizons.
7. Compute the net present value (NPV): sum over all time periods of (benefits_t - costs_t) / (1 + discount_rate)^t.
8. Compute the benefit-cost ratio (BCR): total discounted benefits / total discounted costs. A BCR > 1 indicates benefits exceed costs.
9. Perform sensitivity analysis: vary the discount rate, the most uncertain cost estimates, and the most uncertain benefit estimates. Report the range of NPV and BCR.
10. If the analysis is sensitive to a particular assumption, flag it. If the NPV changes sign within the plausible range, the decision is not robust.

## Output
- Net present value (NPV) and benefit-cost ratio (BCR)
- A breakdown of costs and benefits by category and time period
- Sensitivity analysis: which parameters drive the result and under what conditions the recommendation changes
- A clear statement of which costs and benefits were excluded and why
- A recommendation: go, no-go, or gather more information

## Strengths
- Provides a quantitative, comparable metric for resource allocation decisions
- Forces explicit consideration of all costs and benefits, reducing the risk of selective attention
- Widely understood and accepted in business, government, and policy contexts
- Sensitivity analysis reveals which assumptions drive the result
- Supports comparison across fundamentally different types of projects

## Limitations
- Monetization of non-market goods is contentious and can produce wildly varying estimates
- The choice of discount rate is often decisive and is inherently normative, not technical
- Distributional effects are invisible: a project with positive net benefit that enriches the wealthy and harms the poor passes the test
- Cannot capture irreversible or catastrophic outcomes that are hard to monetize
- The analysis is only as good as the estimates; garbage in, garbage out
- Tends to favor projects with quantifiable, near-term benefits over those with diffuse, long-term benefits

## Common Failure Modes
- Omitting significant costs or benefits because they are hard to quantify, implicitly assigning them a value of zero
- Double-counting benefits that appear under multiple labels
- Using an arbitrary discount rate without justification, or using zero discount rate (which treats all future values as equally important)
- Treating the NPV point estimate as the answer without sensitivity analysis
- Cherry-picking the valuation method that produces the desired result
- Ignoring the counterfactual: what would happen without the project is not "nothing," it is the status quo trajectory
- Confusing financial costs (private) with economic costs (social) when the analysis is meant to inform public policy

## Verification
- Check that the counterfactual is explicitly defined and plausible
- Verify that no major cost or benefit category has been omitted (ask: what would an opponent of this project point to?)
- Test whether the recommendation changes under a plausible range of discount rates
- Confirm that the time horizon is long enough to capture all material effects
- Review the valuation methods for the most uncertain items: are they defensible?
- Check for double-counting: does the same benefit appear under two different names?

## Combine With
- sensitivity-analysis: essential for testing the robustness of the NPV and BCR
- risk-analysis: when costs or benefits are uncertain and their distribution matters
- scenario-planning: when the future context could make the project much more or less valuable
- multi-criteria-decision: when some costs and benefits cannot be monetized and must be evaluated alongside the NPV
- expected-utility: when the decision maker is not risk-neutral and the NPV analysis should account for risk preferences

## Conflicts With
- multi-criteria-decision: CBA reduces everything to money; MCDA preserves multiple dimensions
- decision-under-uncertainty: CBA requires estimates; uncertainty methods work without them
- satisficing: CBA seeks the optimal; satisficing stops at adequate

## Example
A city is considering building a new public transit line. Costs include construction ($2B), annual operating costs ($50M/year), and disruption during construction (estimated $100M in lost business). Benefits include reduced travel time (valued at $150M/year using wage rates), reduced emissions (valued at $30M/year using the social cost of carbon), reduced traffic accidents (valued at $20M/year), and increased property values near stations (estimated $500M one-time). Using a 30-year horizon and a 4% social discount rate, the NPV is $450M and the BCR is 1.3. Sensitivity analysis shows that if the discount rate exceeds 5.5% or if construction costs exceed $2.5B, the NPV becomes negative. The analysis also notes that the property value increase is a transfer (not a net social benefit) and should be excluded from the primary analysis. The recommendation is to proceed, contingent on cost controls.

## Selection Metadata
```
id: cost-benefit-analysis
category: decision
best_for: [resource-allocation, policy-evaluation, go-no-go-decisions]
requires: [costs, benefits, time-horizon, discount-rate]
produces: [net-present-value, benefit-cost-ratio, sensitivity-findings]
strengths: [quantitative, comparable-across-options, widely-understood]
limitations: [monetization-difficulties, distributional-blindness, discount-rate-dependence]
combine_with: [sensitivity-analysis, risk-analysis, scenario-planning, multi-criteria-decision]
avoid_when: [costs-benefits-are-unquantifiable, distributional-effects-matter, ethical-constraints-override-efficiency]
```