# Option Reasoning

## Purpose
Evaluate decisions that involve sequential, irreversible commitments under uncertainty by recognizing that the ability to wait, learn, and then decide has value. This method adapts the logic of financial options to strategic and operational decisions: the right to make a future decision is itself an asset worth quantifying.

## When to Use
- When a decision involves an irreversible commitment of resources (sunk costs that cannot be recovered)
- When uncertainty is likely to resolve over time: you will know more next quarter or next year than you know now
- When you have the flexibility to delay, stage, expand, contract, or abandon a project
- When comparing a "commit now" strategy against a "wait and see" or "invest in stages" strategy
- When the value of flexibility is not being captured by a standard NPV analysis

## When Not to Use
- When the decision is fully reversible at low cost (there is no option value to waiting)
- When waiting does not resolve uncertainty: the information you need will not arrive with time
- When the window of opportunity will close: waiting means losing the option entirely
- When the decision is a one-shot binary choice with no staging or flexibility
- When the uncertainty is so deep that even the structure of future decisions cannot be anticipated

## Problem Signals
- The user describes a decision that can be made in stages or phases
- The user says "we could start small and expand later" or "we could wait until we know more"
- The problem involves an investment with a large upfront cost that is partly or fully sunk
- The user is comparing a "big bang" approach against a phased or incremental approach
- The NPV of a project is positive but close to zero, and the user suspects that flexibility might tip the balance
- The user is deciding whether to acquire a "platform" or "toehold" that enables future options

## Inputs
- A decision tree that maps the sequence of decisions, uncertainties, and outcomes over time
- The initial decision: "commit now" or "wait" or "invest in a pilot"
- The subsequent decisions that become available after the first stage: expand, continue, contract, abandon, switch
- The uncertainties that will resolve over time: market size, technology maturity, regulatory approval, competitor moves
- The costs of each action at each decision node
- The payoffs at each terminal node
- The discount rate (for time value of money)
- Optionally, the volatility of the underlying uncertainty (for real options valuation using Black-Scholes or binomial models)

## Procedure
1. Map the decision as a tree or sequence of stages. At each stage, identify:
   - What decisions are available?
   - What uncertainties resolve between this stage and the next?
   - What information will be available at the next decision point?
2. Identify the types of real options embedded in the decision:
   - Option to defer: wait until uncertainty resolves before committing
   - Option to stage: invest in phases, with each phase conditional on the success of the previous one
   - Option to expand: invest more if early results are promising
   - Option to contract: reduce scale if early results are disappointing
   - Option to abandon: exit and recover salvage value if the project is failing
   - Option to switch: change inputs, outputs, or technology in response to changing conditions
   - Growth option: an initial investment that creates the opportunity (but not the obligation) to invest in follow-on opportunities
3. Value the project without flexibility: compute the NPV assuming a fixed commitment path. This is the baseline against which the value of flexibility is measured.
4. Value the project with flexibility. Use one of:
   - Decision tree analysis: work backward from the terminal nodes using expected value (or expected utility) at each chance node and optimal choice at each decision node. This works when the tree is small and probabilities are estimable.
   - Binomial lattice: model the evolution of the underlying uncertain value over time as a lattice of up and down moves. Work backward, valuing the option to exercise at each node. This is appropriate when the underlying uncertainty is continuous and volatility can be estimated.
   - Black-Scholes analog: if the option structure is simple (European call or put), use the closed-form formula with appropriate parameter mappings (underlying asset value, exercise price, volatility, time to expiration, risk-free rate).
5. Compute the value of flexibility: (value with flexibility) minus (value without flexibility). If this is positive and material, the option reasoning adds value beyond the static analysis.
6. Identify the optimal exercise strategy: under what conditions (what trigger values) should each option be exercised? This is the decision rule for the future.
7. Sensitivity analysis: vary the uncertainty parameters (volatility, probability of success, market size) and observe how the option value and optimal exercise strategy change.

## Output
- The decision tree or lattice showing the structure of decisions and uncertainties
- The value of the project with and without flexibility
- The value of each embedded real option (defer, stage, expand, abandon, etc.)
- The optimal exercise strategy: trigger values or conditions for each decision
- Sensitivity analysis: how the value of flexibility changes with key parameters
- A recommendation: commit now, wait, or invest in stages

