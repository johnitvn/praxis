# Systems Thinking

## Purpose
Map the structure of an interconnected system to identify leverage points, feedback loops, and emergent behaviors that component-level reasoning would miss.

## When to Use
- When the problem involves multiple interacting parts whose collective behavior is not obvious from the parts alone.
- When a solution directed at one part keeps failing because the system compensates elsewhere.
- When you are asked to explain why a system resists change or produces counterintuitive outcomes.
- When the problem spans organizational boundaries, time horizons, or disciplinary silos.
- When root causes are not local to a single component but reside in the structure of relationships.

## When Not to Use
- When the problem is genuinely isolated to a single component with no feedback to the rest of the system.
- When the system is simple enough that a linear causal chain suffices.
- When the cost of mapping the system exceeds the cost of the problem itself.

## Problem Signals
- A problem that has been "solved" repeatedly but keeps returning.
- Interventions that work in the short term but worsen the situation over time.
- "Side effects" that are as large as the intended effect.
- A problem described as "complex," "messy," or "wicked."
- The user describes multiple actors or departments whose actions affect each other.

## Inputs
- A description of the system boundary (what is in and what is out).
- A list of components or actors.
- The relationships, flows, or dependencies between components.
- The time horizon of interest.

## Procedure
1. Define the system boundary. State explicitly what is inside the system and what is outside. This is a choice, not a fact — justify it.
2. Catalog the components. List every actor, stock, process, or entity inside the boundary.
3. Map the relationships. For each pair of components, identify: Does A influence B? Is the influence direct or indirect? Is it positive (reinforcing) or negative (balancing)? How strong is the link? Are there delays?
4. Identify feedback loops. Trace closed cycles in the relationship map. Label each loop as reinforcing (amplifies change) or balancing (resists change, seeks equilibrium).
5. Locate leverage points. For each loop, ask: where would a small change produce a large shift in system behavior? Classic leverage points include: changing the rules of the system, altering information flows, modifying goals, shifting the paradigm.
6. Test the map. For each major observed behavior of the system, verify that the map can explain it. If the map cannot explain a known behavior, it is incomplete.
7. State what the map reveals. Articulate the structural reason the system behaves as it does.

## Output
- A system map (described in text or structure) showing components, relationships, feedback loops, and delays.
- A list of leverage points ranked by estimated impact.
- An explanation of the system's dominant behavior in structural terms.
- A prediction: if we intervene at lever X, the system should respond with Y, after adjusting for delays.

## Strengths
- Reveals why obvious solutions fail and where high-leverage interventions actually lie.
- Integrates information across boundaries that component-level analysis treats as separate.
- Explains counterintuitive behavior (policy resistance, worse-before-better, shifting the burden).

## Limitations
- The boundary is a subjective choice; different boundaries produce different maps and different conclusions.
- A map is not the system; every model omits detail that might matter.
- Systems thinking is descriptive, not prescriptive — it tells you what to change, but not how to implement the change in a specific organizational context.

## Common Failure Modes
- **Infinite scope creep**: the agent keeps adding components and relationships until the map is unmanageably large. Fix: define the boundary at the start and hold it.
- **Map without leverage**: the agent produces a thorough map but never identifies actionable leverage points. The output becomes an academic exercise.
- **Confusing correlation with causal connection**: the agent draws a link between A and B because they covary, without establishing that A influences B.
- **Ignoring delays**: the agent treats all relationships as instantaneous, missing the dynamic behavior that delays create.

## Verification
- Can the map explain the system's observed behavior, including the behaviors that prompted the analysis?
- Are the leverage points ranked, and is the ranking justified?
- Does the analysis identify at least one feedback loop?
- Are delays explicitly noted where they matter?

## Combine With
- **feedback-analysis**: for deeper analysis of the loops identified in the systems map.
- **causal-graph-reasoning**: for formalizing causal relationships within the system.
- **decomposition**: for breaking down complex components before mapping.
- **design-thinking**: when the system includes human users whose behavior shapes the system.

## Conflicts With
- **reductionist analysis**: breaking the system into independent parts and analyzing each in isolation — the opposite of systems thinking.
- **linear causal chains**: assuming A causes B causes C without feedback.

## Example

**Problem**: A company's product quality keeps declining despite repeated quality initiatives.

**System map**:
- Components: Engineering team, QA team, Product Management, Customers, Support tickets, Feature backlog, Technical debt.
- Key loop (reinforcing): Feature pressure -> rushed releases -> more bugs -> higher support load -> less time for quality -> more technical debt -> slower development -> more feature pressure.
- Key loop (balancing): Quality initiative -> temporary QA headcount -> catches more bugs -> quality improves -> initiative declared success -> QA headcount removed -> quality declines.

**Leverage points**: (1) Change the goal from "features shipped" to "reliability over time" — paradigm shift. (2) Make technical debt visible to Product Management — information flow change. (3) Cap work-in-progress to reduce context-switching — rule change.

## Selection Metadata
```
id: systems-thinking
category: systems
best_for: [interconnected problems, emergent behavior, long-term dynamics, policy resistance]
requires: [system boundary, components, relationships, time horizon]
produces: [system map, leverage points, structural explanation, behavioral prediction]
strengths: [reveals counterintuitive behavior, identifies high-leverage interventions, integrates across boundaries]
limitations: [boundary is subjective, model is not the system, descriptive not prescriptive]
combine_with: [feedback-analysis, causal-graph-reasoning, decomposition, design-thinking]
avoid_when: [problem is isolated, system is simple, mapping cost exceeds problem cost]
```