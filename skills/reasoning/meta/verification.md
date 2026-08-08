# Verification

Verify that reasoning and conclusions are correct.

## Purpose

Verification is the process of checking whether reasoning is sound and conclusions are correct. It is distinct from self-critique (which looks for flaws) — verification confirms correctness.

## Verification vs. Validation

- **Verification**: "Did we reason correctly?" (process check)
- **Validation**: "Did we reach the right conclusion?" (outcome check)

Both are necessary. Verification checks the reasoning; validation checks the result.

## Verification Levels

### Level 1: Sanity Check
Quick plausibility check.
- Does the result make sense?
- Is it in the right order of magnitude?
- Does it pass basic consistency checks?

### Level 2: Independent Recalculation
Re-derive from scratch, ideally using a different method.
- Can you reach the same conclusion a different way?
- If you re-do the key calculation, do you get the same result?

### Level 3: Cross-Validation
Check against external benchmarks.
- Do other sources agree?
- Does this match historical patterns?
- Would an expert in this domain agree?

### Level 4: Adversarial Testing
Actively try to break the conclusion.
- What would make this wrong?
- Can you construct a counterexample?
- Does it hold in edge cases?

### Level 5: Empirical Test
Test against reality where possible.
- Can you run an experiment?
- Can you check against data?
- Can you observe the outcome?

## Procedure

### Step 1: Identify What to Verify

Not everything needs equal verification. Focus on:
- The most uncertain steps
- The highest-impact conclusions
- The steps where errors would be most costly
- The steps where the method is most error-prone

### Step 2: Select Verification Level

Match verification level to stakes:
- Low stakes: Level 1 (sanity check)
- Medium stakes: Level 2-3
- High stakes: Level 3-4
- Critical: Level 4-5

### Step 3: Apply Verification

Execute the verification at the selected level. If verification fails:
- Identify where the error is
- Correct it
- Re-verify from that point forward

### Step 4: Document Verification

- What was verified?
- How was it verified?
- What was the result?
- What was NOT verified and why?

## Verification Checklist

- [ ] Result is plausible (sanity check)
- [ ] Result is internally consistent
- [ ] Key calculations have been checked
- [ ] Edge cases have been considered
- [ ] Alternative methods produce similar results
- [ ] External sources/benchmarks agree (where available)
- [ ] The conclusion would survive adversarial challenge
- [ ] Remaining uncertainty is documented

## Common Failure Modes

- **Verification theater**: Going through the motions without genuine checking
- **Selective verification**: Only verifying steps that are likely to pass
- **Method-external verification gap**: Verifying the process but not the result
- **Over-verification**: Spending more time verifying than the verification is worth
- **Verification blindness**: Not seeing errors because you're using the same flawed method to verify