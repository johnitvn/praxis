# Superforecasting

## Purpose
Produce calibrated probabilistic forecasts about real-world events through a disciplined methodology of question decomposition, base-rate anchoring, Bayesian updating, and regular calibration. This method is derived from the practices of "superforecasters" — individuals who consistently outperform experts and prediction markets in long-term geopolitical and economic forecasting tournaments.

## When to Use
- When forecasting complex, real-world events with long time horizons (months to years)
- When the question is decomposable into sub-questions that can be forecast more precisely
- When base rates exist for the class of event but the specific case has distinguishing features
- When you are willing to update forecasts incrementally as new information arrives
- When forecast accuracy matters enough to justify the time investment (hours to days per question)

## When Not to Use
- When a quick answer is needed and the time investment of superforecasting is not justified
- When the question is not decomposable into smaller, forecastable sub-questions
- When base rates are unavailable and the question is entirely novel
- When the forecast is for a deterministic system where a model can compute the exact answer
- When the forecaster is not willing to track and calibrate their forecasts over time

## Problem Signals
- The user asks "what is the probability that X will happen by date Y?"
- The user describes a geopolitical, economic, or technological event with multiple contributing factors
- The user has access to news, data, and expert analysis that can be used to update a forecast over time
- The user wants a forecast they can act on, not just a qualitative "likely" or "unlikely"

## Inputs
- A clearly defined forecasting question with a specific outcome, time horizon, and resolution criteria
- Access to base rate data for the class of event
- Knowledge of the specific factors that distinguish this case from the base rate
- A commitment to track the forecast and update it as new information arrives

## Procedure
1. **Define the question precisely.** The question must specify: what event, by when, and how it will be verified. "Will the Fed raise interest rates?" is vague. "Will the Federal Reserve raise the federal funds rate by at least 25 basis points at any FOMC meeting before December 31, 2026?" is forecastable.
2. **Decompose the question.** Break it into sub-questions that are easier to forecast. For the Fed question: (a) What is the current inflation rate and trend? (b) What is the current unemployment rate and trend? (c) What have FOMC members said in recent statements? (d) What is the historical frequency of rate increases in similar economic conditions? Each sub-question should have its own forecast.
3. **Anchor with the base rate.** For each sub-question and the overall question, find the base rate: how often does this type of event occur in similar circumstances? The base rate is the starting point. Do not skip this step — superforecasters are distinguished by their use of base rates, not by superior intuition.
4. **Adjust with specific evidence.** Move away from the base rate only when you have specific, reliable evidence that this case differs from the average. Each piece of evidence should nudge the probability, not replace it. Use Bayesian updating: prior = base rate, update with likelihood ratios from each piece of evidence.
5. **Use Fermi estimation.** For sub-questions where data is unavailable, break the question into components you can estimate. "How many EV charging stations will be built in the US next year?" becomes: number of EVs sold x percentage of buyers who install chargers x average chargers per installation. Each component is easier to estimate than the whole.
6. **Assign a probability.** Synthesize the sub-forecasts into an overall probability. Express it as a specific number (e.g., 65%), not a vague term ("likely"). Superforecasters use granular probabilities (5% increments) rather than coarse categories.
7. **Update incrementally.** As new information arrives, update the forecast. Do not wait for a major event — small pieces of evidence should produce small adjustments. Track the forecast over time to see the evolution of your thinking.
8. **Calibrate regularly.** After the resolution date, compare your forecast to the actual outcome. Compute your Brier score. Assess whether your confidence intervals were appropriately wide. Use the calibration method to identify and correct systematic biases.

## Output
- A specific probability (e.g., 65%) for the target event, with a rationale document
- Sub-forecasts for each decomposed sub-question
- The base rate used as the anchor, with the adjustments made
- A forecast tracking log showing how the probability evolved over time
- A post-resolution calibration assessment (after the event)

## Strengths
- Empirically validated: superforecasters in the IARPA forecasting tournament outperformed intelligence analysts with access to classified information by 30%
- Produces forecasts that are specific, calibrated, and updatable, making them actionable for decision-making
- The decomposition step reveals which assumptions drive the forecast, enabling targeted evidence gathering
- The discipline of tracking and calibrating creates a virtuous cycle of improvement

