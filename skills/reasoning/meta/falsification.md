# Falsification

Actively attempt to disprove your own conclusions.

## Purpose

Falsification is the strongest form of verification. Instead of looking for confirmation, you actively try to prove yourself wrong. A conclusion that survives genuine falsification attempts is far more robust than one that has merely been "confirmed."

## The Falsification Principle

> The strength of a conclusion is measured not by the evidence that supports it, but by the severity of the tests it has survived.

## Falsification vs. Verification

- **Verification** asks: "Is this correct?"
- **Falsification** asks: "How could I prove this wrong?"

Verification looks for confirming evidence. Falsification looks for disconfirming evidence. Falsification is generally stronger because a single counterexample can disprove a claim, while no amount of confirming evidence proves it.

## Procedure

### Step 1: State the Claim Precisely

A claim must be falsifiable — there must be some conceivable observation that would show it to be false.

**Not falsifiable**: "This architecture is good."
**Falsifiable**: "This architecture will handle 10k concurrent users with p99 latency under 100ms."

### Step 2: Identify Falsification Conditions

For each claim, ask: "What observation would prove this wrong?"

If you cannot identify any possible observation that would prove it wrong, the claim is unfalsifiable — which means you cannot meaningfully verify it.

### Step 3: Search for Falsifying Evidence

Actively look for evidence that would falsify the claim:
- Are there counterexamples?
- Does the claim fail in edge cases?
- Does it make predictions that can be tested?
- Has it been falsified in similar contexts?

### Step 4: Attempt Refutation

Try to construct a refutation:
- What's the strongest argument against this claim?
- If I were debating against this conclusion, what would I say?
- What would an intelligent critic point out?

### Step 5: Assess Survival

After falsification attempts:
- Did the claim survive? (If yes, it's stronger)
- Did it partially fail? (If yes, it needs refinement)
- Did it completely fail? (If yes, reject it)

## Severity of Test

Not all falsification attempts are equal. A "severe test" is one that:
- Would be very likely to find an error if one exists
- Tests the claim's most uncertain elements
- Tests the claim's boundary conditions
- Uses independent evidence or methods

## Falsification Checklist

- [ ] The claim is stated in falsifiable terms
- [ ] I have identified what would falsify the claim
- [ ] I have searched for counterexamples
- [ ] I have tested edge cases
- [ ] I have constructed the strongest argument against the claim
- [ ] The claim has survived severe tests (not just weak ones)
- [ ] I can state what additional evidence would falsify it

## Common Failure Modes

- **Unfalsifiable claims**: Making claims too vague to be falsified
- **Weak tests**: Only testing against easy challenges
- **Confirmation masquerading as falsification**: "Trying" to falsify but not really
- **Falsification avoidance**: Avoiding falsification because it's uncomfortable
- **Survivorship bias**: Only reporting claims that survived falsification
- **Moving the target**: Changing the claim when it's falsified instead of accepting falsification