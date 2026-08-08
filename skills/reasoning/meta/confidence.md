# Confidence Calibration

Ensure your stated confidence matches your actual accuracy.

## Purpose

Calibration is the alignment between confidence and accuracy. A well-calibrated reasoner is right ~X% of the time when they say they are X% confident.

## Why Calibration Matters

- **Overconfidence** → Bad decisions, ignored risks, missed verification
- **Underconfidence** → Analysis paralysis, missed opportunities, unnecessary verification
- **Good calibration** → Appropriate depth, correct risk assessment, efficient reasoning

## Calibration Assessment

### Self-Test Questions

1. When I say "I'm 90% confident," how often am I actually right?
2. When I say "I'm 50% confident," do I acknowledge I'm essentially guessing?
3. Can I distinguish between 60%, 80%, and 95% confidence?
4. Do I ever say "I'm 100% confident"? (If so, you're almost certainly miscalibrated)

### Calibration Levels

| Confidence | Meaning | Appropriate Use |
|-----------|---------|-----------------|
| >99% | Essentially certain | Mathematical proof, logical necessity |
| 95% | Very confident | Strong evidence, multiple confirming sources |
| 90% | Confident | Good evidence, some uncertainty |
| 80% | Moderately confident | Reasonable evidence, significant uncertainty |
| 60-70% | Weakly confident | Limited evidence, high uncertainty |
| 50% | Guessing | No useful evidence either way |
| <50% | Likely wrong | Evidence points against |

## Improving Calibration

### 1. Track Your Accuracy
- When you make a prediction, record your confidence
- When the outcome is known, compare
- Look for systematic overconfidence or underconfidence

### 2. Use Reference Classes
- Don't just think about this specific case
- Ask: "In similar situations, how often am I right?"
- The outside view is usually better calibrated than the inside view

### 3. Decompose and Recombine
- Break complex judgments into components
- Assess confidence in each component
- Combine using probability rules
- This usually produces better-calibrated overall judgments

### 4. Seek Disconfirming Evidence
- Actively look for reasons you might be wrong
- Adjust confidence downward when you find none (yes, downward — if you can't find counterarguments, you're probably not looking hard enough)

### 5. Use Verbal-Numerical Mapping

| Verbal | Numerical |
|--------|-----------|
| "Certain" | >99% |
| "Almost certain" | 95-99% |
| "Very likely" | 85-95% |
| "Likely" | 70-85% |
| "Probably" | 60-70% |
| "More likely than not" | 50-60% |
| "Uncertain" | 40-60% |
| "Unlikely" | 15-30% |
| "Very unlikely" | 5-15% |
| "Almost impossible" | 1-5% |
| "Impossible" | <1% |

## Common Failure Modes

- **100% confidence**: Almost always wrong. Reserve for mathematical truths.
- **Hedge words as calibration**: "I think maybe probably..." without numerical confidence
- **Confidence without track record**: Stating confidence without any basis for calibration
- **Overconfidence on extremes**: Being too confident about very unlikely or very likely events
- **Underconfidence on moderate**: Being too uncertain about moderate-probability events
- **Confidence inflation**: Raising stated confidence because "I'm an AI, I should be confident"