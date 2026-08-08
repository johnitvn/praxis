# Workflow: Troubleshoot

Rapidly identify and resolve operational issues in known systems.

## Purpose

Troubleshooting is the fast, systematic isolation of faults in systems you understand. It differs from diagnosis (which is broader and handles unknown causes) in that troubleshooting assumes a known system with known failure modes.

## When to Use

- A system is not working correctly
- The system is known and understood
- Fast resolution is important
- You can interact with the system to test hypotheses
- The failure mode is likely in a known set

## Workflow

### Phase 1: Triage

**Goal**: Quickly assess severity and scope.

1. **What is the impact?** Who or what is affected?
2. **Is it getting worse?** Escalating or stable?
3. **Is it safe to investigate?** Don't make things worse by poking
4. **Should you mitigate first?** Sometimes you stop the bleeding before diagnosing

**Methods**: Triage, impact assessment, risk assessment

### Phase 2: Reproduce

**Goal**: Observe the problem reliably.

1. **Can you reproduce the issue?** If not, it's much harder to troubleshoot
2. **What are the exact steps?** Minimal reproduction
3. **What is the expected behavior?** What should happen
4. **What is the actual behavior?** What actually happens
5. **Is it consistent or intermittent?** Intermittent problems are harder

**Methods**: Reproduction, observation, controlled testing

### Phase 3: Isolate

**Goal**: Narrow down where the fault is.

1. **What is the scope?** What is affected and what is NOT affected?
2. **Bisect**: Divide the system in half. Which half contains the fault?
3. **Check recent changes**: What changed recently?
4. **Check dependencies**: Are upstream/downstream systems working?

**Methods**: Bisection, binary search, differential diagnosis, temporal reasoning

### Phase 4: Hypothesize

**Goal**: Form a specific hypothesis about the cause.

1. **What could cause these symptoms?**
2. **What is the most likely cause?** (base rates matter)
3. **What is the fastest hypothesis to test?**
4. **What is the safest hypothesis to test?**

**Methods**: Abductive reasoning, pattern matching, causal reasoning

### Phase 5: Test

**Goal**: Test the hypothesis with minimal risk.

1. **What would confirm this hypothesis?**
2. **What would rule it out?**
3. **Can you test without affecting production?**
4. **Test the hypothesis**

**Methods**: Hypothesis testing, experimentation, controlled testing

### Phase 6: Fix

**Goal**: Apply the fix.

1. **What is the minimal fix?**
2. **What are the side effects of the fix?**
3. **Apply the fix**
4. **Verify the symptom is resolved**

**Methods**: Intervention, repair, minimal change

### Phase 7: Verify

**Goal**: Ensure the fix worked and didn't break anything.

1. **Is the original symptom resolved?**
2. **Are there any new symptoms?**
3. **Do related systems still work?**
4. **Monitor for recurrence**

**Methods**: Verification, regression testing, monitoring

### Phase 8: Prevent

**Goal**: Prevent recurrence if warranted.

1. **Why did this happen?** Root cause
2. **Could it happen again?** In this system or others
3. **What would prevent it?** Process, monitoring, design change
4. **Is prevention worth the cost?** Not every bug needs a process change

**Methods**: Root cause analysis, risk analysis, preventive action

## Common Failure Modes

- **Skipping reproduction**: Trying to fix without being able to reproduce
- **Assuming the cause**: Jumping to a conclusion without testing
- **Fixing symptoms, not causes**: Patching the symptom without understanding why
- **Not verifying the fix**: Assuming the fix worked
- **Changing too many things at once**: Can't tell what fixed it
- **Not checking recent changes**: Most failures follow changes
- **Blaming the usual suspect**: Assuming it's the same cause as last time