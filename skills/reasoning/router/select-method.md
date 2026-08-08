# Router: Method Selection

Select the appropriate reasoning method(s) given a problem classification.

## Purpose

Given a classified problem, select the reasoning method or methods that are most appropriate. Support single-method, multi-method, and chained selections.

## Procedure

### Step 1: Match Classification to Methods

Use the classification from `classify-problem.md` and consult `ontology/methods.yaml` to identify candidate methods.

Key matching criteria:
- `best_for` — does the method's best-for list match the problem type?
- `requires` — does the agent have the required inputs?
- `avoid_when` — does the problem trigger any avoid conditions?

### Step 2: Filter by Constraints

| Constraint | Filter |
|-----------|--------|
| Time pressure | Prefer satisficing, fast methods; avoid multi-stage methods |
| Missing data | Prefer methods that handle uncertainty; avoid methods requiring precise inputs |
| High stakes | Require verification methods; prefer methods with explicit uncertainty |
| Irreversible | Require adversarial review; add premortem |
| Novel domain | Prefer first-principles, creative; avoid methods requiring reference classes |

### Step 3: Select Method Count

| Situation | Approach |
|-----------|---------|
| Simple, well-defined problem | Single method |
| Multi-faceted problem | Multiple methods in parallel |
| Sequential reasoning needed | Method chain (ordered) |
| High uncertainty | Iterative loop (apply → check → refine) |
| Novel problem | Explore with multiple methods, then converge |

### Step 4: Check for Method Conflicts

Consult `ontology/relationships.yaml` for known conflicts between selected methods.

If methods conflict:
1. Identify which method's assumptions match the problem better
2. Use the primary method; note the conflict
3. Or: use the methods sequentially, in different phases

### Step 5: Select Substitution if Needed

If the primary method requires inputs the agent doesn't have, consult `ontology/relationships.yaml` for substitutions.

## Decision Tree

```
Problem classified
│
├─ Simple + well-defined
│   └─ Single method
│
├─ Complex + multi-faceted
│   ├─ Independent facets
│   │   └─ Parallel methods
│   └─ Dependent facets
│       └─ Method chain
│
├─ High uncertainty
│   └─ Iterative loop
│       ├─ Apply method
│       ├─ Check result
│       ├─ Refine
│       └─ Repeat until stable
│
├─ High stakes
│   └─ Method chain + adversarial review
│       ├─ Primary method
│       ├─ Alternative method (different perspective)
│       ├─ Compare results
│       └─ Premortem
│
└─ Novel / ill-defined
    └─ Explore → Converge
        ├─ Divergent phase (multiple methods)
        ├─ Compare insights
        └─ Convergent phase (best method)
```

## Escalation

If the selected method proves insufficient:
1. Add complementary methods (see `combine_with` in method metadata)
2. Escalate to a more powerful method (see `relationships.yaml` escalation paths)
3. Add verification methods
4. Consider whether the problem was misclassified

## Output

A method selection plan:
- **primary_methods**: [list of method ids]
- **composition**: [single | parallel | chain | loop | explore-converge]
- **sequence** (if chain): [ordered list]
- **verification_methods**: [list]
- **rationale**: why these methods were selected
- **fallback**: what to do if insufficient