# Design Thinking

## Purpose
Solve ill-defined, human-centered problems through an iterative process of empathy, definition, ideation, prototyping, and testing that keeps the user's needs at the center of every phase.

## When to Use
- When the problem is human-centered: the solution will be used by, consumed by, or experienced by people, and their needs and behaviors are not fully understood.
- When the problem is ill-defined or "wicked": the problem statement itself is unclear and must be discovered through exploration.
- When innovation is the goal and incremental improvement of an existing solution is insufficient.
- When the user's experience, emotions, and context are as important as the technical functionality.
- When you need to bridge the gap between what users say they want and what they actually need.

## When Not to Use
- When the problem is purely technical and human factors are irrelevant (e.g., optimizing a database query).
- When the user population is inaccessible for research or testing.
- When the solution is already well-defined and the task is implementation, not discovery.
- When time is extremely constrained and the full iterative cycle cannot be completed.

## Problem Signals
- "Our users are unhappy and we don't know why."
- "We built what they asked for, but they don't use it."
- A problem statement that is vague: "improve the customer experience," "make it more intuitive."
- The user describes a problem in terms of symptoms but cannot articulate the underlying need.
- Multiple stakeholders describe the problem differently, suggesting it is not well-defined.

## Inputs
- A problem area or opportunity space (may be initially vague).
- Access to information about users: their context, behaviors, goals, pain points, and current workarounds.
- The scope of the solution space: what is in bounds and what is out of bounds.
- Stakeholder perspectives: who cares about the problem and why.

## Procedure
1. **Empathize**: Understand the user's experience from their perspective, not yours.
   - Gather information about users: what do they do? What do they say? What do they think? What do they feel?
   - Identify pain points: where do they struggle? What workarounds have they created?
   - Identify goals: what are they trying to accomplish? What does success look like to them?
   - Look for the gap between what users say and what they do.
   - If you cannot observe users directly, construct personas based on available information and state your assumptions explicitly.

2. **Define**: Synthesize empathy findings into a clear, actionable problem statement.
   - Identify patterns and themes in the user research.
   - Frame the problem in human terms: "[User] needs [need] because [insight]."
   - Distinguish between symptoms and root causes.
   - Define what success looks like from the user's perspective.
   - State the problem in a way that invites solutions: "How might we...?"

3. **Ideate**: Generate a wide range of potential solutions.
   - Apply divergent thinking to explore the solution space broadly.
   - Defer judgment during ideation.
   - Generate ideas across multiple categories of approach.
   - Include both incremental improvements and radical reimaginings.
   - Prioritize ideas that directly address the defined user need.

4. **Prototype**: Create a low-fidelity representation of the top ideas to make them tangible and testable.
   - A prototype can be a description, a sketch, a wireframe, a storyboard, a role-play scenario, or a process flow.
   - The goal is to make the idea concrete enough to get feedback, not to build a finished product.
   - Prototype multiple ideas, not just the favorite.
   - Keep prototypes low-cost: the purpose is to learn, not to impress.

5. **Test**: Gather feedback on the prototypes from the user's perspective.
   - Present the prototype to users (or simulate their perspective if direct access is unavailable).
   - Ask: does this solve the problem? What is confusing? What is missing? What would you change?
   - Look for surprises: what did users react to that you did not expect?
   - Identify what to keep, what to change, and what to discard.

6. **Iterate**: Use test feedback to refine the problem definition, generate new ideas, or improve the prototype.
   - Design thinking is not linear. You may loop back to any previous phase:
     - If users did not understand the problem the way you defined it, return to Define.
     - If the prototype revealed a need you had not considered, return to Empathize.
     - If the test showed the idea is promising but needs refinement, return to Ideate or Prototype.
   - Continue iterating until the solution meets the user need or until time runs out.
   - On each iteration, note what you learned and how it changed your understanding.

## Output
- A user-centered problem definition: "[User] needs [need] because [insight]."
- A set of prototyped solutions, each with user feedback.
- A recommended solution with justification grounded in user needs.
- A record of what was learned through iteration and how the understanding evolved.

## Strengths
- Keeps the user's actual needs at the center of the process, not the builder's assumptions.
- Iterative structure catches misunderstandings early, before large investments are made.
- Handles ill-defined problems by treating problem definition as part of the process.
- Bridges the gap between what users say they want and what they actually need.

