# Router: Stopping Criteria

Know when to stop reasoning.

## Purpose

Reasoning has diminishing returns. Knowing when to stop is as important as knowing how to reason.

## Stopping Criteria

### Criterion 1: Sufficient Confidence
The agent's confidence in the conclusion meets the required threshold for the stakes.

| Stakes | Minimum Confidence |
|--------|-------------------|
| Low, reversible | >60% |
| Medium | >80% |
| High, somewhat reversible | >90% |
| Critical, irreversible | >95% + adversarial review |

### Criterion 2: Convergent Stability
Additional reasoning is not changing the conclusion.

**Test**: If you did one more round of reasoning, would the answer change?
- If no → stop
- If maybe → do one more round
- If yes → continue

### Criterion 3: Diminishing Returns
The cost of further reasoning exceeds the expected value of a better answer.

**Test**: Compare:
- Cost of more reasoning (time, effort, delay)
- Expected improvement in decision quality × value of better decision

If cost > expected improvement, stop.

### Criterion 4: Actionable Threshold
The answer is good enough to act on.

**Test**: Can you act on this conclusion now?
- If yes → stop and act
- If no → continue reasoning or gather information

### Criterion 5: Information Ceiling
No additional information is available that would change the conclusion.

**Test**: What information would change your mind?
- If nothing → stop (you've reached the information ceiling)
- If something → can you get it? If not → stop (note the uncertainty)

### Criterion 6: Time Constraint
A deadline requires action now.

**Test**: Is the cost of delay greater than the cost of being wrong?
- If yes → stop, act, note uncertainty
- If no → continue if other criteria are not met

## Stopping Anti-Patterns

| Anti-Pattern | Description |
|-------------|-------------|
| Analysis paralysis | Never stopping, always "one more analysis" |
| Premature closure | Stopping at the first plausible answer |
| False precision | Continuing to add decimal places that don't matter |
| Certainty seeking | Continuing because you want certainty, not because it's achievable |
| Deadline denial | Ignoring time constraints because "this is important" |
| Perfectionism | Not stopping because the answer isn't perfect |

## Stopping Checklist

Before stopping, verify:

- [ ] I can state my conclusion clearly
- [ ] I can state my confidence level
- [ ] I can state what would change my mind
- [ ] I can state the key remaining uncertainties
- [ ] I have verified the reasoning (not just the conclusion)
- [ ] I have considered at least one alternative
- [ ] I have checked for common biases
- [ ] The depth matches the stakes
- [ ] Further reasoning would not materially change the conclusion
- [ ] I can act on this conclusion