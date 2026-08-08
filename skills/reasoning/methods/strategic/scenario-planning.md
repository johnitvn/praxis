# Scenario Planning

## Purpose
Generate a set of distinct, plausible futures to test the robustness of strategies, surface hidden assumptions, and prepare for a range of possible environments. Unlike forecasting, which predicts a single future, scenario planning creates multiple divergent futures and asks: what would we do if this happened?

## When to Use
- When the planning horizon is long (5+ years) and the future is too uncertain for a single-point forecast
- When the environment is shaped by forces you cannot control: technology shifts, regulatory changes, geopolitical events, demographic trends
- When you need to challenge organizational assumptions and broaden the range of possibilities considered
- When you are making a strategy that must be robust across fundamentally different possible worlds
- When you have identified key uncertainties that would dramatically change the value of different strategies

## When Not to Use
- When the future is predictable enough that a single forecast with confidence intervals is sufficient
- When the planning horizon is short and the environment is stable
- When you lack the ability to act on the insights (scenario planning without action is entertainment)
- When the number of uncertainties is so large that the scenario space explodes combinatorially (use decision-under-uncertainty)
- When the organization needs a single prediction to align around, not multiple possibilities

## Problem Signals
- The user says "we need to plan for the next 5-10 years" or "the future is highly uncertain"
- The problem involves long-term investments, R&D portfolio decisions, or strategic positioning
- The user describes "wild cards" or "black swans" that could reshape the industry
- The user's current plan assumes a single future (typically an extrapolation of the present)
- The user is debating strategies that would be brilliant in one future and disastrous in another

## Inputs
- A focal question or decision: what are we planning for?
- A time horizon: how far into the future are we looking?
- Key driving forces: trends and factors that will shape the future environment (demographics, technology, regulation, economics, social values, environment)
- Key uncertainties: driving forces whose future direction is unknown and whose impact is high
- Current assumptions about the future that are embedded in the organization's strategy
- Stakeholder perspectives: whose view of the future matters?

## Procedure
1. Define the focal question or decision. Be specific: "Should we invest in electric vehicle manufacturing?" not "What will the automotive industry look like?"
2. Set the time horizon. It should be long enough that the future is genuinely uncertain but short enough that the scenarios are actionable. For most strategic decisions, 5-15 years.
3. Identify driving forces using a PESTEL framework (Political, Economic, Social, Technological, Environmental, Legal). For each force, note whether it is a trend (direction is reasonably clear) or an uncertainty (direction is unknown).
4. Identify the two or three most critical uncertainties: the ones with the highest impact on the focal question and the highest uncertainty about their direction. These will be the axes along which scenarios diverge.
5. Construct a 2x2 scenario matrix (if using two critical uncertainties) or a small set of scenario narratives (if using three or more). Each scenario should be:
   - Plausible: it could happen, even if it is not the most likely future
   - Distinct: it differs from the other scenarios in meaningful ways
   - Relevant: it has clear implications for the focal decision
   - Challenging: it forces the organization to question its assumptions
   - Internally consistent: the elements within the scenario fit together logically
6. Develop each scenario into a narrative. Give it a memorable name. Describe the path from the present to that future: what events and decisions lead there? What does the world look like in that scenario? Who are the winners and losers?
7. Test current strategies against each scenario. For each strategy-scenario pair, ask: how would this strategy perform? What would we need to change? What early warning signs would tell us this scenario is unfolding?
8. Identify robust strategies: actions that perform well across multiple scenarios. Identify contingent strategies: actions that are excellent in one scenario but disastrous in another (these are options, not commitments).
9. Identify early indicators: what signals would suggest that a particular scenario is becoming more likely? What should we monitor?
10. Develop an action plan: what robust strategies should we pursue now? What contingent strategies should we prepare but not yet execute? What indicators should trigger a strategy shift?

## Output
- A set of 3-5 distinct, named scenarios with narratives
- A scenario matrix showing the critical uncertainties and how they combine
- An assessment of current strategy robustness across scenarios
- A list of robust strategies (good in most scenarios) and contingent strategies (good in specific scenarios)
- Early warning indicators for each scenario
- An action plan: what to do now, what to prepare, and what to monitor

