# Statistical Reasoning

## Purpose
Draw reliable inferences from data by modeling variability, estimating unknown quantities, and quantifying the uncertainty in those estimates using the machinery of probability theory.

## When to Use
- When you have data and need to estimate an unknown quantity or relationship
- When you need to distinguish signal from noise in observed data
- When you need to summarize a dataset with descriptive statistics before applying more specific methods
- When the problem involves generalizing from a sample to a population
- When you need to assess whether an observed pattern is likely to replicate

## When Not to Use
- When you have no data — statistical reasoning requires observations
- When the data-generating process is deterministic and there is no variability to model
- When the question is purely logical or deductive
- When the data is population-level (no sampling) and the question is purely descriptive
- When model assumptions are clearly violated and cannot be corrected

## Problem Signals
- The problem involves "estimating" an unknown quantity from data
- The user describes "variability" or "noise" in measurements
- The problem asks about "trends," "relationships," or "patterns" in data
- The user has a sample and wants to make claims about a broader population
- The problem requires "quantifying how confident" we should be in an estimate

## Inputs
- A dataset with observations (quantitative, categorical, or both)
- A research question or estimand: what quantity is being estimated
- A statistical model relating the data to the unknown quantity
- Knowledge of the data-generating process (sampling method, measurement error structure)

## Procedure

### Step 1: Define the Estimand
Specify precisely what you want to estimate. Examples: a population mean, a regression coefficient, a correlation, a difference between groups, a prediction interval.

### Step 2: Explore the Data
- Compute summary statistics (mean, median, variance, quantiles)
- Visualize distributions (histograms, box plots, scatter plots)
- Check for outliers, missing data, and data quality issues
- Identify the scale and distributional shape of each variable

### Step 3: Choose a Statistical Model
Select a model appropriate for the data type and estimand:
- Continuous outcome: linear regression, ANOVA, t-tests
- Binary outcome: logistic regression, proportions test
- Count data: Poisson or negative binomial regression
- Time-to-event: survival analysis
- Multivariate: PCA, factor analysis, clustering

### Step 4: Check Model Assumptions
Verify the assumptions of the chosen model:
- Independence of observations
- Distributional assumptions (normality, homoscedasticity)
- Linearity (for linear models)
- Absence of influential outliers
If assumptions are violated, consider transformations, robust methods, or alternative models.

### Step 5: Estimate and Quantify Uncertainty
- Compute point estimates of the parameters
- Compute standard errors and confidence intervals
- For prediction: compute prediction intervals (wider than confidence intervals)
- Report the uncertainty, not just the point estimate

### Step 6: Validate the Model
- Check residuals for patterns that indicate model misspecification
- Use cross-validation or holdout data to assess predictive performance
- If the model is used for inference (not prediction), check sensitivity to alternative specifications

### Step 7: Interpret with Caution
- Distinguish between statistical significance and practical significance
- Correlation is not causation — statistical reasoning alone cannot establish causal relationships
- Acknowledge limitations: sampling bias, measurement error, unobserved confounders

## Output
- Point estimates with confidence intervals
- Model diagnostics and assumption checks
- A measure of model fit (R-squared, AIC, deviance, etc.)
- A clear statement of what conclusions the data supports and what it does not

## Strengths
- Handles variability: explicitly models noise and uncertainty
- Generalizable: methods apply across diverse domains and data types
- Quantifies uncertainty: produces intervals, not just point estimates
- Well-validated: extensive theory on when estimates are reliable

## Limitations
- Model dependence: different models can produce different conclusions from the same data
- Assumption sensitivity: valid inference requires assumptions that may be violated
- Causally limited: statistical reasoning alone cannot establish causation without experimental design or causal methods
- Garbage in, garbage out: poor data quality or biased sampling invalidates conclusions regardless of method sophistication

## Common Failure Modes
- **Model fishing**: trying many models and reporting the one that fits best or produces the desired result. This inflates false positive rates.
- **Assumption neglect**: applying a method without checking whether its assumptions hold. A t-test on skewed data with unequal variances produces invalid p-values.
- **Confusing correlation with causation**: observing a statistical association and concluding one variable causes the other. Use causal reasoning methods for this.
- **Over-interpreting non-significance**: treating "failed to reject the null" as "the null is true." Absence of evidence is not evidence of absence.
- **Ignoring effect size**: reporting only p-values without the magnitude of the effect. A trivially small effect can be statistically significant with enough data.
- **Extrapolation beyond the data**: making predictions or inferences for values far outside the range of observed data, where the model has no support.

## Verification
- Are the model assumptions checked and documented?
- Is the uncertainty quantification appropriate (standard errors, confidence intervals, prediction intervals)?
- Does the model fit the data reasonably well? Check residuals and goodness-of-fit measures.
- Are conclusions robust to reasonable alternative model specifications?
- Is the distinction between statistical significance and practical significance clearly articulated?

## Combine With
- **Causal Graph Reasoning**: to move from association to causation
- **Bayesian Reasoning**: to incorporate prior information into the estimation
- **Frequentist Reasoning**: the dominant framework for statistical inference
- **Experimental Design**: to ensure the data is suitable for causal inference
- **Uncertainty Quantification**: for more rigorous treatment of uncertainty sources

## Conflicts With
- **Deductive Reasoning**: statistical conclusions are uncertain by nature; deductive reasoning requires certainty. Do not treat statistical estimates as logical truths.

## Example
A researcher wants to estimate the effect of a training program on employee productivity. They have productivity scores for 200 employees before and after the program, and 200 control employees who did not receive training.

- Estimand: the average treatment effect of training on productivity change
- Model: linear regression with productivity change as the outcome, training status as the predictor, and pre-training productivity as a covariate
- Estimate: training increases productivity by 3.2 points (95% CI: [1.1, 5.3])
- Diagnostics: residuals are approximately normal; no influential outliers; variance is similar across groups
- Interpretation: the data is consistent with a modest positive effect of training. The confidence interval excludes zero, so the effect is statistically significant. Whether a 3.2-point increase is practically meaningful depends on the productivity scale and the cost of the program.

## Selection Metadata
```
id: statistical-reasoning
category: probabilistic
best_for: [data analysis, estimation, inference from samples]
requires: [data, statistical model]
produces: [estimates, uncertainty intervals]
strengths: [handles variability, quantifies uncertainty]
limitations: [model dependence, assumptions required]
combine_with: [causal-graph-reasoning, bayesian-reasoning, frequentist-reasoning, experimental-design, uncertainty-quantification]
avoid_when: [data is absent, model assumptions are violated]
```