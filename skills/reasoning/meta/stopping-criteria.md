# Stopping Criteria

Know when to stop reasoning.

## Purpose

Reasoning has diminishing returns. The value of additional reasoning eventually falls below its cost. Knowing when to stop is an essential meta-cognitive skill.

## Stopping Triggers

### 1. Sufficient Confidence
The agent's confidence meets the threshold required by the stakes.

### 2. Convergent Stability
Additional reasoning is not changing the conclusion. If one more round produces the same answer, stop.

### 3. Diminishing Returns
The expected improvement from more reasoning is less than the cost of that reasoning.

### 4. Information Ceiling
No additional information is available that would change the conclusion.

### 5. Time Constraint
A deadline requires action. The cost of delay exceeds the cost of potential error.

### 6. Actionable Threshold
The answer is good enough to act on, even if not perfect.

## Stopping Questions

Before stopping, ask:

1. **Can I state my conclusion clearly?** If not, continue reasoning.
2. **Can I state my confidence level?** If not, you don't understand your uncertainty.
3. **Can I state what would change my mind?** If not, you haven't thought about falsification.
4. **Can I state the key remaining uncertainties?** If not, you're not being honest about what you don't know.
5. **Have I verified the reasoning?** Not just the conclusion — the process.
6. **Have I considered at least one alternative?** If not, you may be missing something.
7. **Would more reasoning change the answer?** If yes, continue. If no, stop.
8. **Is the cost of delay greater than the cost of being wrong?** If yes, stop and act.

## Stopping Anti-Patterns

| Anti-Pattern | Description |
|-------------|-------------|
| **Analysis paralysis** | Never stopping, always "one more analysis" |
| **Premature closure** | Stopping at the first plausible answer |
| **Perfectionism** | Not stopping because the answer isn't perfect |
| **False precision** | Continuing to add decimal places that don't matter |
| **Certainty seeking** | Continuing because you want certainty, not because it's achievable |
| **Deadline denial** | Ignoring time constraints because "this is important" |

## The Stopping Decision

```
After each reasoning step:
│
├─ Can I act on this conclusion?
│   ├─ Yes → Is more reasoning likely to change the action?
│   │   ├─ No → STOP
│   │   └─ Yes → Continue
│   └─ No → Continue
│
├─ Has confidence stopped improving?
│   ├─ Yes → STOP (document uncertainty)
│   └─ No → Continue
│
├─ Is there a binding deadline?
│   ├─ Yes → STOP (act with current best answer)
│   └─ No → Continue
│
└─ Would more information change the answer?
    ├─ No → STOP
    └─ Yes → Can I get it?
        ├─ Yes → Gather information, then decide
        └─ No → STOP (document the information gap)
```