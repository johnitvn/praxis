# Information Gathering

Strategy for acquiring missing information needed for reasoning.

## Purpose

When reasoning requires information the agent doesn't have, it must decide whether and how to acquire it. Not all information gaps need to be filled — some are not worth the cost.

## Information Value Assessment

### Step 1: Identify Information Gaps

For each gap, ask:
- What specific information is missing?
- How would it affect the reasoning if known?
- What decision or conclusion does it bear on?

### Step 2: Assess Value of Information

The value of information is the expected improvement in decision quality from having it.

**High value**: Information that could change the decision or conclusion
**Low value**: Information that would not change anything
**Zero value**: Information that is interesting but irrelevant

### Step 3: Assess Cost of Acquisition

| Acquisition Method | Cost | When Appropriate |
|-------------------|------|-----------------|
| Search (existing sources) | Low | Information is publicly available |
| Ask (user/stakeholder) | Medium | Information is held by someone accessible |
| Experiment (generate data) | High | Information doesn't exist yet |
| Compute (analyze existing data) | Medium | Raw data exists but needs processing |

### Step 4: Decide

If value > cost → acquire
If value < cost → proceed without it (note the gap)
If value is uncertain → start with the cheapest acquisition method

## Information Gathering Strategy

### 1. Progressive Disclosure

Start with the cheapest, fastest methods. Escalate only if needed.

```
Search existing sources
    │
    ├─ Found? → Use it
    └─ Not found? → Ask
        │
        ├─ Answered? → Use it
        └─ Not answered? → Experiment or compute
            │
            ├─ Feasible? → Do it
            └─ Not feasible? → Proceed with uncertainty
```

### 2. Parallel Gathering

When multiple independent information gaps exist, gather in parallel.

### 3. Just-in-Time Gathering

Don't gather information until it's needed. The answer may become unnecessary, or other information may fill the gap.

### 4. Sufficiency, Not Completeness

You don't need all possible information. You need enough to make a sound decision with appropriate confidence.

## Information Quality Assessment

When you acquire information, assess its quality:
- **Source credibility**: How reliable is the source?
- **Recency**: Is the information current?
- **Relevance**: Does it actually address the gap?
- **Precision**: Is it precise enough for the decision?
- **Bias**: Could the source be biased?

## Common Failure Modes

- **Information hoarding**: Gathering far more information than needed
- **Information avoidance**: Not gathering information that might challenge your view
- **Analysis without information**: Reasoning extensively on assumptions instead of gathering facts
- **Perfect information fallacy**: Waiting for perfect information that will never arrive
- **Source neglect**: Not evaluating the quality of information sources