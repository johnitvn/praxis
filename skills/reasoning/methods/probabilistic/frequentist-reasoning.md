# Frequentist Reasoning

## Purpose
Make inferences from data by analyzing the properties of procedures over repeated sampling, controlling long-run error rates without incorporating prior beliefs about parameters.

## When to Use
- When you need to control long-run error rates (Type I and Type II) at specified levels
- When the sampling process is well-defined and repeatable
- When you want conclusions that do not depend on subjective prior beliefs
- When the problem is naturally framed as a decision rule with a significance threshold
- When you need to estimate an effect with a confidence interval that has a guaranteed coverage probability

## When Not to Use
- When reasoning about a single unique event with no reference class for repeated sampling
- When prior information is substantial and ignoring it would be wasteful or misleading
- When the sampling model is not well-defined or the data-generating process is unknown
- When the hypothesis space is not pre-specified
- When you need probability statements about hypotheses (rather than about procedures)

## Problem Signals
- The problem asks "is this effect statistically significant?"
- The user describes an experiment with a control group and a treatment group
- The user mentions "p-value," "confidence interval," or "null hypothesis"
- The problem involves deciding whether observed differences are real or noise
- The user wants to control the false positive rate at a specific level (e.g., 5%)

## Inputs
- A well-defined null hypothesis
- A sampling model describing how data is generated under the null
- A test statistic and its sampling distribution
- A significance threshold (alpha level)
- The observed data

## Procedure

### Step 1: Specify the Null Hypothesis
Define H0 precisely. It must be specific enough to generate a sampling distribution for the test statistic. The null typically represents "no effect" or "no difference."

### Step 2: Choose a Test Statistic
Select a statistic that captures the effect of interest. The statistic must have a known (or derivable) sampling distribution under the null hypothesis.

### Step 3: Set the Significance Level
Choose alpha (typically 0.05). This is the maximum acceptable probability of rejecting H0 when it is true (Type I error). Select this before seeing the data.

### Step 4: Compute the Test Statistic
Calculate the observed value of the test statistic from the data.

### Step 5: Compute the p-value
The p-value is the probability of observing a test statistic at least as extreme as the observed value, assuming the null hypothesis is true. It is NOT the probability that the null hypothesis is true.

### Step 6: Make a Decision
- If p < alpha: reject the null hypothesis
- If p >= alpha: fail to reject the null hypothesis

### Step 7: Report Effect Size and Confidence Interval
A significance decision alone is insufficient. Report:
- The estimated effect size with its confidence interval
- The confidence interval's interpretation: if the procedure were repeated many times, the interval would contain the true parameter in (1-alpha) proportion of samples
- Whether the effect size is practically meaningful, not just statistically significant

## Output
- The p-value and the significance decision
- An effect size estimate
- A confidence interval at the specified confidence level
- A statement about practical significance (distinct from statistical significance)

## Strengths
- Objective: conclusions follow from the data and the sampling model without subjective inputs
- Error control: provides guaranteed long-run error rates under the model assumptions
- Well-established: widely understood methodology with extensive literature
- Reproducible: same data + same procedure = same conclusion

## Limitations
- Cannot make probability statements about hypotheses: p-values are about the data, not the hypothesis
- Arbitrary thresholds: the binary "significant/not significant" distinction at alpha = 0.05 is a convention, not a law of nature
- p-hacking vulnerability: flexible analysis choices can inflate the effective false positive rate
- Does not incorporate prior information or costs of different errors
- Large samples make trivial effects statistically significant

## Common Failure Modes
- **p-value misinterpretation**: treating p < 0.05 as "the probability the null is true is less than 5%." The p-value is P(data | H0), not P(H0 | data).
- **Confusing statistical and practical significance**: a tiny effect can be statistically significant with a large enough sample. Report the effect size and judge its practical importance separately.
- **p-hacking**: trying multiple analyses and reporting only the significant one. Pre-register the analysis plan or correct for multiple comparisons.
- **The null ritual**: mechanically applying the p < 0.05 decision rule without thinking about effect size, confidence intervals, or whether the null hypothesis is even plausible.
- **Ignoring power**: failing to reject the null when the sample is too small to detect a meaningful effect. Always consider statistical power.
- **Confidence interval misinterpretation**: a 95% CI does not mean there is a 95% probability the true value lies in the interval. It means the procedure that generated the interval captures the true value in 95% of repeated samples.

## Verification
- Is the null hypothesis precisely specified? Vague nulls produce meaningless p-values.
- Was the significance threshold set before seeing the data?
- Are the sampling distribution assumptions satisfied? Check normality, independence, and equal variance assumptions.
- If multiple tests were performed, were corrections applied (Bonferroni, FDR)?
- Is the effect size reported alongside the p-value?

## Combine With
- **Bayesian Reasoning**: to incorporate prior information and produce probability statements about hypotheses
- **Effect Size Analysis**: to assess practical significance
- **Power Analysis**: to design studies with adequate sample size
- **Experimental Design**: to ensure valid randomization and control

## Conflicts With
- **Bayesian Reasoning**: when the question is "what should I believe?" rather than "what decision rule should I use?" Frequentist methods answer the latter.
- **Decision Analysis**: when error costs are asymmetric, the fixed alpha threshold may be inappropriate.

## Example
An A/B test on a website: variant B has a conversion rate of 12.3% (n=10,000) and variant A (control) has 11.8% (n=10,000). The observed difference is 0.5 percentage points.

- H0: conversion rates are equal
- Test statistic: z-test for difference in proportions
- p-value: 0.04
- Decision: reject H0 at alpha = 0.05
- Effect size: 0.5 percentage point difference
- 95% CI: [0.02%, 0.98%]
- Practical significance: the 0.5pp lift is small; whether it is worth deploying depends on business context and implementation cost

The p-value says the observed difference is unlikely under the null. It does not say the probability that B is better is 96%. It does not say the effect is large enough to matter.

## Selection Metadata
```
id: frequentist-reasoning
category: probabilistic
best_for: [repeated sampling, error control, significance testing]
requires: [sampling model, significance threshold]
produces: [p-values, confidence intervals]
strengths: [objective error rates, well-established]
limitations: [misinterpretation common, arbitrary thresholds]
combine_with: [bayesian-reasoning, effect-size-analysis, power-analysis, experimental-design]
avoid_when: [single event, prior information is critical]
```