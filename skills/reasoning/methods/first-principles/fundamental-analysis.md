# Fundamental Analysis

## Purpose
Reason from the most basic, irreducible truths of a domain — stripping away assumptions, analogies, and conventions — to build understanding or solutions from the ground up.

## When to Use
- When existing solutions are inadequate and incremental improvement is not enough
- When you need to challenge inherited assumptions that may no longer be valid
- When the domain is novel and there are no established reference solutions
- When you suspect that conventional wisdom is wrong or limiting
- When you need to innovate and existing approaches are converging on local optima
- When the cost of a wrong assumption is high and you need to verify foundations

## When Not to Use
- When speed is critical and existing solutions are adequate — fundamental analysis is slow
- When the domain's fundamentals are well-understood and the problem is a standard application
- When you lack the deep domain expertise required to identify what is truly fundamental
- When the problem is routine and the cost of re-deriving from first principles exceeds the benefit

## Problem Signals
- The user says "we've always done it this way" without knowing why
- The problem involves multiple conflicting assumptions
- Existing solutions are plateaued or diminishing returns have set in
- The user describes the problem as "we need to rethink this from scratch"
- The problem is in a new domain with no established best practices

## Inputs
- The domain or system under analysis
- A willingness to question every assumption, including ones that "everyone knows"
- Access to foundational knowledge: physical laws, axioms, empirical invariants, or definitional truths
- The current state of the art (to understand what assumptions it relies on)

## Procedure

### Step 1: State the Objective
Define what you are trying to understand or achieve, stripped of any solution-specific language. For example, not "we need a better engine" but "we need to convert stored energy into motion."

### Step 2: Identify All Assumptions
List every assumption embedded in the current understanding or approach. Include:
- Explicit assumptions (stated in documentation)
- Implicit assumptions (things taken for granted)
- Historical assumptions (conditions that were true when the approach was developed but may have changed)
- Domain assumptions (constraints that are specific to the current solution, not the problem)

### Step 3: Identify the Fundamentals
For each assumption, ask: "Is this a fundamental truth, or is it a choice?" A fundamental truth is:
- A physical law that cannot be violated
- A logical axiom in a formal system
- A definitional constraint (what the words mean)
- A verified empirical invariant (a pattern that has held across all available observations)

Everything else is a choice, a convention, or an unverified belief.

### Step 4: Rebuild from Fundamentals
Starting from the identified fundamentals:
1. What is possible? What does the fundamental truth permit?
2. What is impossible? What does it rule out?
3. What is unknown? What lies between the possible and the impossible?

### Step 5: Derive Implications
From the fundamentals, derive what follows logically. Do not skip steps. Each conclusion must be traceable back to a fundamental truth or a previously derived conclusion.

### Step 6: Compare to Current Understanding
Identify where the derived conclusions differ from the current understanding. Each difference is a place where an assumption was unnecessarily constraining the solution space.

### Step 7: Generate New Approaches
Using the derived understanding, generate approaches that are consistent with the fundamentals but not constrained by the abandoned assumptions.

## Output
- A list of identified fundamentals (the axioms of the domain)
- A list of abandoned assumptions and why they were not fundamental
- Derived conclusions traceable to fundamentals
- New approaches that are consistent with the fundamentals
- A comparison showing where the new understanding differs from the old

## Strengths
- Escapes local optima: bypasses the accumulated assumptions that constrain incremental improvement
- Enables radical innovation: the space of solutions consistent with fundamentals is often larger than the space of conventional solutions
- Robust: conclusions are grounded in truths that do not change, not in conventions that may become obsolete
- Transferable: the fundamentals of one domain often illuminate another

## Limitations
- Time-intensive: questioning everything takes time, and most assumptions will turn out to be valid
- May rediscover known results: the path from fundamentals to a solution may arrive at the same place as conventional wisdom
- Requires deep expertise: identifying what is truly fundamental requires domain mastery
- The "fundamentals" may not be as fundamental as you think: what appears fundamental may itself rest on deeper assumptions

## Common Failure Modes
- **Stopping too early**: accepting a conventional assumption as fundamental because it is widely held. The most dangerous assumptions are the ones that "everyone knows."
- **Going too deep**: questioning axioms that are definitional and cannot be productively questioned. "What is a customer?" may be useful. "What is a number?" usually is not.
- **Missing implicit assumptions**: the assumptions you do not know you are making are the ones that constrain you most. Use external perspectives or adversarial review to surface them.
- **Rebuilding without fundamentals**: claiming to reason from first principles while actually jumping to a new set of assumptions. Trace every conclusion back to a fundamental.
- **Ignoring constraints that are real**: some constraints are not fundamental truths but are nevertheless binding in practice (regulations, physics, economics). Do not discard them.

## Verification
- For each identified fundamental, ask: "Could this be false?" If yes, it is not fundamental — dig deeper.
- For each derived conclusion, trace the chain of reasoning back to a fundamental. If there is a gap, an assumption is hiding.
- Test the new approaches against edge cases and adversarial scenarios. Do they hold up where the old approaches failed?
- Have an expert review the fundamentals list. Are there missing fundamentals? Are any listed fundamentals actually assumptions?

## Combine With
- **Decomposition**: to break the domain into components before analyzing each fundamentally
- **Assumption Checking**: to systematically surface and challenge assumptions
- **Deductive Reasoning**: to derive implications from fundamentals with logical rigor
- **Systems Thinking**: to understand how fundamentals interact across system boundaries
- **Analogical Reasoning**: to identify assumptions by comparing the domain to a different one

## Conflicts With
- **Analogical Reasoning**: when used as a substitute for fundamental analysis. Reasoning by analogy can import assumptions from the source domain. Use analogies only after fundamentals are established.
- **Conventional Methods**: when they encode assumptions that fundamental analysis would challenge. Use fundamental analysis first, then apply conventional methods if they are consistent with the fundamentals.

## Example
Objective: Reduce the cost of space launch.

Current assumption: rockets must be single-use because the stresses of launch and re-entry make reuse impractical.

Fundamental analysis:
- Fundamental: physics requires ~9.4 km/s of delta-v to reach low Earth orbit. The rocket equation relates mass ratio to exhaust velocity. These are physical laws.
- Assumption challenged: "rockets must be single-use." Is this fundamental? No — it is an engineering choice, not a physical law. The physics permits reusability if the vehicle can be recovered and refurbished.
- Rebuild: what is required for reusability? Controlled descent, thermal protection, structural integrity for multiple flights, refurbishment economics.
- Implication: if the cost of recovery and refurbishment is less than the cost of building a new rocket, reuse is economically viable.

Result: SpaceX demonstrated that reusable rockets are not only possible but economically superior, reducing launch costs by an order of magnitude. The assumption was not fundamental — it was a convention that had persisted because no one had successfully challenged it.

## Selection Metadata
```
id: fundamental-analysis
category: first-principles
best_for: [challenging assumptions, innovation, deep understanding]
requires: [domain, willingness to question everything]
produces: [foundational truths]
strengths: [bypasses inherited assumptions, enables radical innovation]
limitations: [time-intensive, may rediscover known results]
combine_with: [decomposition, assumption-checking, deductive-reasoning, systems-thinking, analogical-reasoning]
avoid_when: [speed is critical, existing solutions are adequate]
```