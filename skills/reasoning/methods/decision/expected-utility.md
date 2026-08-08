# Expected Utility

## Purpose
Select the option that maximizes expected value by weighing each possible outcome by its probability and the decision maker's utility for it. This is the normative standard for rational choice under risk.

## When to Use
- When you can enumerate all relevant options and their possible outcomes
- When outcome probabilities are estimable from data, models, or expert judgment
- When utilities (preferences over outcomes) can be meaningfully elicited or approximated
- When the decision maker accepts the von Neumann-Morgenstern axioms of rational choice
- When the decision is consequential enough to justify formal modeling

## When Not to Use
- When probabilities are entirely unknown or cannot be bounded (use decision-under-uncertainty instead)
- When utilities are incommensurable across dimensions (use multi-criteria-decision instead)
- When the decision involves irreversible commitments with unknown future flexibility (combine with option-reasoning)
- When the decision maker's preferences violate expected utility axioms (e.g., Allais paradox scenarios)
- When the decision is trivial and the cost of formal analysis exceeds the stakes

## Problem Signals
- The problem description includes explicit probabilities, percentages, or likelihood estimates
- The user asks "which option maximizes expected value" or "what should I choose given these probabilities"
- The problem involves a gamble, investment, insurance decision, or medical treatment choice with known risk profiles
- The user presents a decision tree or payoff matrix with probability estimates attached to branches
- The problem involves repeated decisions where the law of large numbers applies

## Inputs
- A set of mutually exclusive options (actions, choices, decisions)
- For each option, a set of possible outcomes with associated probabilities (must sum to 1)
- A utility function or value for each outcome (can be monetary, but must reflect risk preferences)
- Risk attitude (risk-neutral, risk-averse, risk-seeking) if utility is not directly elicited

## Procedure
1. Enumerate all available options. Verify they are mutually exclusive and collectively exhaustive.
2. For each option, identify all possible outcomes. Be explicit about what "other" or "default" outcomes look like.
3. Assign a probability to each outcome. Probabilities for each option must sum to 1. Use base rates, historical data, or calibrated expert judgment. Do not fabricate probabilities.
4. Elicit or assign a utility value to each outcome. If using monetary values, assess whether the decision maker is risk-averse (concave utility), risk-neutral (linear), or risk-seeking (convex). For non-monetary outcomes, use a 0-100 scale anchored to the best and worst possible outcomes.
5. For each option, compute expected utility: EU(option) = sum over outcomes of (probability * utility).
6. Select the option with the highest expected utility.
7. Perform sensitivity analysis: vary probabilities and utilities within plausible ranges. If the ranking changes, the decision is sensitive to those inputs and requires caution.
8. Report the recommendation, the expected utility values, and the sensitivity findings.

## Output
- The recommended option with its expected utility
- A ranked list of all options by expected utility
- Sensitivity analysis: which parameters, if changed within plausible bounds, would alter the ranking
- A clear statement of the assumptions made about probabilities and utilities

## Strengths
- Axiomatically grounded: if the decision maker accepts the axioms, expected utility is the uniquely rational choice rule
- Compresses complex trade-offs across uncertain outcomes into a single comparable metric
- Supports sensitivity analysis to identify which uncertainties matter most
- Widely applicable across domains: finance, medicine, policy, engineering, personal decisions

## Limitations
- Utility elicitation is difficult in practice; people cannot reliably report their own utility functions
- Requires probability estimates that may be unreliable or disputed
- Cannot handle unknown unknowns: outcomes not in the model are assigned zero probability by construction
- Assumes separability of outcomes (no complementarities across time or states)
- The axioms are descriptively violated (Allais paradox, Ellsberg paradox, framing effects), so the recommendation may conflict with intuition

## Common Failure Modes
- Using expected value (monetary) when the decision maker is risk-averse, ignoring diminishing marginal utility of money
- Fabricating probabilities for outcomes without any empirical basis, creating false precision
- Omitting low-probability high-impact outcomes that would dominate the calculation if included
- Treating the expected utility calculation as the final answer without sensitivity analysis
- Applying expected utility to one-shot decisions where the law of large numbers provides no consolation for a bad outcome
- Confusing expected utility with multi-criteria decision: trying to cram multiple incommensurable values into a single utility number

## Verification
- Check that probabilities for each option sum to exactly 1
- Check that the utility scale is consistent across all outcomes (same anchor points)
- Verify that risk attitude is correctly modeled (not assuming risk neutrality without justification)
- Test whether the ranking survives plausible variation in the two most uncertain parameters
- Confirm that no outcome with probability less than 0.01 has been arbitrarily rounded to zero

## Combine With
- sensitivity-analysis: to test robustness of the recommendation
- risk-analysis: when low-probability catastrophic outcomes are present
- scenario-planning: when probabilities are uncertain and need structured bounding
- option-reasoning: when the decision has sequential stages with future flexibility

## Conflicts With
- multi-criteria-decision: expected utility collapses all values into a single dimension; MCDA preserves multiple dimensions
- decision-under-uncertainty: expected utility requires probabilities; uncertainty methods work without them
- satisficing: expected utility seeks the optimum; satisficing stops at "good enough"

## Example
A startup must choose between three pricing strategies: freemium, flat subscription, and usage-based. For each strategy, they estimate three market response scenarios (strong adoption, moderate, weak) with probabilities 0.3, 0.5, 0.2. They estimate annual revenue (in millions) for each scenario-strategy combination. Because the founders are risk-averse and a bad outcome could kill the company, they apply a concave utility function U(x) = sqrt(x) rather than using raw revenue. Computing expected utility for each strategy yields flat subscription as the highest EU. Sensitivity analysis shows that if the probability of strong adoption exceeds 0.45, freemium becomes optimal — a finding that informs how much market research to invest in before committing.

## Selection Metadata
```
id: expected-utility
category: decision
best_for: [explicit-outcomes, known-probabilities, rational-choice]
requires: [options, outcome-probabilities, utilities]
produces: [optimal-choice, expected-utility-values, sensitivity-findings]
strengths: [axiomatic-foundation, consistent, compressible]
limitations: [utility-elicitation, probability-estimation, unknown-unknowns-blind]
combine_with: [sensitivity-analysis, risk-analysis, option-reasoning, scenario-planning]
avoid_when: [probabilities-are-unknown, utilities-are-incommensurable, one-shot-high-stakes-without-sensitivity]
```