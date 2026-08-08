# Example: Product Decision

## Problem

"Our app has 2M monthly active users. User retention drops 40% after the first week. We have limited engineering capacity (one team of 6). We need to decide: should we invest in improving onboarding, adding social features, or improving performance? We can only do one well this quarter."

## Classification

- **problem_type**: [what-to-do]
- **uncertainty_profile**: epistemic (we have data but not perfect knowledge)
- **stakes**: high (affects retention, growth, revenue)
- **reversibility**: somewhat reversible (can change direction next quarter)
- **domain**: product
- **structure**: multi-stakeholder, resource-constrained

## Selected Methods

1. **Cost-benefit analysis** — Quantify expected impact of each option
2. **Multi-criteria decision** — Evaluate across multiple dimensions
3. **Decision under uncertainty** — Handle uncertainty in impact estimates
4. **Premortem** — Challenge the decision before committing

## Reasoning Process

### Step 1: Define Options

**Option A: Improve onboarding**
- Redesign first-run experience
- Add interactive tutorial
- Estimated: 6 weeks, 3 engineers

**Option B: Add social features**
- Friend invites, activity sharing
- Estimated: 10 weeks, 4 engineers

**Option C: Improve performance**
- Reduce app startup time (currently 4s → target 1.5s)
- Reduce API latency
- Estimated: 8 weeks, 3 engineers

**Option D: Do nothing major** (baseline)
- Small improvements, bug fixes
- Used as comparison baseline

### Step 2: Cost-Benefit Analysis

| Option | Est. Retention Impact | Confidence | Engineering Cost | Risk |
|--------|----------------------|------------|-----------------|------|
| A: Onboarding | +15-25% | Medium (60%) | 6 weeks, 3 eng | Low |
| B: Social | +10-40% | Low (40%) | 10 weeks, 4 eng | High |
| C: Performance | +5-15% | High (80%) | 8 weeks, 3 eng | Low |
| D: Baseline | 0% | — | — | — |

**Key insight**: Option B has the highest potential upside but also the highest uncertainty and cost. Option A has the best expected value with moderate confidence. Option C is the safest bet.

### Step 3: Multi-Criteria Decision

**Criteria**:
- Expected retention impact (35%)
- Confidence in estimate (25%)
- Engineering feasibility (20%)
- Strategic alignment (10%)
- Speed to market (10%)

**Scores** (1-5):
| Criterion | A: Onboarding | B: Social | C: Performance |
|-----------|--------------|-----------|----------------|
| Retention impact | 4 | 4 | 3 |
| Confidence | 3 | 2 | 4 |
| Feasibility | 4 | 3 | 4 |
| Strategic alignment | 4 | 5 | 3 |
| Speed | 4 | 2 | 3 |

**Weighted scores**:
- A: 3.80
- B: 3.25
- C: 3.35

**Onboarding is the top choice on analysis.**

### Step 4: Decision Under Uncertainty

**Robustness check**: What if our estimates are wrong?

- If onboarding impact is at the low end (15%), it's still better than performance at the high end (15%)
- If social features are at the high end (40%), they'd be the best choice — but we're only 40% confident
- Performance is the most robust option (narrowest range, highest confidence)

**Minimax regret**: The maximum regret is highest for B (could invest 10 weeks for low impact), lowest for A.

### Step 5: Premortem

"Imagine it's 3 months from now. We chose onboarding. It failed. Why?"

- We redesigned onboarding but didn't test with real users during development
- The problem wasn't onboarding — users understood the app, they just didn't find ongoing value
- We should have invested in core engagement, not first-run experience
- We confused "users don't understand the app" with "users don't find the app valuable"

**This is a critical challenge to the onboarding hypothesis.**

### Step 6: Decision

Given the premortem challenge, we need more information before committing fully.

**Decision**: Run a 2-week experiment on onboarding before committing the full quarter:
1. Implement a lightweight onboarding improvement (1 week)
2. A/B test with 10% of new users (1 week)
3. If retention improves >10%, commit to full onboarding redesign
4. If not, pivot to performance improvements

**Confidence**: 70% that this approach is better than committing to any option now
**Key uncertainty**: Whether onboarding is actually the retention bottleneck
**What would change the decision**: A/B test results

## Verification

- [x] A/B test designed with clear success criteria
- [x] Small investment before large commitment
- [x] Premortem revealed a critical assumption (that onboarding is the bottleneck)
- [x] Decision is reversible after 2 weeks

## Result

The A/B test showed that onboarding improvements increased day-1 retention by 22% but had no effect on day-7 retention. The bottleneck wasn't onboarding — it was the core value proposition. The team pivoted to investigating why users churn after week 1, which revealed that the app lacked a "habit loop." The real investment should be in daily engagement features, not onboarding.

**The premortem was right.** The structured approach saved 2 months of engineering time.