## Strengths
- Challenges the implicit assumption that the future will resemble the present
- Broadens the range of possibilities considered, reducing the risk of surprise
- Makes assumptions explicit and testable
- Identifies strategies that are robust across fundamentally different futures
- Creates a shared language and framework for discussing uncertainty
- Does not require probability estimates, making it applicable in deep uncertainty

## Limitations
- Scenario quality depends entirely on the identification of the right critical uncertainties; miss one and the scenarios are blind
- The 2x2 matrix can oversimplify, reducing complex futures to four cells
- Scenarios can be vivid but wrong, creating a false sense of preparedness
- Organizations may treat the most comfortable scenario as the prediction and ignore the others
- Scenario planning is time-consuming and requires significant organizational buy-in to be effective
- Does not tell you which scenario is most likely; it is not a forecasting tool

## Common Failure Modes
- Generating scenarios that are all variations on the same theme (the "official future" with minor tweaks)
- Using the 2x2 matrix mechanically without verifying that the chosen axes are the most critical uncertainties
- Creating scenarios that are interesting but not actionable for the focal decision
- Treating the scenario exercise as a one-time event rather than an ongoing monitoring and updating process
- Anchoring on the scenario that feels most plausible and ignoring the others in subsequent decisions
- Generating too many scenarios, making the analysis overwhelming and unactionable
- Failing to identify early warning indicators, so the scenarios cannot inform real-time decisions

## Verification
- Check that each scenario is internally consistent: do the elements within the scenario fit together logically?
- Verify that the scenarios are distinct: could a reasonable person confuse two of them?
- Test that each scenario has clear, specific implications for the focal decision
- Confirm that the critical uncertainties are genuinely uncertain (not just things you wish were different)
- Review the current strategy against each scenario: does it fail in any scenario? If so, is that an acceptable risk?
- Validate that early warning indicators are observable and would actually trigger a response

## Combine With
- decision-under-uncertainty: use scenarios as the states of the world in a payoff matrix
- strategic-analysis: to understand the current competitive position before testing it against futures
- option-reasoning: to value the flexibility to switch strategies as scenarios unfold
- premortem: to identify failure modes within each scenario
- game-theoretic-analysis: to model how competitors would respond within each scenario
- risk-analysis: to assess the severity of bad outcomes in adverse scenarios

## Conflicts With
- forecasting methods: scenario planning deliberately avoids predicting a single future
- expected-utility: requires probabilities; scenario planning treats scenarios as equally worthy of preparation
- constrained-optimization: assumes a single objective function; scenarios require multiple evaluations

## Example
An energy company is deciding its 15-year investment portfolio. The focal question: what mix of renewable and fossil fuel assets should we build? They identify two critical uncertainties: (1) the speed of carbon regulation (fast vs. slow) and (2) the rate of renewable cost decline (rapid vs. gradual). The 2x2 matrix produces four scenarios: "Green Revolution" (fast regulation, rapid cost decline), "Regulatory Push" (fast regulation, gradual cost decline), "Market Transition" (slow regulation, rapid cost decline), and "Fossil Persistence" (slow regulation, gradual cost decline). Current strategy (heavy fossil investment) performs well only in Fossil Persistence. Robust strategies include investing in grid infrastructure (valuable in all scenarios) and building expertise in carbon capture (valuable in regulatory scenarios). Contingent strategies include a major renewable buildout (triggered by early indicators of rapid cost decline). The company decides to shift 30% of capex to robust investments, prepare contingent plans for the remaining 70%, and monitor renewable cost curves and regulatory proposals as early indicators.

## Selection Metadata
```
id: scenario-planning
category: strategic
best_for: [long-term-planning, high-uncertainty, strategy-robustness]
requires: [key-uncertainties, driving-forces, time-horizon]
produces: [multiple-scenarios, robust-strategies, early-warning-indicators]
strengths: [handles-deep-uncertainty, challenges-assumptions, no-probabilities-required]
limitations: [scenario-quality-varies, can-be-overwhelming, 2x2-oversimplification]
combine_with: [decision-under-uncertainty, strategic-analysis, option-reasoning, premortem]
avoid_when: [future-is-predictable, short-time-horizon, organization-cannot-act-on-insights]
```