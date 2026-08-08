# Argument Analysis

## Purpose
Systematically evaluate the structure, strength, and validity of an argument by identifying its components (premises, warrant, claim), testing the logical connection between them, and assessing whether the conclusion follows from the stated reasons.

## When to Use
- When evaluating a claim made by someone else (a report, a proposal, a debate opponent)
- When constructing your own argument and want to ensure it is logically sound before presenting it
- When an argument is complex and its validity is not obvious from a surface reading
- When the argument relies on implicit assumptions that need to be surfaced and examined

## When Not to Use
- When the argument is purely empirical and can be settled by checking the data directly
- When the claim is trivial and the cost of analysis exceeds the value of the conclusion
- When the argument is not yet explicit — the arguer is still forming their position and needs exploration, not evaluation
- When the domain is purely formal (mathematics, logic) where formal proof methods are more appropriate

## Problem Signals
- The user says "they claim X, but is that actually valid?"
- The user is presented with a persuasive argument and wants to know whether to trust it
- The user is constructing an argument and wants to test its soundness before presenting it
- The user describes a disagreement where both sides seem to have plausible arguments

## Inputs
- An explicit argument: a claim supported by stated reasons (premises)
- The context in which the argument is made (who is making it, to whom, for what purpose)
- Domain knowledge to assess the truth of factual premises

## Procedure
1. **Identify the claim.** What is the arguer trying to establish? State it in a single sentence. If the argument has multiple claims, identify the main conclusion and treat supporting claims as premises to be analyzed.
2. **Extract explicit premises.** List every reason the arguer provides in support of the claim. Quote directly if possible. Number each premise for reference.
3. **Identify the warrant.** The warrant is the logical bridge that connects the premises to the claim. It is often implicit. Ask: "if these premises are true, why does the claim follow?" Common warrants: generalization (what is true of the sample is true of the population), analogy (what is true of A is true of similar B), causation (A caused B, so A will cause B again), authority (the expert says X, so X is true).
4. **Surface implicit premises.** What unstated assumptions must be true for the argument to work? Every argument has them. List them explicitly. The most common implicit premise is "the warrant applies in this case."
5. **Test premise truth.** For each premise (explicit and implicit), assess whether it is true. For factual premises: check against evidence. For definitional premises: check for consistency. For normative premises: check for value alignment with the audience.
6. **Test logical validity.** Assume all premises are true. Does the claim necessarily follow? If yes, the argument is valid. If no, the argument is invalid — there is a logical gap. Identify the gap.
7. **Test soundness.** An argument is sound if it is valid AND all its premises are true. An argument can be valid but unsound (logical structure is correct but a premise is false). An argument can be invalid but have a true conclusion (the arguer is right for the wrong reasons).
8. **Assess overall strength.** Consider: (a) soundness (valid + true premises), (b) relevance (premises actually support the claim, not a different claim), (c) sufficiency (premises provide enough support for the strength of the claim), (d) resilience (the argument survives obvious objections).

## Output
- The argument's structure: claim, explicit premises, implicit premises, warrant
- Premise-by-premise truth assessment
- Validity assessment: does the claim follow from the premises?
- Soundness assessment: valid AND all premises true?
- Overall strength rating with rationale

## Strengths
- Makes the structure of an argument visible, enabling precise critique
- Surfaces implicit assumptions that are often the weak point of an argument
- Distinguishes between logical validity and factual truth, which are often conflated
- Provides a systematic alternative to "I agree/disagree" reactions

## Limitations
- Requires the argument to be explicit; real-world arguments are often vague, incomplete, or shifting
- The identification of implicit premises is subjective and can be contested
- Does not address rhetorical effectiveness — a logically weak argument can still persuade
- The truth of premises may depend on disputed evidence or values, making soundness assessment inconclusive

## Common Failure Modes
- **Straw-man analysis**: analyzing a weaker version of the argument than the arguer intended, then declaring it invalid
- **Premise nitpicking**: rejecting an argument because a minor premise is imprecise, while ignoring that the core reasoning is sound
- **Warrant blindness**: failing to identify the warrant and treating the argument as a simple list of premises, which misses the logical structure
- **Soundness conflation**: treating an invalid argument as "false" (the conclusion might still be true) or a valid argument as "true" (the premises might be false)
- **Implicit premise inflation**: inventing implausible implicit premises to make the argument look weaker than it is

## Verification
- Have the claim, premises, and warrant been stated explicitly and clearly?
- Have implicit premises been identified and are they plausible interpretations of the arguer's intent?
- Has validity been assessed separately from premise truth?
- Does the overall strength rating reflect both logical structure and factual accuracy?

## Combine With
- evidence-evaluation for assessing the quality of evidence supporting factual premises
- fallacy-detection for identifying specific logical errors in the argument's structure
- dialectic for testing the argument against its strongest counter-argument
- deductive-reasoning (from logical category) for formal validity testing

## Conflicts With
- Approaches that evaluate arguments by their conclusions rather than their structure
- Rhetorical analysis that focuses on persuasiveness rather than logical validity

## Example
**Argument**: "We should not deploy on Fridays because last month's Friday deployment caused a weekend outage, and the team was unable to respond quickly."

**Claim**: We should not deploy on Fridays.

**Explicit premises**:
P1: Last month's Friday deployment caused a weekend outage.
P2: The team was unable to respond quickly to the weekend outage.

**Warrant**: Past incidents predict future incidents (generalization). If a deployment practice caused a problem in the past, it will cause problems in the future.

**Implicit premises**:
IP1: Last month's deployment is representative of all Friday deployments.
IP2: The outage was caused by deploying on Friday, not by the specific change that was deployed.
IP3: The team's response capability is the same on all weekends.
IP4: The cost of not deploying on Fridays (delayed releases) is less than the cost of a potential weekend outage.

**Truth assessment**:
P1: True (verifiable incident record).
P2: True (incident report confirms slow response).
IP1: Questionable — one data point is not representative. Other Friday deployments may have succeeded.
IP2: Questionable — the outage was likely caused by the specific change, not the day of the week.
IP3: True (the team is consistently smaller on weekends).
IP4: Unverified — the cost of delayed deployments has not been quantified.

**Validity**: If all premises are true, the claim follows (the argument is valid). The warrant is a straightforward generalization.

**Soundness**: Not sound. IP1 and IP2 are questionable. The argument conflates correlation (Friday deployment) with causation (the specific change).

**Overall strength**: Weak. The argument identifies a real risk but overgeneralizes from a single incident. A stronger argument would address: what specifically about the deployment caused the outage, and whether that specific cause can be mitigated without a blanket ban on Friday deployments.

## Selection Metadata
```
id: argument-analysis
category: argumentation
best_for: [evaluating claims, detecting fallacies, structured debate]
requires: [claim, premises, warrant]
produces: [argument strength, fallacy identification]
strengths: [systematic, fallacy-aware]
limitations: [requires explicit argument, implicit premises]
combine_with: [evidence-evaluation, deductive-reasoning]
avoid_when: [argument is not explicit, domain is purely empirical]
```