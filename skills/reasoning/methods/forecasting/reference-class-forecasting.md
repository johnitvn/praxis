# Reference Class Forecasting

## Purpose
Predict the duration, cost, or outcome of a project by comparing it to a class of similar past projects, rather than by decomposing the project into tasks and estimating from the bottom up. This method counters the planning fallacy — the systematic tendency to underestimate time and cost for one's own projects while acknowledging that similar projects typically overrun.

## When to Use
- When forecasting a unique project where bottom-up estimates are likely to be optimistic
- When historical data exists for a class of projects similar enough to serve as a comparison
- When the project has characteristics that can be used to select an appropriate reference class
- When the forecast is for cost, duration, or another quantitative outcome with a known distribution in the reference class

## When Not to Use
- When no reference class exists — the project is truly novel with no comparable precedents
- When the reference class is too heterogeneous (the "similar" projects vary wildly in their outcomes)
- When the project is small and routine enough that bottom-up estimation is reliable
- When the forecast is about a qualitative outcome rather than a quantitative metric

## Problem Signals
- The user says "this project is different" or "we've learned from past mistakes" without specifying what is different
- The user provides a single-point estimate for a complex project ("it will take 3 months")
- The project involves known sources of optimism bias (new technology, unfamiliar domain, internal team estimating its own work)
- Past projects in the same organization have systematically overrun their estimates

## Inputs
- A description of the project to be forecasted, including its key characteristics (size, complexity, novelty, domain)
- A reference class: a set of similar past projects with their actual outcomes (durations, costs, or other metrics)
- Distributional data for the reference class: at minimum, the mean and standard deviation; ideally, the full distribution or key percentiles

## Procedure
1. **Define the outcome to forecast.** Be specific: "total project duration from kickoff to production deployment," not "how long it will take." The outcome must be measurable and comparable across projects.
2. **Identify the reference class.** Select past projects that are similar to the current one on the dimensions that matter for the outcome. The reference class should be broad enough to provide statistical power but narrow enough to be informative. Common dimensions: project type, team size, technology stack, domain, budget range.
3. **Assess distributional fit.** Check whether the current project falls within the range of the reference class on the key characteristics. If the current project is an outlier (much larger, more novel, different domain), the reference class is not appropriate.
4. **Adjust for known differences.** If the current project differs from the reference class average in a specific, measurable way (e.g., the team is 50% larger), adjust the forecast by the expected effect of that difference. Use data from the reference class itself to estimate the effect size if possible.
5. **Produce the forecast.** Report the distribution, not a single point. At minimum: the median (50th percentile), the 25th and 75th percentiles, and the 90th percentile. The 90th percentile is often the most useful for planning: "there is a 90% chance the project will take less than X months."
6. **Validate against the inside view.** Compare the reference class forecast with the bottom-up (inside view) estimate. If the inside view is more optimistic than the reference class median, the inside view is likely biased. The reference class forecast should carry more weight unless there is a specific, documented reason the project is different.

## Output
- A distributional forecast (median, key percentiles) for the target outcome
- The reference class used, with its size and key characteristics
- The adjustment factors applied and their rationale
- A comparison with the inside view (bottom-up estimate) if available

## Strengths
- Empirically validated: reference class forecasting consistently outperforms unaided expert judgment
- Counters the planning fallacy by grounding estimates in actual outcomes rather than intentions
- Provides a distribution, not a point estimate, which supports risk-aware planning
- Transparent: the forecast can be debated by debating the reference class and adjustments, not the estimator's intuition

## Limitations
- Requires a reference class with sufficient data; for truly novel projects, no reference class exists
- The reference class may not be perfectly comparable; adjustments are judgment calls
- Historical data may reflect systemic biases (e.g., all past projects were underfunded in the same way)
- The method does not tell you why projects take as long as they do — it only tells you they do

## Common Failure Modes
- **Cherry-picking the reference class**: selecting projects that support a desired conclusion rather than projects that are genuinely similar
- **Over-adjustment**: adjusting for every difference between the current project and the reference class, effectively recreating the inside view
- **Ignoring the distribution**: treating the median as a point estimate and ignoring the spread, which is often the most important information
- **Survivorship bias**: the reference class only includes completed projects; failed or cancelled projects are missing, biasing the distribution downward
- **Category error**: using a reference class that is too broad (e.g., "all software projects" for a project with unique characteristics)

## Verification
- Is the reference class documented with explicit inclusion criteria?
- Are the adjustment factors justified with data, not intuition?
- Is the forecast reported as a distribution, not a point estimate?
- Has the reference class forecast been compared with the inside view?

## Combine With
- bayesian-reasoning (from probabilistic category) for updating the reference class forecast with project-specific information
- calibration for assessing and improving the forecaster's confidence intervals
- premortem (from risk category) for identifying why the project might fall at the pessimistic end of the distribution
- superforecasting for decomposing the forecast into sub-questions that can be forecast separately

## Conflicts With
- Bottom-up estimation methods that rely solely on task decomposition without historical calibration
- Expert judgment that is not anchored to base rates

## Example
**Forecast**: Duration of a mobile app development project from kickoff to app store launch.

**Reference class**: 15 mobile app projects completed by the same organization in the past 3 years. Project characteristics: team size 2-6, scope includes iOS and Android, backend integration required.

**Reference class distribution**: Median 5.2 months, 25th percentile 3.8 months, 75th percentile 7.1 months, 90th percentile 9.4 months.

**Adjustment**: The current project has a 50% larger team than the reference class median (6 vs 4). Historical data shows that each additional team member reduces duration by approximately 8% (with diminishing returns). Adjusted forecast: median 4.7 months, 75th percentile 6.4 months, 90th percentile 8.5 months.

**Inside view comparison**: The bottom-up estimate from the development team is 3.5 months. The reference class forecast says there is less than a 25% chance of completing in 3.5 months. The inside view is likely optimistic. Recommend planning for 6.4 months (75th percentile) with a contingency budget to 8.5 months.

## Selection Metadata
```
id: reference-class-forecasting
category: forecasting
best_for: [unique projects, cost estimation, duration estimation]
requires: [reference class, distribution data]
produces: [calibrated forecast]
strengths: [reduces optimism bias, evidence-based]
limitations: [requires reference class, class may not fit]
combine_with: [bayesian-reasoning, calibration]
avoid_when: [no reference class exists, project is truly novel]
```