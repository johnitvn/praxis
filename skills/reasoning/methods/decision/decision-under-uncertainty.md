# Decision Under Uncertainty

## Purpose
Select a robust course of action when probabilities of future states are unknown, unknowable, or disputed. Instead of maximizing expected value, the method applies decision criteria (maximin, minimax regret, optimism-pessimism, Laplace) that require only the specification of possible states and their payoffs.

## When to Use
- When you can enumerate the possible states of the world but cannot assign meaningful probabilities to them
- When probabilities are deeply uncertain: experts disagree, historical data is absent, or the system is non-stationary
- When the decision is one-shot and high-stakes, so the expected value framing is not comforting
- When you need a decision that is robust to the worst case rather than optimal in expectation
- When the decision maker's risk attitude is extreme (highly cautious or highly opportunistic)

## When Not to Use
- When probabilities are well-calibrated and agreed upon (use expected-utility)
- When the decision is repeated many times, so expected value is the right long-run guide
- When you can gather more information to reduce uncertainty (consider option-reasoning for valuing information)
- When payoffs are trivial and the cost of formal analysis exceeds the stakes
- When the set of possible states is unbounded or cannot be enumerated

## Problem Signals
- The user says "we have no idea how likely this is" or "any probability would be a guess"
- The problem involves a novel technology, unprecedented regulatory change, or a geopolitical event with no historical precedent
- The user describes a "worst-case scenario" that would be catastrophic if it occurred
- The decision involves a one-time commitment with no opportunity to learn or adjust
- Experts on the problem disagree not just about the outcome but about the probability distribution itself (Knightian uncertainty)

## Inputs
- A set of mutually exclusive options (actions, strategies)
- A set of possible future states of the world (scenarios) that are mutually exclusive and collectively exhaustive
- A payoff matrix: for each option-state pair, the outcome (in whatever units are meaningful: monetary, lives saved, utility)
- The decision maker's attitude toward uncertainty: extreme caution, moderate caution, or neutrality
- Optionally, a regret matrix derived from the payoff matrix

## Procedure
1. Enumerate the options. Verify that "do nothing" or "status quo" is included as a baseline.
2. Identify the possible states of the world. These must be mutually exclusive and collectively exhaustive. Use scenario-planning if the state space is complex. Include a "worst plausible case" and a "best plausible case" to bound the analysis.
3. Construct the payoff matrix: rows are options, columns are states, cells are the payoff if that option is chosen and that state occurs.
4. Compute the regret matrix: for each state, find the best payoff among all options. Regret for each cell is (best payoff for that state) minus (actual payoff for that cell). Regret represents how much worse you did compared to the best possible choice given that state.
5. Apply decision criteria appropriate to the context:
   - **Maximin** (Wald): For each option, find the minimum payoff across states. Choose the option with the highest minimum. This is the most conservative criterion, appropriate when the worst case is catastrophic.
   - **Maximax**: For each option, find the maximum payoff. Choose the option with the highest maximum. Only appropriate when the decision maker can afford to be fully opportunistic.
   - **Minimax Regret** (Savage): For each option, find the maximum regret. Choose the option with the smallest maximum regret. Appropriate when you want to minimize the pain of being wrong.
   - **Hurwicz (Optimism-Pessimism)**: Choose a coefficient of optimism alpha (0 to 1). For each option, compute alpha * max_payoff + (1 - alpha) * min_payoff. Choose the highest. Use when you can quantify the decision maker's optimism level.
   - **Laplace (Principle of Insufficient Reason)**: Assume all states are equally likely. Compute the average payoff for each option. Choose the highest. Only use when you genuinely believe the states are symmetric in the absence of information — do not use this as a default convenience.
6. Check for dominance: if one option has a strictly better payoff than another in every state, eliminate the dominated option before applying criteria.
7. Report which criterion or criteria are most appropriate for the context and what each recommends.
8. If different criteria recommend different options, report the disagreement and the conditions under which each criterion is appropriate.

