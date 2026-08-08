# Inductive Reasoning

## Purpose
Inductive reasoning generalizes from specific observations to broader patterns, principles, or rules. It produces conclusions that are probable but not certain — the conclusion goes beyond what the premises strictly contain.

## When to Use
- When you have a set of observations and need to infer a general pattern.
- When the domain is empirical and you are learning from data.
- When you need to make predictions about unseen cases based on seen cases.
- When certainty is not required and probabilistic conclusions are acceptable.

## When Not to Use
- When certainty is required and the conclusion must be guaranteed.
- When the sample is too small, biased, or unrepresentative of the target population.
- When the domain has known exceptions that make generalization dangerous.
- When you are reasoning about a single case with no pattern to generalize from.

## Problem Signals
- The problem contains "likely," "tends to," "in general," "based on the data," "pattern suggests."
- The user presents multiple examples and asks what they have in common.
- The problem involves prediction: "Given what we've seen, what will happen next?"
- The user has a dataset and asks for the rule or trend.

## Inputs
- A set of observations (specific instances, data points, cases).
- A domain of generalization (what population or class are you generalizing to?).
- Optional: prior knowledge about plausible patterns, which constrains the hypothesis space.

## Procedure
1. **Define the target population.** What are you generalizing to? Be explicit about the scope.
2. **Characterize the sample.** How many observations? How were they collected? Are they representative?
3. **Identify candidate patterns.** What regularities appear in the observations? List multiple possibilities.
4. **Assess sample quality.** Check for: sample size (is it adequate?), selection bias (who/what is missing?), measurement error (are observations reliable?).
5. **Evaluate each pattern.** For each candidate: how well does it fit the observed data? How simple is it? How plausible given prior knowledge?
6. **Choose the best generalization.** Apply Occam's razor: prefer simpler patterns that fit the data. But do not overfit — a pattern that fits noise is not general.
7. **State confidence explicitly.** "Based on N observations from [population], the pattern [X] is likely, with confidence [level]."
8. **Acknowledge uncertainty.** State what would disconfirm the generalization. What evidence would change your mind?

## Output
- A probabilistic generalization: "X tends to Y" with an explicit confidence level.
- The sample characteristics that support the generalization.
- The scope of generalization: what population the conclusion applies to.
- Conditions under which the generalization would be revised.

## Strengths
- Extends knowledge beyond what is directly observed.
- Learns from data without requiring a pre-existing theory.
- Handles empirical domains where formal rules are unavailable.
- Produces falsifiable claims — the generalization can be tested against new observations.

## Limitations
- Conclusions are never certain; they are always probabilistic.
- Sample bias can produce spurious generalizations.
- The problem of induction: past patterns do not guarantee future patterns.
- Overfitting: finding patterns in noise that do not generalize.

## Common Failure Modes
- **Hasty generalization.** Drawing a conclusion from too few observations. Always check sample size against the complexity of the pattern.
- **Ignoring sample bias.** Treating a convenience sample as representative. Always ask: "How were these observations collected?"
- **Confirmation bias.** Noticing only observations that fit a preferred pattern. Always list disconfirming evidence.
- **Overgeneralizing scope.** Extending a pattern beyond the population it was observed in. "All swans are white" fails because the sample was only European swans.
- **Treating induction as deduction.** Stating inductive conclusions with deductive certainty. Never say "therefore it must be" when you mean "therefore it is likely."

## Verification
- Would a new random sample from the same population likely show the same pattern?
- Is the sample size adequate for the complexity of the pattern claimed?
- Are there known counterexamples that the generalization fails to explain?
- Has the generalization been stated with an appropriate confidence qualifier?

## Combine With
- **Deductive reasoning** — use induction to establish general premises, then deduction to derive specific consequences.
- **Statistical reasoning** — use statistical methods to quantify the strength of inductive generalizations.
- **Bayesian reasoning** — use Bayes' rule to update inductive beliefs as new evidence arrives.
- **Abductive reasoning** — use induction to identify patterns, then abduction to explain why those patterns exist.

## Example
**Problem:** A developer observes that every time they deploy on Friday, there is a production incident. They have data from 8 Friday deploys and 20 weekday deploys. All 8 Friday deploys had incidents. Only 2 of 20 weekday deploys had incidents. What should they conclude?

**Application:**
1. Target population: All deploys by this team.
2. Sample: 8 Friday deploys (100% incident rate), 20 weekday deploys (10% incident rate).
3. Candidate pattern: Friday deploys are associated with higher incident rates.
4. Sample quality: 8 Friday deploys is a small sample. Check for confounding — are Friday deploys larger? Are they rushed? Is there less staffing for incident response?
5. Generalization: "Friday deploys appear to be riskier (8/8 vs 2/20), but the sample is small. Confidence: moderate."
6. Disconfirming condition: If the next 3 Friday deploys have no incidents, the pattern weakens substantially.

## Selection Metadata
```
id: inductive-reasoning
category: logical
best_for: [pattern discovery, generalization, empirical domains]
requires: [observations, pattern sensitivity]
produces: [probable generalizations]
strengths: [learns from data, extends knowledge]
limitations: [conclusions are not certain, sample bias]
combine_with: [deductive-reasoning, statistical-reasoning]
avoid_when: [sample is unrepresentative, certainty is required]
```