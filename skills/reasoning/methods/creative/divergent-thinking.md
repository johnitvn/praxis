# Divergent Thinking

## Purpose
Generate a large quantity of diverse ideas, options, or possibilities by suspending judgment and exploring broadly before narrowing.

## When to Use
- When the solution space has not been adequately explored and the first few ideas are likely to be conventional.
- When you are stuck on a problem and need to break out of a mental rut or fixation.
- When the problem is novel and there is no established solution path to follow.
- When you are at the ideation phase of a creative process and need raw material for later evaluation.
- When the user asks for "more options," "brainstorming," or "out-of-the-box ideas."

## When Not to Use
- When a single correct answer exists and can be derived through deductive or algorithmic reasoning.
- When time is extremely limited and a satisficing solution is acceptable.
- When the problem has already been adequately explored and the best options are identified.
- When the user is asking for evaluation, selection, or refinement — those are convergent-thinking tasks.

## Problem Signals
- "I can't think of any other way to do this."
- The first solution that comes to mind is the only one being considered.
- The user keeps returning to the same category of solution despite its flaws.
- "We need fresh ideas," "brainstorm," "think outside the box."
- A problem where the obvious approach has been tried and failed.

## Inputs
- A clear problem statement or design challenge.
- Any constraints that define the solution space (budget, time, physics, regulations).
- Knowledge of what has already been tried or considered.

## Procedure
1. State the problem clearly. A vague problem produces vague ideas. Frame it as "How might we..." or "In what ways could we..." to open the solution space.
2. Defer judgment. Explicitly suspend evaluation. The goal is quantity and diversity, not quality. Ideas that seem impractical or silly are welcome at this stage — they may trigger useful ideas later.
3. Generate ideas using one or more techniques:
   - **Quantity goal**: set a target number (e.g., 20 ideas) and do not stop until you reach it. The last 10 ideas will be more original than the first 10.
   - **Category stretching**: list the categories you have already considered (e.g., "technical solutions," "process changes"), then ask: what categories have I missed? Generate ideas from the missing categories.
   - **Provocation**: state an absurd or impossible version of a solution, then ask: what useful principle does this suggest? Example: "What if the product cost zero dollars?" leads to "What if we gave away the core and charged for add-ons?"
   - **Analogical transfer**: ask: how have other domains solved a structurally similar problem? What would a biologist do? A chef? A musician?
   - **Reversal**: ask: what would make the problem worse? Then invert each answer into a potential solution.
   - **Attribute listing**: list the attributes of the current solution, then vary each attribute one at a time. What if it were faster/slower, bigger/smaller, more/less connected?
   - **Random stimulus**: introduce a random word or image and force a connection to the problem. The constraint of finding a connection often produces novel ideas.
4. Record all ideas without filtering. An idea that seems unworkable may contain a kernel that becomes viable when combined with another idea.
5. When the flow of ideas slows, push further. The most original ideas often come after the obvious ones are exhausted.
6. Stop when you have generated a sufficient quantity and diversity of ideas that the solution space is well-covered. A good heuristic: at least 3 ideas from each of 3 different categories of approach.

## Output
- A list of ideas, options, or approaches, ideally organized by category of approach.
- A note of which ideas are most novel or surprising (without evaluating their quality).
- Raw material ready for convergent thinking.

## Strengths
- Generates quantity, which is the best predictor of quality in creative work.
- Breaks fixation on the first solution that comes to mind.
- Produces novel combinations by deferring judgment.
- Works well for problems with no established answer.

## Limitations
- Does not produce a finished solution — it produces raw material that requires evaluation, combination, and refinement.
- Quality is uneven; many ideas will be impractical. This is a feature, not a bug, but it means divergent thinking must be paired with convergent thinking.
- The output is only as good as the problem framing. A poorly framed problem produces a list of irrelevant ideas.

## Common Failure Modes
- **Premature evaluation**: the agent starts judging ideas during generation, filtering out unconventional ones before they can trigger useful associations. Fix: explicitly separate the generation and evaluation phases.
- **Shallow variation**: the agent generates many ideas that are minor variations of the same concept. Count how many distinct categories of approach are represented. If fewer than 3, the divergence is shallow.
- **Stopping too early**: the agent generates 5-7 ideas and stops, missing the more original ideas that come after the obvious ones are exhausted. Set a quantity target and hit it.
- **Generating without a problem**: producing a list of ideas that are creative but do not address the actual problem. Every idea must be traceable back to the problem statement.

## Verification
- Are there at least 15-20 ideas (or a quantity appropriate to the problem)?
- Do the ideas span at least 3 distinct categories of approach?
- Are there ideas that are genuinely surprising or non-obvious?
- Has judgment been deferred — is there no evaluation mixed into the generation?

## Combine With
- **convergent-thinking**: the natural partner. Divergent thinking generates options; convergent thinking selects among them.
- **lateral-thinking**: for the provocation and reframing techniques that break through impasses during divergence.
- **design-thinking**: divergent thinking is the ideation phase of the design-thinking process.
- **analogical-reasoning**: for the analogical transfer technique that generates cross-domain ideas.

## Conflicts With
- **convergent-thinking**: when applied simultaneously. Divergence and convergence are complementary but sequential — do not mix them.
- **deductive-reasoning**: when the problem has a single correct answer, divergent thinking is a waste of time.
- **satisficing**: divergent thinking aims for quantity and novelty; satisficing aims for "good enough." They serve different goals.

## Example

**Problem**: "How might we reduce the time customers spend waiting on hold for support?"

**Divergent generation** (quantity target: 20):

Category 1 — Reduce call volume:
1. Better self-service documentation
2. In-app contextual help
3. Proactive notifications before customers need to call
4. Community forum with peer support
5. AI chatbot for common questions
6. Video tutorials for common issues

Category 2 — Make wait time productive/pleasant:
7. Callback option instead of holding
8. Estimated wait time displayed upfront
9. Entertainment or education during hold (tips about the product)
10. Gamified hold experience that earns rewards
11. Let customers do other tasks and alert them when an agent is ready

Category 3 — Speed up resolution:
12. Pre-collect information before connecting to agent
13. Route to specialized agents by issue type
14. Give agents better tools to reduce average handle time
15. AI-assisted agent responses (suggested replies)
16. Empower agents to resolve without escalation

Category 4 — Eliminate the call entirely:
17. In-product issue resolution that fixes problems automatically
18. Predictive support: detect issues before the customer notices
19. Design the product so support calls are unnecessary
20. Async messaging instead of synchronous calls

**Novel/surprising ideas**: #10 (gamified hold), #18 (predictive support), #19 (design away support need).

## Selection Metadata
```
id: divergent-thinking
category: creative
best_for: [idea generation, option exploration, breaking mental sets, novel problems]
requires: [problem statement, suspension of judgment, generation techniques]
produces: [many ideas, novel options, categorized raw material]
strengths: [generates quantity, breaks fixation, produces novel combinations]
limitations: [quality varies, requires subsequent filtering, output depends on problem framing]
combine_with: [convergent-thinking, lateral-thinking, design-thinking, analogical-reasoning]
avoid_when: [single correct answer exists, time is extremely limited, problem is already well-explored]
```