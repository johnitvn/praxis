# Calibration

## Purpose
Assess and improve the accuracy of probabilistic forecasts by comparing predicted probabilities against actual outcome frequencies. A well-calibrated forecaster whose 70% confidence predictions come true 70% of the time produces forecasts that can be used for decision-making with known reliability.

## When to Use
- When you are making probabilistic forecasts and want to know how much to trust them
- When you have a history of forecasts with known outcomes and want to quantify your accuracy
- When overconfidence is a known risk (e.g., experts forecasting outside their domain, high-stakes single estimates)
- When you want to improve forecast quality over time through feedback

## When Not to Use
- When you have no outcomes to compare against — calibration requires a track record
- When forecasts are deterministic (yes/no with no probability) — calibration applies to probabilistic judgments
- When the forecasting task is a one-off with no opportunity for iterative improvement
- When the forecaster is already known to be well-calibrated and the cost of calibration assessment exceeds its benefit

## Problem Signals
- The user expresses high confidence in a forecast without evidence of past accuracy
- The user provides a confidence interval that is suspiciously narrow ("the project will take 6-8 weeks")
- The user has a history of being surprised by outcomes they were "sure" about
- The user makes probabilistic statements but never revisits them to check accuracy

## Inputs
- A set of probabilistic forecasts, each with a predicted probability (e.g., "60% chance of rain") or a confidence interval
- The actual outcomes for those forecasts (did it rain? what was the actual value?)
- A sufficient sample size: at least 20-30 forecasts for a rough calibration assessment, 100+ for a reliable one

## Procedure
1. **Organize forecasts by predicted probability.** Group forecasts into bins: 0-10%, 10-20%, ..., 90-100%. For confidence intervals, group by the stated confidence level (e.g., 80% intervals, 90% intervals).
2. **Compute actual frequency per bin.** For each bin, count how many forecasts had the predicted outcome. Divide by the total number of forecasts in that bin. This is the empirical probability.
3. **Plot the calibration curve.** X-axis: predicted probability. Y-axis: actual frequency. A perfectly calibrated forecaster produces a diagonal line (y = x). Points above the diagonal indicate underconfidence (outcomes happen more often than predicted). Points below the diagonal indicate overconfidence (outcomes happen less often than predicted).
4. **Compute the Brier score.** For each forecast, compute (predicted probability - actual outcome)^2, where actual outcome is 1 if the event occurred and 0 otherwise. Average across all forecasts. A Brier score of 0 is perfect; 0.25 is no better than guessing 50/50; lower is better.
5. **Diagnose the pattern.** Common patterns: (a) overconfidence: actual frequencies are closer to 50% than predicted, the calibration curve is flatter than the diagonal; (b) underconfidence: actual frequencies are more extreme than predicted, the curve is steeper; (c) systematic bias: consistently over- or under-predicting in one direction.
6. **Apply calibration correction.** If overconfident: widen confidence intervals. If underconfident: narrow them. If systematically biased: adjust the central estimate. The correction should be based on the observed calibration pattern, not intuition.
7. **Track calibration over time.** Reassess calibration periodically. A forecaster who improves their Brier score over time is learning. A forecaster whose calibration degrades may be overcorrecting or facing a changing environment.

## Output
- A calibration curve showing predicted vs. actual frequencies
- A Brier score quantifying overall accuracy
- A diagnosis of the calibration pattern (overconfident, underconfident, biased)
- Recommended corrections to apply to future forecasts

## Strengths
- Provides an objective, quantitative measure of forecast quality
- Surfaces overconfidence that is invisible to the forecaster
- Creates a feedback loop that drives improvement over time
- Enables decision-makers to adjust forecasts based on the forecaster's known calibration

## Limitations
- Requires a track record of forecasts and outcomes, which takes time to accumulate
- Calibration is domain-specific: a forecaster well-calibrated in one domain may be poorly calibrated in another
- A well-calibrated forecaster can still be uninformative (e.g., always predicting the base rate)
- Small sample sizes produce noisy calibration estimates that can be misleading

## Common Failure Modes
- **Calibration without discrimination**: optimizing for calibration while ignoring whether the forecasts distinguish between events that happen and those that don't. A forecaster who always predicts the base rate is perfectly calibrated but useless.
- **Overfitting corrections**: adjusting forecasts based on a small calibration sample, producing corrections that do not generalize
- **Outcome availability bias**: only tracking forecasts whose outcomes are easy to verify, ignoring the ones that are hard to check, which creates a biased calibration sample
- **Calibration as a checkbox**: computing a calibration score once and declaring the forecaster "calibrated" without ongoing monitoring
- **Confusing calibration with accuracy**: a well-calibrated forecaster can still be wrong about specific events; calibration is about the match between probability and frequency, not about being right

## Verification
- Is the calibration assessment based on at least 20 forecasts?
- Are the forecast bins large enough to produce meaningful frequency estimates (at least 5 forecasts per bin)?
- Is the calibration curve plotted and interpreted, not just the Brier score?
- Has the forecaster's discrimination been assessed alongside calibration?

## Combine With
- bayesian-reasoning (from probabilistic category) for systematic probability updating
- superforecasting for the full methodology that includes calibration as a core practice
- reference-class-forecasting for calibrating forecasts against historical distributions
- metacognition for developing awareness of one's own forecasting accuracy

## Conflicts With
- Methods that treat forecasts as binary (right/wrong) rather than probabilistic
- Forecasting approaches that never revisit old predictions

## Example
**Forecaster**: A product manager who has made 50 probability estimates about feature delivery dates over the past year.

**Calibration assessment**:
- 10 forecasts at 90% confidence: 7 were correct (70% actual). Overconfident.
- 15 forecasts at 70% confidence: 9 were correct (60% actual). Slightly overconfident.
- 12 forecasts at 50% confidence: 6 were correct (50% actual). Well-calibrated.
- 8 forecasts at 30% confidence: 4 were correct (50% actual). Underconfident.
- 5 forecasts at 10% confidence: 2 were correct (40% actual). Underconfident.

**Brier score**: 0.19 (better than guessing, but with room for improvement).

**Diagnosis**: The forecaster is overconfident at high confidence levels and underconfident at low confidence levels. The 90% confidence forecasts should be closer to 70-80%. The 10% confidence forecasts should be closer to 5%.

**Correction**: When the forecaster says "90% confident," treat it as 70-80%. When the forecaster says "10% chance," treat it as a 5% chance. Recalibrate in 6 months.

## Selection Metadata
```
id: calibration
category: forecasting
best_for: [confidence assessment, forecast quality, overconfidence reduction]
requires: [forecasts, outcomes]
produces: [calibration score]
strengths: [improves accuracy, reveals overconfidence]
limitations: [requires outcome data, slow feedback]
combine_with: [bayesian-reasoning, metacognition]
avoid_when: [outcomes are unavailable, calibration is not the goal]
```