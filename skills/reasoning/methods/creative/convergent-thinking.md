# Convergent Thinking

## Purpose
Evaluate, filter, and select among a set of options to identify the best solution according to defined criteria, combining ideas where appropriate to produce a refined result.

## When to Use
- When you have a set of candidate solutions, ideas, or options and need to choose the best one.
- When you need to evaluate whether an idea meets constraints, requirements, or success criteria.
- When you are at the refinement phase of a creative process, after divergent thinking has produced raw material.
- When the user asks for "the best option," "evaluation," "prioritization," or "narrowing down."
- When you need to combine multiple partial ideas into a coherent solution.

## When Not to Use
- When the solution space has not been adequately explored. Convergent thinking before divergent thinking produces conventional, narrow results.
- When the criteria for evaluation are unclear or undefined.
- When the user is asking for more options, not fewer.
- When the problem is simple enough that the best answer is obvious without formal evaluation.

## Problem Signals
- "We have too many options and can't decide."
- "Which of these ideas is actually the best?"
- "We need to narrow this down to the top 3."
- The user presents a list of ideas and asks for a recommendation.
- A decision needs to be made and the options are known but unranked.

## Inputs
- A set of candidate options, ideas, or solutions.
- Explicit evaluation criteria: what makes one option better than another?
- Constraints: what must be true of any viable solution?
- Priorities or weights for the criteria (if multiple criteria apply).

## Procedure
1. Define evaluation criteria. Criteria must be explicit and, where possible, measurable. Ask: "What would make one option better than another?" Common criteria include: feasibility, cost, time to implement, likely impact, risk, alignment with goals, scalability, novelty.
2. Weight the criteria if they are not equally important. State the weights explicitly: "impact is twice as important as cost."
3. Screen for viability. Apply hard constraints first. Eliminate any option that fails a must-have requirement. This is a binary filter, not a judgment call.
4. Apply the primary criterion. Sort remaining options by the most important criterion. Identify the top tier.
5. Apply secondary criteria. Within the top tier, use the next most important criterion to differentiate. Continue until the options are ranked or a clear winner emerges.
6. Test for combination. Before finalizing, ask: can the strengths of two or more options be combined into a hybrid that is better than any individual option? Do not force this — only combine if the combination genuinely improves on the parts.
7. Pressure-test the selection. For the top option(s), ask: what would have to be true for this to fail? What assumptions am I making? What is the weakest part of this option?
8. State the recommendation. Name the selected option(s) and justify the choice by reference to the criteria. Be explicit about the trade-offs: what is being sacrificed and why it is acceptable.

## Output
- A ranked list of options with scores or assessments against the stated criteria.
- A recommended option with justification.
- An explicit statement of trade-offs: what is gained and what is sacrificed.
- Any hybrid or combined options that emerged during the process.

## Strengths
- Provides a systematic, transparent basis for selection.
- Makes criteria and trade-offs explicit rather than implicit.
- Screens out non-viable options efficiently.
- Can combine the strengths of multiple ideas into a better solution.

## Limitations
- The quality of the output depends entirely on the quality of the criteria. Poorly chosen criteria produce poor selections.
- Convergent thinking can prematurely eliminate unconventional ideas that are actually strong but don't fit the criteria well.
- Criteria weighting is subjective. Different weights produce different rankings.
- A systematic process can create an illusion of objectivity when the inputs are subjective.

## Common Failure Modes
- **Converging too early**: applying convergent thinking before the solution space has been adequately explored. The result is a conventional choice from a narrow set.
- **Criteria without justification**: listing criteria without explaining why they are the right criteria for this problem. "Feasibility" is not always the most important thing.
- **False precision**: assigning numerical scores to subjective judgments to create an appearance of rigor. A 7 vs. an 8 on "innovation potential" is meaningless unless the scale is defined.
- **Anchoring on the first strong option**: once a promising option is identified, evaluating subsequent options against it rather than against the criteria.
- **Ignoring the null option**: failing to consider "do nothing" or "status quo" as a legitimate option. Sometimes the best choice is no change.

## Verification
- Are the evaluation criteria explicitly stated and justified?
- Are the criteria applied consistently to all options?
- Is the recommendation justified by reference to the criteria, not by intuition?
- Are the trade-offs explicit?
- Was the combination step attempted (not forced, but considered)?

## Combine With
- **divergent-thinking**: the natural partner. Divergent thinking generates options; convergent thinking selects among them.
- **multi-criteria-decision**: for formal multi-criteria analysis when the decision involves many weighted criteria.
- **trade-off-analysis**: for deeper analysis of the trade-offs between top options.
- **decision-under-uncertainty**: when the criteria are clear but the outcomes of each option are uncertain.
- **design-thinking**: convergent thinking is the selection phase of the design-thinking process.

## Conflicts With
- **divergent-thinking**: when applied simultaneously. They are sequential phases, not parallel processes.
- **satisficing**: convergent thinking aims for the best option; satisficing stops at the first satisfactory one. They serve different goals.
- **lateral-thinking**: lateral thinking deliberately violates the criteria to find breakthroughs. Convergent thinking enforces the criteria. They are complementary in sequence but conflict if applied simultaneously.

## Example

**Problem**: Select the best approach to reduce customer wait time, given 20 options generated during divergent thinking.

**Criteria** (weighted):
1. Impact on wait time (40%) — how much reduction is expected?
2. Implementation speed (30%) — can we do it this quarter?
3. Cost (20%) — what is the required investment?
4. Customer experience improvement (10%) — does it make the experience better, not just shorter?

**Hard constraints**: Must be implementable within 6 months. Must not require hiring more than 3 people.

**Screening**: Eliminate options requiring new product architecture (#19 design away support need — exceeds 6 months), options requiring major new hires.

**Top tier by impact**: Callback option (#7), AI chatbot (#5), pre-collect information (#12), predictive support (#18).

**Differentiation by secondary criteria**: Callback (#7) is fastest to implement (existing phone system supports it) and lowest cost. Predictive support (#18) has highest impact but highest implementation complexity. AI chatbot (#5) has good impact but moderate implementation time.

**Combination**: Callback (#7) + pre-collect information (#12) is a natural combination: when the customer requests a callback, the system can collect issue details at the same time, reducing the agent's handle time when they call back.

**Recommendation**: Implement callback with pre-collected information (#7 + #12 hybrid) as the immediate solution. Begin scoping predictive support (#18) as the medium-term play.

**Trade-offs**: We sacrifice the highest-potential impact (predictive support) for speed and certainty. The callback hybrid is a known quantity with predictable results.

## Selection Metadata
```
id: convergent-thinking
category: creative
best_for: [selecting among options, evaluation, refinement, prioritization]
requires: [candidate solutions, evaluation criteria, constraints]
produces: [selected solution, ranked options, trade-off analysis]
strengths: [systematic selection, quality filtering, transparent criteria, enables combination]
limitations: [criteria-dependent, may miss unconventional solutions, subjective weighting]
combine_with: [divergent-thinking, multi-criteria-decision, trade-off-analysis, decision-under-uncertainty, design-thinking]
avoid_when: [criteria are unclear, solution space is unexplored, the problem is simple]
```