# Uncertainty Quantification

## Purpose
Systematically identify, characterize, and propagate sources of uncertainty through a model or decision process to produce calibrated uncertainty bounds on conclusions, enabling robust decisions under incomplete knowledge.

## When to Use
- When model predictions or estimates feed into consequential decisions
- When there are multiple identifiable sources of uncertainty that compound
- When you need to communicate the limits of knowledge to decision-makers
- When comparing models or methods and their uncertainty profiles differs
- When the cost of being wrong is high and you need to know how wrong you might be
- When validating that a model's confidence is well-calibrated (predicted uncertainty matches observed error)

## When Not to Use
- When the sources of uncertainty are fundamentally unknowable and cannot be bounded
- When a decision is insensitive to the range of plausible uncertainty
- When the model is so simple that uncertainty is already fully characterized by a standard error
- When the problem demands a single point estimate and decision-makers will not use uncertainty information

## Problem Signals
- The user asks "how confident should I be in this prediction?"
- The problem involves multiple uncertain inputs that combine
- The user describes "worst-case" and "best-case" scenarios without a systematic framework
- The problem involves model selection and the user wants to know which model to trust
- The user mentions "error bars," "prediction intervals," or "confidence bands"

## Inputs
- A model or decision function that produces outputs from inputs
- A list of uncertainty sources for each input and model component
- For each source: its type (aleatoric or epistemic), its magnitude or distribution, and whether it is reducible
- The required level of confidence for the output bounds

## Procedure

### Step 1: Classify Uncertainty Sources
Categorize each source of uncertainty:
- **Aleatoric uncertainty**: inherent randomness in the system that cannot be reduced by more data or better models (e.g., coin flips, measurement noise). Quantify with probability distributions.
- **Epistemic uncertainty**: uncertainty due to limited knowledge that can be reduced with more data, better models, or expert input (e.g., parameter uncertainty, model form uncertainty). Quantify with distributions that narrow as knowledge improves.
- **Model form uncertainty**: uncertainty about whether the model structure itself is correct. This is epistemic but harder to quantify — consider multiple model structures.

### Step 2: Characterize Each Source
For each source, specify:
- A probability distribution (if data is available to estimate it)
- Bounds (if only a range is known)
- An interval with expert-elicited confidence (if neither data nor bounds are available)
- Note whether the source is correlated with other sources

### Step 3: Choose a Propagation Method
- **Analytical propagation**: when the model is simple and uncertainties are well-behaved (e.g., Gaussian error propagation with Taylor expansion)
- **Monte Carlo simulation**: when the model is complex but can be evaluated quickly. Sample from input distributions, run the model, and collect the output distribution.
- **Polynomial chaos expansion**: when the model is expensive to evaluate but smooth. Build a surrogate that approximates the model.
- **Interval analysis**: when only bounds are known for inputs. Propagate intervals through the model.

### Step 4: Propagate Uncertainty
Execute the chosen propagation method. Produce an ensemble of outputs or a set of output bounds.

### Step 5: Analyze Output Distribution
- Compute summary statistics of the output distribution (mean, median, variance, quantiles)
- Construct a prediction interval at the desired confidence level
- Identify which input uncertainties dominate the output uncertainty (sensitivity analysis)
- Report the shape of the output distribution — is it symmetric, skewed, multi-modal?

### Step 6: Calibration Check
If historical predictions and outcomes are available, check whether the quantified uncertainty is well-calibrated:
- Do the 90% prediction intervals contain the true value approximately 90% of the time?
- If intervals are too narrow (overconfident), the uncertainty quantification is incomplete.
- If intervals are too wide (underconfident), the model may be useful but the UQ is conservative.

### Step 7: Communicate Uncertainty
- Report uncertainty in terms the decision-maker can use: "There is a 90% probability the outcome falls between X and Y."
- For risk-averse decisions, report worst-case bounds.
- Distinguish between reducible uncertainty (more data will help) and irreducible uncertainty (it will not).

