# Workflow: Optimize

Improve an existing system or solution against defined objectives.

## Purpose

Optimization is the process of making something better along one or more dimensions. Unlike design (which creates new solutions), optimization improves existing ones.

## When to Use

- You have an existing solution that needs improvement
- The objectives are measurable and quantifiable
- There are constraints on what can be changed
- The improvement is worth the cost of optimization
- You can measure whether the optimization worked

## Workflow

### Phase 1: Define Objectives

**Goal**: Establish what "better" means.

1. **What are you optimizing for?** Speed, cost, quality, reliability, something else?
2. **Are there multiple objectives?** If so, how do they trade off?
3. **What is the current baseline?** Measure it
4. **What would "good enough" look like?** Set aspiration levels

**Methods**: Objective definition, multi-objective optimization, satisficing

### Phase 2: Identify Constraints

**Goal**: Define what cannot be changed or violated.

1. **What are the hard constraints?** (must not violate)
2. **What are the soft constraints?** (prefer not to violate)
3. **What are the resource constraints?** (budget, time, effort)
4. **What are the technical constraints?** (physics, architecture, compatibility)

**Methods**: Constraint analysis

### Phase 3: Measure Current State

**Goal**: Establish a quantitative baseline.

1. **Measure current performance** on all objectives
2. **Identify bottlenecks**: Where is the system constrained?
3. **Profile**: Where is time/resources being spent?
4. **Document the baseline**: You need to know if you improved

**Methods**: Measurement, profiling, bottleneck analysis

### Phase 4: Identify Improvement Opportunities

**Goal**: Find where improvements can be made.

1. **Where are the biggest gaps?** Between current and desired
2. **What are the leverage points?** Small changes with big effects
3. **What are others doing?** Benchmarking
4. **What are the low-hanging fruit?** Easy wins

**Methods**: Gap analysis, systems thinking, benchmarking

### Phase 5: Generate and Evaluate Options

**Goal**: Create and assess improvement options.

1. **Generate improvement options** for each opportunity
2. **Estimate impact** of each option
3. **Estimate cost** of each option
4. **Rank by ROI**: Impact per unit cost

**Methods**: Divergent thinking, cost-benefit analysis, trade-off analysis

### Phase 6: Implement

**Goal**: Apply the selected improvements.

1. **Prioritize**: Start with highest ROI
2. **Implement incrementally**: One change at a time when possible
3. **Measure after each change**: Did it improve things?
4. **Be prepared to revert**: If an improvement makes things worse

**Methods**: Implementation, A/B testing, incremental change

### Phase 7: Verify

**Goal**: Confirm the improvement worked.

1. **Measure post-change performance**
2. **Compare to baseline**: Did it improve?
3. **Check for side effects**: Did anything else change?
4. **Is the improvement statistically significant or practically meaningful?**

**Methods**: Verification, statistical testing, before/after comparison

### Phase 8: Iterate

**Goal**: Continue improving until objectives are met or diminishing returns set in.

1. **Are objectives met?**
2. **Is further improvement possible?**
3. **Is further improvement worth the cost?**
4. **If yes, return to Phase 4**

**Methods**: Stopping criteria, iterative optimization

## Common Failure Modes

- **Optimizing the wrong thing**: Improving a metric that doesn't matter
- **Premature optimization**: Optimizing before understanding the system
- **Local optimum**: Getting stuck in a local optimum, missing the global one
- **Over-optimization**: Optimizing past the point of diminishing returns
- **Not measuring baseline**: You can't know if you improved without a baseline
- **Optimizing one dimension at the expense of all others**: The "whack-a-mole" problem
- **Optimizing without constraints**: Producing solutions that can't be implemented