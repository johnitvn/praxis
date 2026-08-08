# When to Delegate

Decide when to delegate reasoning or action to another agent, process, or person.

## Purpose

Delegation is recognizing that someone or something else is better positioned to handle a task. Effective delegation multiplies capability; ineffective delegation creates confusion and overhead.

## When to Delegate

### Delegate When:
- Another agent has domain expertise you lack
- The task is parallelizable and you're the coordinator
- The task requires specialized tools you don't have
- The task is well-defined and the delegate is competent
- The user has explicitly asked you to delegate
- The task benefits from independent perspective
- The task is too large for a single agent

## When NOT to Delegate

### Don't Delegate When:
- The task requires your specific context or judgment
- The coordination cost exceeds the benefit
- The delegate is not competent for the task
- The task is trivial (delegation overhead > task cost)
- The user expects you to do it personally
- You're delegating to avoid responsibility
- The task requires synthesis across multiple delegated results

## Delegation Patterns

### 1. Independent Parallel
Delegate independent subtasks to multiple agents simultaneously.

**When**: Subtasks don't depend on each other
**Risk**: Integration complexity; inconsistent approaches

### 2. Sequential Handoff
Agent A completes work, hands to Agent B.

**When**: Tasks have clear sequential dependencies
**Risk**: Bottlenecks; context loss at handoffs

### 3. Adversarial Review
Delegate the same task to independent agents and compare.

**When**: High stakes, verification is important
**Risk**: Higher cost; resolution of disagreements

### 4. Specialist Consultation
Delegate specific subtasks to domain specialists.

**When**: Task requires diverse expertise
**Risk**: Integration of specialist outputs

## Delegation Quality

### Good Delegation:
- **Clear scope**: What exactly should the delegate do?
- **Clear output**: What should they produce?
- **Clear constraints**: What are the boundaries?
- **Clear context**: What do they need to know?
- **Clear deadline**: When is it needed?

### Bad Delegation:
- **Vague scope**: "Look into this"
- **No output spec**: Delegate doesn't know what success looks like
- **Hidden constraints**: Delegate discovers constraints late
- **Missing context**: Delegate lacks necessary background
- **No deadline**: No urgency or priority signal

## The Delegation Decision

```
Could this task be done better or faster by someone/something else?
│
├─ No → Do it yourself
└─ Yes → Is the task well-defined enough to delegate?
    ├─ No → Define it better, then delegate
    └─ Yes → Is the coordination cost < benefit?
        ├─ No → Do it yourself
        └─ Yes → DELEGATE
            ├─ Provide clear scope, output, constraints, context
            ├─ Monitor progress (not micromanage)
            └─ Integrate results when done
```