## Output
- The payoff matrix and regret matrix
- The recommendation under each applicable decision criterion
- A clear statement of which criterion is most appropriate for this decision maker and context
- Identification of dominated options that should be eliminated regardless of criterion
- If criteria disagree, a structured description of the trade-off between robustness and opportunity

## Strengths
- Works without probability estimates, making it applicable in deep uncertainty
- Makes the decision maker's risk attitude explicit through the choice of criterion
- Identifies robust options that perform reasonably across many states
- The regret matrix provides a psychologically intuitive measure of decision quality
- Dominance analysis eliminates options without needing any criterion at all

## Limitations
- The recommendation depends entirely on which states are included in the model; omitting a state gives it zero weight
- The set of states must be complete, but in deep uncertainty, completeness is hard to guarantee
- The criteria can produce conflicting recommendations, requiring a meta-decision about which criterion to use
- Maximin is extremely conservative and can recommend paralysis or extreme caution
- Laplace assumes equal probabilities without justification, which is a strong claim dressed as neutrality
- All criteria ignore the magnitude of probability differences; they treat all included states as equally "possible"

## Common Failure Modes
- Using Laplace (equal probabilities) as a default without considering whether the states are genuinely symmetric
- Cherry-picking the criterion that gives the answer the decision maker already wants
- Omitting a plausible worst-case state because it is uncomfortable to contemplate
- Constructing the payoff matrix too narrowly (only one or two states) and missing the state that would change the recommendation
- Applying maximin when the decision is reversible and the worst case is merely inconvenient, not catastrophic
- Confusing decision under uncertainty (no probabilities) with decision under risk (known probabilities)

## Verification
- Check that the states are mutually exclusive and collectively exhaustive: can two states occur simultaneously? Is there a state missing?
- Verify that payoffs are in consistent units across the matrix
- Confirm that dominated options have been identified and eliminated
- Test whether the recommendation changes if a plausible additional state is added to the matrix
- Validate that the chosen criterion aligns with the decision maker's stated risk attitude

## Combine With
- scenario-planning: to systematically generate the states of the world
- risk-analysis: when the worst-case states involve catastrophic outcomes
- premortem: to identify states that might be missing from the analysis
- option-reasoning: when the decision has sequential stages and flexibility matters
- sensitivity-analysis: to test how the recommendation changes when payoffs are varied

## Conflicts With
- expected-utility: requires probability estimates; decision under uncertainty explicitly works without them
- bayesian-reasoning: requires priors; uncertainty methods reject the need for priors
- statistical-reasoning: assumes data from which probabilities can be estimated

## Example
A pharmaceutical company must decide whether to invest in a new vaccine platform: (A) mRNA technology, (B) traditional attenuated virus, or (C) do nothing. They identify four future states: (1) pandemic recurrence within 5 years, (2) no pandemic but strong regulatory support for new platforms, (3) no pandemic and regulatory retrenchment, (4) competing technology renders the platform obsolete. They cannot estimate probabilities for these states because the interactions are unprecedented. They construct a payoff matrix in billions of NPV. Maximin recommends the traditional platform (lowest downside). Minimax regret recommends mRNA (if pandemic occurs, not having mRNA would be the biggest missed opportunity). The CEO, who is moderately risk-averse, chooses the Hurwicz criterion with alpha=0.3, which recommends the traditional platform but with a smaller margin. The analysis reveals that the key uncertainty is not pandemic probability but regulatory response — a finding that reshapes the company's government affairs strategy.

## Selection Metadata
```
id: decision-under-uncertainty
category: decision
best_for: [unknown-probabilities, high-stakes, robust-decisions]
requires: [options, possible-states, payoffs]
produces: [robust-choice, regret-bounds, criterion-comparison]
strengths: [handles-deep-uncertainty, no-probability-required, explicit-risk-attitude]
limitations: [conservative, may-miss-opportunities, criterion-dependence]
combine_with: [scenario-planning, risk-analysis, premortem, option-reasoning]
avoid_when: [probabilities-are-well-calibrated, stakes-are-low, states-cannot-be-enumerated]
```