## Limitations
- Time-intensive: a single superforecast can take hours to days of research
- Requires a base rate; for truly novel events, the base rate is unknown and the forecast is less reliable
- The method works best for events with 3-month to 2-year horizons; very short-term events are too noisy and very long-term events have too many unknowns
- Requires the forecaster to be intellectually honest about updating; confirmation bias can lead to selective updating

## Common Failure Modes
- **Base rate neglect**: skipping the base rate step and starting with the specific evidence, which produces forecasts that are overconfident and under-anchored
- **Decomposition paralysis**: decomposing the question into too many sub-questions, spending more time on decomposition than on forecasting, and never producing a final probability
- **Granularity theater**: using specific probabilities (e.g., 67%) without the rigor to justify them, creating an illusion of precision
- **Sticky priors**: failing to update the forecast when new evidence arrives, treating the initial probability as a final answer rather than a starting point
- **Selective updating**: updating the forecast when evidence supports the current view and dismissing evidence that contradicts it
- **Resolution neglect**: forecasting events whose outcomes will never be verified, defeating the calibration feedback loop that makes superforecasting work

## Verification
- Is the question defined with a specific outcome, time horizon, and resolution criteria?
- Has the question been decomposed into sub-questions, each with its own forecast?
- Is the forecast anchored to a documented base rate?
- Has the forecast been updated as new information arrived?
- Has the forecast been calibrated against actual outcomes after resolution?

## Combine With
- bayesian-reasoning (from probabilistic category) for the formal updating mechanism
- calibration for tracking and improving forecast accuracy over time
- decomposition (from first-principles category) for breaking questions into sub-questions
- reference-class-forecasting for finding and using base rates
- ensemble-forecasting for combining multiple superforecasters' predictions

## Conflicts With
- Methods that produce deterministic predictions without probabilities
- Expert judgment that relies on domain expertise without base rates or calibration
- Quick, intuitive forecasting that does not invest in decomposition or updating

## Example
**Question**: Will North Korea conduct a nuclear test before December 31, 2026?

**Decomposition**:
1. What is the historical frequency of North Korean nuclear tests? (6 tests over 20 years = 0.3 tests/year, but clustered in active periods)
2. Is North Korea currently in an active testing period? (Last test was in 2017, a 9-year gap — unusual)
3. What is the current political posture? (Recent statements indicate nuclear modernization is a priority; Kim Jong Un has referenced "new strategic weapons")
4. What is the external pressure? (UN sanctions remain in place; China has not signaled tolerance for new tests; US policy under the current administration is ambiguous)
5. What is the technical readiness? (Satellite imagery shows activity at the Punggye-ri test site; tunnel maintenance has been observed)

**Sub-forecasts**:
- Probability of active testing period: 70%
- If active, probability of a test within 12 months: 60%
- If not active, probability of a test anyway: 5%

**Base rate**: Among countries with nuclear weapons programs, the probability of a test in any given year during an active development phase is approximately 40%.

**Adjustment**: North Korea's 9-year gap is longer than the historical average for active programs. This could indicate either a permanent pause or a buildup to a significant test. The satellite imagery and political rhetoric suggest the latter. Adjust upward from 40% to 55%.

**Overall probability**: 55% (revised from 45% last month after new satellite imagery was released).

**Update log**: 
- January: 40% (base rate anchor)
- March: 45% (after Kim Jong Un's New Year speech)
- June: 50% (after satellite imagery of Punggye-ri activity)
- September: 55% (after defense ministry statement on "new strategic weapons")

## Selection Metadata
```
id: superforecasting
category: forecasting
best_for: [geopolitical events, long-term predictions, probabilistic judgments]
requires: [question decomposition, base rates, Bayesian updating]
produces: [calibrated probabilities]
strengths: [empirically validated, outperforms experts]
limitations: [requires training, time-intensive]
combine_with: [bayesian-reasoning, calibration, decomposition]
avoid_when: [quick answer needed, question is not decomposable]
```