## Limitations
- Time-intensive: the full cycle requires multiple iterations, each of which takes time.
- Requires access to users or user data for empathy and testing. Without user input, the process becomes guesswork dressed up as design thinking.
- Can be misused as a superficial process: going through the motions of empathy and prototyping without genuine engagement with users.
- The iterative, non-linear nature can be uncomfortable for stakeholders who expect a linear plan with predictable outcomes.

## Common Failure Modes
- **Empathy theater**: claiming to empathize with users without actually engaging with their experience. The agent describes what it imagines users feel, presenting imagination as research.
- **Skipping to solution**: jumping directly to ideation without doing the empathy and define phases. The result is a solution to a problem the agent invented, not the user's actual problem.
- **Fake iteration**: going through the cycle once and declaring it complete. Design thinking is iterative by design — one pass is not enough.
- **Prototyping the finished product**: spending too much effort on the prototype, making it too polished, and becoming attached to it. The prototype should be just good enough to get feedback, not a near-final version.
- **User as validator**: using the test phase to confirm the idea rather than to learn from it. The test should be a search for problems, not a search for approval.

## Verification
- Is there a user-centered problem statement in the format "[User] needs [need] because [insight]"?
- Were multiple ideas prototyped, not just one?
- Was user feedback gathered (or simulated with explicit assumptions stated)?
- Did the process iterate at least once based on feedback?
- Are the assumptions about users explicitly stated and acknowledged as assumptions?

## Combine With
- **divergent-thinking**: for the ideation phase.
- **convergent-thinking**: for the selection and refinement phases.
- **lateral-thinking**: for reframing the problem during the define phase.
- **systems-thinking**: when the user's experience is shaped by a larger system that must be understood.
- **first-principles reasoning**: for challenging assumptions about what users need.

## Conflicts With
- **waterfall approaches**: defining all requirements upfront and building to specification. Design thinking assumes you will discover requirements through iteration.
- **purely technical problem-solving**: when the problem can be solved without understanding human behavior or experience.
- **optimization**: design thinking is about discovering what to build, not optimizing an existing solution. It is a divergent-and-convergent process, not a hill-climbing one.

## Example

**Problem**: A hospital wants to improve the patient experience in the emergency department. Patients report high stress and confusion.

**Empathize** (findings):
- Patients arrive in pain or distress and are immediately confronted with paperwork.
- They do not know how long they will wait, who they will see, or what will happen next.
- The environment is noisy, bright, and impersonal.
- Patients feel they have no control or information.
- Staff are rushed and communicate in medical jargon.

**Define**: "Emergency department patients need to feel informed and in control of their experience because the loss of agency and information amplifies the stress of the medical situation itself."

**Ideate** (selected ideas):
1. A digital display showing each patient's position in the queue and estimated wait time.
2. A "patient navigator" role — a non-clinical staff member who greets patients and explains what to expect.
3. Redesign the physical space to provide visual privacy and noise reduction.
4. A simple card given at triage: "Here is what will happen next, in order."

**Prototype**: For the lowest-cost, highest-impact test, prototype #4: a simple card with a 4-step visual timeline of the ED process, with estimated times for each step. The card uses plain language and icons.

**Test**: Present the card design to 10 patients. Findings: 8 of 10 said it reduced their anxiety. 2 said they wanted more specific time estimates. Several asked for the card to include space to write questions for the doctor.

**Iterate**: Add a "Questions for the doctor" section to the card. Return to ideate: the card is effective but low-tech. The digital display (#1) could complement it. Prototype both together.

**Recommendation**: Deploy the card immediately. Pilot the digital display in one ED pod. The core insight — that information reduces stress — applies to both.

## Selection Metadata
```
id: design-thinking
category: creative
best_for: [human-centered problems, ill-defined problems, innovation, user experience design]
requires: [empathy, user research, iteration, prototyping]
produces: [human-centered solutions, user insights, validated prototypes]
strengths: [user-focused, iterative refinement, handles ill-defined problems, bridges say-do gap]
limitations: [time-intensive, requires user access, can be superficial without genuine engagement]
combine_with: [divergent-thinking, convergent-thinking, lateral-thinking, systems-thinking, first-principles reasoning]
avoid_when: [problem is purely technical, users are inaccessible, solution is already well-defined]
```