## Output
- A complete list of uncertainty sources with their characterization
- Output uncertainty bounds or distributions at the requested confidence level
- A sensitivity ranking showing which sources drive the output uncertainty
- A calibration assessment (if historical data is available)

## Strengths
- Explicit: makes uncertainty visible rather than hiding it behind a point estimate
- Supports robustness: enables decisions that account for the range of possible outcomes
- Identifies knowledge gaps: highlights where more data or better models would reduce uncertainty
- Model-agnostic: applies to any model that maps inputs to outputs

## Limitations
- Requires enumerating all significant uncertainty sources — missing one source can produce overconfident bounds
- Computationally expensive for complex models with many uncertainty sources
- Distributional assumptions for inputs may be poorly justified
- Epistemic uncertainty about model form is the hardest to quantify and the most likely to be underestimated
- Calibration requires historical data that may not be available

## Common Failure Modes
- **Ignoring model form uncertainty**: quantifying parameter uncertainty perfectly while using a model structure that is fundamentally wrong. The tight uncertainty bounds are misleading.
- **Treating epistemic uncertainty as aleatoric**: assuming a parameter is inherently random when it is actually unknown but fixed. This inflates uncertainty but in the wrong way.
- **Assuming independence**: treating correlated uncertainty sources as independent, which can produce bounds that are too narrow or too wide depending on the correlation structure.
- **Overconfidence from limited samples**: estimating input distributions from small samples and treating the estimated distribution as the true distribution. The uncertainty of the uncertainty estimate itself is ignored.
- **Cherry-picking sources**: including only the uncertainty sources that are easy to quantify and ignoring the ones that are hard but potentially large.

## Verification
- Are all major categories of uncertainty addressed: input data, parameter estimates, model structure, and scenario conditions?
- Is the distinction between aleatoric and epistemic uncertainty clear and correct?
- If using Monte Carlo, are enough samples drawn for convergence? Check with a convergence diagnostic.
- Are the output bounds plausible? If they are unreasonably wide or narrow, re-examine the input characterizations.
- If calibration data is available, do the empirical coverage rates match the nominal rates?

## Combine With
- **Sensitivity Analysis**: to identify which inputs drive output uncertainty
- **Risk Analysis**: to evaluate decisions under the quantified uncertainty
- **Bayesian Reasoning**: to update epistemic uncertainty as new data arrives
- **Statistical Reasoning**: to estimate input distributions from data
- **Ensemble Methods**: to address model form uncertainty by using multiple models

## Conflicts With
- **Optimization Methods**: when optimizing for a single best solution, uncertainty information may be discarded. Integrate UQ into robust optimization instead.

## Example
A model predicts the cost of a construction project. Uncertainty sources:
- Material costs: aleatoric, modeled as log-normal with mean $100/unit and coefficient of variation 0.15
- Labor productivity: epistemic, modeled as uniform between 8 and 12 units/day based on expert judgment
- Weather delays: aleatoric, modeled as Poisson with rate 2 days/month
- Model form: the cost model assumes linear scaling; the true relationship may be nonlinear

Monte Carlo propagation with 10,000 samples produces:
- Median cost: $487,000
- 90% prediction interval: [$412,000, $598,000]
- Dominant uncertainty source: labor productivity (explains 52% of output variance)
- Model form uncertainty not quantified: acknowledge this as a limitation

The decision-maker now knows the range of plausible costs and that reducing uncertainty about labor productivity (through a pilot study) would narrow the interval the most.

## Selection Metadata
```
id: uncertainty-quantification
category: probabilistic
best_for: [risk assessment, robust decisions, model validation]
requires: [uncertainty sources, model]
produces: [uncertainty bounds, confidence distributions]
strengths: [explicit uncertainty, supports robust decisions]
limitations: [requires enumeration of uncertainties, computationally expensive]
combine_with: [sensitivity-analysis, risk-analysis, bayesian-reasoning, statistical-reasoning, ensemble-methods]
avoid_when: [uncertainty sources are unknowable]
```