## Strengths
- Values flexibility explicitly, which static NPV analysis treats as worthless
- Particularly valuable when NPV is near zero: option value can be the deciding factor
- Provides decision rules for the future, not just a recommendation for the present
- Handles irreversibility naturally: the more irreversible the commitment, the more valuable the option to wait
- Maps well to real-world decisions that are staged, phased, or conditional
- Bridges the gap between financial analysis and strategic thinking

## Limitations
- Requires a structured decision tree or lattice, which can become combinatorially complex for many stages
- Real options valuation using Black-Scholes requires volatility estimates that are hard to obtain for non-financial assets
- The assumptions of continuous trading and no arbitrage that underlie financial option pricing do not hold for real options
- The value of waiting can be overstated if the analysis ignores competitive preemption: waiting may mean losing the opportunity
- Decision trees require probability estimates, which reintroduces the challenges of subjective probability
- The method can be misused to justify pet projects by adding "option value" to an otherwise negative NPV

## Common Failure Modes
- Treating every project as having option value without identifying a specific, exercisable option
- Using Black-Scholes for real options when the underlying asset is not traded and volatility cannot be estimated
- Ignoring competitive dynamics: the option to wait is worthless if a competitor will preempt you
- Building an overly complex tree that becomes uninterpretable and unactionable
- Computing option value as a point estimate without sensitivity analysis on the volatility parameter
- Forgetting that options expire: the option to defer is not infinite; identify the expiration date
- Overvaluing the option to abandon by ignoring the costs of abandonment (severance, contract penalties, reputational damage)

## Verification
- Check that each identified option is genuinely exercisable: can the organization actually make the decision it describes?
- Verify that the value of flexibility is positive: if waiting adds no value, the NPV analysis was sufficient
- Test that the optimal exercise strategy is actionable: can you observe the trigger condition in practice?
- Confirm that the decision tree captures all material decision nodes and uncertainties
- Validate that the option does not expire before the uncertainty resolves
- Check for competitive preemption: would a competitor capture the value by moving first?

## Combine With
- scenario-planning: to generate the uncertainty states in the decision tree
- decision-under-uncertainty: when probabilities at chance nodes are unknown
- expected-utility: as the valuation method at the terminal nodes of the decision tree
- strategic-analysis: to identify strategic options and competitive dynamics
- game-theoretic-analysis: when the option value depends on competitors' actions
- cost-benefit-analysis: to estimate the costs and benefits at each decision node

## Conflicts With
- satisficing: option reasoning seeks optimal timing; satisficing stops at adequate
- constrained-optimization: optimizes a static allocation; option reasoning optimizes a sequence
- single-point forecasting: option reasoning requires a distribution, not a point estimate

## Example
A pharmaceutical company is deciding whether to commit $500M to build a manufacturing facility for a drug that is in Phase 2 trials. The NPV of building now is -$50M (negative). However, the company has the option to wait 18 months until Phase 3 results are available. The decision tree has two stages: (1) wait or build now, (2) if wait, observe Phase 3 results (success with probability 0.4, failure with 0.6), then decide to build (if success) or abandon (if failure). The value without flexibility (build now) is -$50M. The value with flexibility: wait 18 months, then build if Phase 3 succeeds (NPV = $200M) and abandon if it fails (cost = $0 beyond sunk trial costs). The expected value with flexibility is 0.4 * $200M + 0.6 * $0 = $80M, discounted back 18 months. The value of the option to wait is $80M - (-$50M) = $130M. The recommendation: wait for Phase 3 results. Sensitivity analysis shows that if the probability of Phase 3 success drops below 0.25, even the option to wait has negative value. The company also identifies a growth option: if the drug succeeds, the manufacturing facility could be expanded to produce related compounds — an additional source of option value not captured in the base analysis.

## Selection Metadata
```
id: option-reasoning
category: strategic
best_for: [irreversible-decisions, sequential-decisions, flexibility-valuation]
requires: [decision-tree, uncertainty, flexibility]
produces: [option-value, optimal-timing, exercise-strategy]
strengths: [values-flexibility, handles-irreversibility, provides-decision-rules]
limitations: [requires-probability-estimates, complex-for-many-options, real-options-pricing-assumptions]
combine_with: [scenario-planning, decision-under-uncertainty, expected-utility, strategic-analysis]
avoid_when: [decisions-are-fully-reversible, no-flexibility-exists, competitive-preemption-is-imminent]
```