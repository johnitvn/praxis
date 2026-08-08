# Router: Choose Depth

Determine how deeply to reason about a problem.

## Purpose

Not every problem requires deep reasoning. Match reasoning depth to problem stakes, complexity, and reversibility.

## Depth Levels

### Level 0: Intuitive / Pattern Match
- **When**: Routine problem, seen before, low stakes
- **What**: Recognize pattern, apply known solution
- **Time**: Seconds
- **Example**: "How do I format this date in Python?"

### Level 1: Quick Check
- **When**: Simple problem, low stakes, reversible
- **What**: Quick analysis, single method, basic verification
- **Time**: Under a minute of reasoning
- **Example**: "Should I use a list or a set for this?"

### Level 2: Structured Analysis
- **When**: Moderate complexity, medium stakes, somewhat reversible
- **What**: One or two methods, structured procedure, verification
- **Time**: Several minutes of reasoning
- **Example**: "Which library should we use for this feature?"

### Level 3: Deep Analysis
- **When**: Complex, high stakes, hard to reverse
- **What**: Multiple methods, composition, adversarial review, premortem
- **Time**: Extended reasoning
- **Example**: "What should our system architecture be?"

### Level 4: Exhaustive Analysis
- **When**: Critical, irreversible, safety-critical
- **What**: Full method chain, multiple independent analyses, adversarial review, formal verification where possible
- **Time**: As long as needed
- **Example**: "Is this cryptographic protocol secure?"

## Depth Selection Matrix

| Factor | Weight | Push Toward |
|--------|--------|-------------|
| Stakes | High | Deeper |
| Reversibility | Irreversible | Deeper |
| Complexity | High | Deeper |
| Uncertainty | High | Deeper |
| Time pressure | High | Shallower |
| Domain familiarity | Low | Deeper |
| Consequences of error | Severe | Deeper |
| Stakeholder count | Many | Deeper |

## Depth Escalation

Start at the appropriate depth. Escalate if:

1. **The answer matters more than you thought**: New information raises stakes
2. **The problem is harder than you thought**: Initial analysis reveals hidden complexity
3. **Methods disagree**: Parallel methods produce conflicting results
4. **Assumptions are challenged**: Key assumptions turn out to be uncertain
5. **Verification fails**: Results don't check out

## Depth De-escalation

Reduce depth if:

1. **The answer is obvious**: Further analysis won't change the conclusion
2. **The decision is more reversible than you thought**: You can undo
3. **Time is more critical than you thought**: Delay costs exceed error costs
4. **Diminishing returns**: Additional analysis isn't changing the answer

## Anti-Patterns

- **Analysis paralysis**: Staying at Level 3-4 when Level 1-2 would suffice
- **Shallow on critical**: Using Level 0-1 for high-stakes irreversible decisions
- **Depth creep**: Always escalating, never de-escalating
- **Uniform depth**: Using the same depth for every problem regardless of stakes