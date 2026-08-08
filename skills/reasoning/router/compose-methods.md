# Router: Method Composition

Compose multiple reasoning methods into coherent chains, loops, or parallel applications.

## Purpose

When a single method is insufficient, compose methods deliberately. Composition is not random combination — it follows structural patterns.

## Composition Patterns

### 1. Chain (Sequential)

One method's output becomes the next method's input.

```
Method A → Method B → Method C → Result
```

**When to use**:
- Each step depends on the previous step's output
- The problem has a natural progression (frame → analyze → decide)
- The methods address different aspects of the same problem

**Example**: Architecture Decision
```
Constraint Analysis → Systems Thinking → Trade-off Analysis → Risk Analysis → Premortem → Decision
```

**Anti-pattern**: Chaining methods that don't pass meaningful output between them.

### 2. Parallel (Independent)

Multiple methods applied independently to the same problem, results compared.

```
         ┌→ Method A ─┐
Problem ─┼→ Method B ─┼→ Compare → Synthesize
         └→ Method C ─┘
```

**When to use**:
- Methods provide different perspectives on the same problem
- No method depends on another's output
- You want triangulation or robustness

**Example**: Evaluating a claim
```
         ┌→ Argument Analysis ─┐
Claim ───┼→ Evidence Evaluation ─┼→ Compare → Confidence Assessment
         └→ Source Credibility ─┘
```

**Anti-pattern**: Running methods in parallel when one depends on another's output.

### 3. Loop (Iterative)

Apply, check, refine, repeat until stable.

```
┌─────────────────────────┐
│                         ▼
│  Apply Method → Check → Sufficient? ──No──→ Refine
│                         │
└─────────────────────────┘
                          Yes
                          │
                          ▼
                        Result
```

**When to use**:
- High uncertainty
- Progressive refinement
- Learning from intermediate results

**Example**: Bayesian Updating
```
Prior → Observe Evidence → Update Posterior → More Evidence? → Yes → Update again
                                                                   → No → Final Posterior
```

**Anti-pattern**: Looping without a clear stopping criterion.

### 4. Explore-Converge (Divergent then Convergent)

```
Problem → Divergent Phase (broad) → Convergent Phase (narrow) → Result
```

**When to use**:
- Novel problems
- Ill-defined problems
- Creative solutions needed

**Example**: Design Problem
```
Problem → Divergent Thinking (generate many ideas) → Convergent Thinking (filter, evaluate) → Trade-off Analysis → Selection
```

**Anti-pattern**: Converging too early (premature closure).

### 5. Escalation Chain

Start simple, escalate if insufficient.

```
Simple Method → Insufficient? → Medium Method → Insufficient? → Full Method Chain
```

**When to use**:
- Cost of reasoning matters
- Problem complexity is uncertain
- Quick answer may be sufficient

**Example**: Problem Solving
```
Satisficing → not adequate? → Structured Analysis → still uncertain? → Adversarial Review
```

**Anti-pattern**: Always starting with the most complex method.

## Composition Rules

1. **No redundant methods**: Each method in a composition should add distinct value.
2. **No conflicting assumptions**: Check `relationships.yaml` for conflicts.
3. **Explicit handoffs**: Each method's output should be a valid input to the next.
4. **Verification at boundaries**: Verify at method transitions, not just at the end.
5. **Document the composition**: Why these methods, in this order.

## Composition Anti-Patterns

| Anti-Pattern | Description | Fix |
|-------------|-------------|-----|
| Kitchen sink | Using too many methods | Remove redundant methods |
| Single method for everything | Using one method for all problems | Match method to problem |
| Unordered pile | Methods without structure | Add explicit composition pattern |
| Missing verification | No method to check results | Add verification step |
| Premature convergence | Converging before exploring | Extend divergent phase |
| Analysis paralysis | Never converging | Set stopping criteria |
| Fake composition | Methods that don't actually interact | Ensure handoffs are meaningful |

## Verification

After composing methods, verify:
1. Does each method contribute something the others don't?
2. Are the handoffs between methods valid?
3. Are there any conflicting assumptions?
4. Is there a verification step?
5. Is there a clear stopping criterion?