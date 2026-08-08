# Workflow: Diagnose

Systematically identify the cause of an observed problem.

## Purpose

Diagnosis is the process of identifying the cause of observed symptoms. This workflow is applicable to system failures, bugs, medical problems, performance issues, and any situation where something is wrong and the cause is unknown.

## When to Use

- Something is not working as expected
- The cause is not obvious
- Multiple possible causes exist
- The problem may recur if the root cause is not found
- Fixing the symptom is not sufficient

## Workflow

### Phase 1: Observe

**Goal**: Understand what is happening.

1. **Characterize the symptom**: What exactly is wrong?
2. **Determine scope**: What is affected? What is NOT affected?
3. **Establish timeline**: When did it start? Is it constant or intermittent?
4. **Collect data**: Logs, metrics, error messages, observations

**Methods**: Evidence gathering, observation

### Phase 2: Define the Problem

**Goal**: State the problem precisely.

1. **What is the expected behavior?**
2. **What is the actual behavior?**
3. **What is the gap between them?**
4. **What changed recently?**

**Methods**: Problem framing, constraint analysis

### Phase 3: Generate Hypotheses

**Goal**: List possible explanations.

1. **Brainstorm possible causes**: What could explain the symptoms?
2. **Consult known failure modes**: What typically causes this?
3. **Consider recent changes**: What changed that could have caused this?
4. **Consider external factors**: Environment, dependencies, load

**Methods**: Abductive reasoning, divergent thinking, causal reasoning

### Phase 4: Rank Hypotheses

**Goal**: Prioritize which hypotheses to investigate first.

1. **Rate by likelihood**: Which is most probable given the evidence?
2. **Rate by impact**: Which would be most severe if true?
3. **Rate by testability**: Which is easiest to test?
4. **Prioritize**: Highest likelihood × impact × testability first

**Methods**: Bayesian reasoning, risk analysis

### Phase 5: Gather Discriminating Evidence

**Goal**: Find evidence that distinguishes between hypotheses.

1. **Design tests**: What would confirm or rule out each hypothesis?
2. **Gather evidence**: Run tests, collect data, inspect state
3. **Document findings**: What did you learn?

**Methods**: Hypothesis testing, experimentation, evidence evaluation

### Phase 6: Test and Eliminate

**Goal**: Rule out hypotheses until one remains.

1. **Test the highest-priority hypothesis**
2. **If confirmed**: Move to Phase 7
3. **If ruled out**: Eliminate it, return to Phase 5 with remaining hypotheses
4. **If uncertain**: Refine the test, or deprioritize

**Methods**: Falsification, Bayesian updating

### Phase 7: Confirm

**Goal**: Verify the identified cause.

1. **Can you reproduce the problem by triggering the cause?**
2. **Does fixing the cause resolve the symptom?**
3. **Are there any other symptoms explained by this cause?**
4. **Could there be multiple causes?**

**Methods**: Verification, causal reasoning

### Phase 8: Verify Intervention

**Goal**: Ensure the fix works and doesn't break anything else.

1. **Apply the fix**
2. **Verify the symptom is resolved**
3. **Check for side effects**
4. **Monitor for recurrence**

**Methods**: Verification, regression testing

## Common Failure Modes

- **Premature closure**: Stopping at the first plausible hypothesis
- **Confirmation bias**: Seeking evidence for a preferred hypothesis
- **Base rate neglect**: Ignoring how common different causes are
- **Single-cause assumption**: Assuming there's only one cause
- **Not verifying the fix**: Assuming the fix worked because it should
- **Fixing symptoms**: Addressing the symptom, not the root cause