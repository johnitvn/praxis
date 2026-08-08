# Router: Choose Next Step

After applying a reasoning method, determine what to do next.

## Purpose

Reasoning is not a single pass. After each step, decide: continue reasoning, change approach, gather information, or stop.

## Decision States

### State 1: Continue
The current method is producing useful results. Continue applying it.

**Signals**:
- Results are converging
- Uncertainty is decreasing
- New insights are still emerging
- The method hasn't exhausted its value

### State 2: Switch Method
The current method is insufficient. Switch to a different method.

**Signals**:
- Results are not converging
- Method assumptions are violated
- The problem has changed
- The method's limitations are blocking progress

**Action**: Return to `select-method.md` with updated problem understanding.

### State 3: Compose
The current method needs to be combined with another.

**Signals**:
- The problem has aspects the current method doesn't address
- Results from this method reveal a need for another perspective
- The method's output is incomplete without another method's input

**Action**: Use `compose-methods.md` to add a method.

### State 4: Escalate Depth
The current depth is insufficient.

**Signals**:
- Stakes are higher than initially assessed
- Results are surprising or concerning
- Assumptions are more uncertain than expected

**Action**: Use `choose-depth.md` to increase depth.

### State 5: Gather Information
The current method needs information the agent doesn't have.

**Signals**:
- Key inputs are missing
- Assumptions need validation
- Uncertainty is epistemic (can be reduced)
- The method requires external data

**Action**: Use `meta/when-to-search.md`, `meta/when-to-ask.md`, or `meta/when-to-experiment.md`.

### State 6: Verify
The method has produced a result. Verify it.

**Signals**:
- A conclusion has been reached
- A decision has been made
- A plan has been formed

**Action**: Use `meta/verification.md`, `meta/self-critique.md`, `meta/consistency-check.md`.

### State 7: Stop
Reasoning is complete. No further analysis is needed.

**Signals**:
- The question is answered with sufficient confidence
- Further analysis won't change the conclusion
- The cost of further reasoning exceeds the benefit
- The decision is made and is being acted upon

**Action**: Report the result with confidence level and remaining uncertainty.

## Next-Step Decision Flow

```
After each reasoning step:
│
├─ Result is clear and confident?
│   ├─ Yes → Verify → Stop
│   └─ No → Continue
│
├─ Current method is still productive?
│   ├─ Yes → Continue
│   └─ No → Switch or Compose
│
├─ Missing critical information?
│   ├─ Yes → Gather Information
│   └─ No → Continue reasoning
│
├─ Stakes higher than expected?
│   ├─ Yes → Escalate Depth
│   └─ No → Continue at current depth
│
└─ Further reasoning would help?
    ├─ Yes → Continue
    └─ No → Stop (report with uncertainty)
```

## Anti-Patterns

- **Infinite loop**: Continuing without making progress
- **Premature stop**: Stopping before reaching sufficient confidence
- **Method lock-in**: Sticking with a failing method too long
- **Information hoarding**: Gathering more information than needed
- **Verification skipping**: Moving to the next step without verifying the current one