# Fallacy Detection

## Purpose
Identify specific reasoning errors (fallacies) in arguments by comparing the argument's structure against a taxonomy of known invalid reasoning patterns. This method enables precise critique of an argument rather than vague dismissal, and helps the agent avoid committing fallacies in its own reasoning.

## When to Use
- When an argument seems persuasive but something feels wrong about it — fallacy detection names the error
- When evaluating arguments in adversarial or persuasive contexts (debates, marketing, political speech)
- When constructing your own arguments and want to check for common reasoning errors before presenting them
- When teaching or explaining why a particular argument is flawed

## When Not to Use
- When the argument is in a purely formal domain (mathematics, logic) where validity is determined by formal rules, not fallacy taxonomy
- When the context is cooperative and the arguer is genuinely exploring ideas — fallacy detection can be weaponized to shut down exploration
- When the argument is so weak that fallacy detection is overkill — a simple "this doesn't follow" is sufficient
- When the fallacy label is used as a substitute for explaining why the argument fails

## Problem Signals
- The user says "this argument sounds convincing but I can't put my finger on what's wrong with it"
- The user encounters arguments that appeal to emotion, authority, or popularity rather than evidence
- The user describes a debate where one side seems to be using rhetorical tricks rather than reasoning
- The user is constructing an argument and wants to ensure it is free of common reasoning errors

## Inputs
- An argument (claim + supporting reasoning) to evaluate
- Sufficient context to understand what the arguer is trying to establish and to whom
- A taxonomy of fallacies (the agent should have a working knowledge of common fallacies, including formal fallacies like affirming the consequent and informal fallacies like ad hominem, straw man, false dilemma, and appeal to authority)

## Procedure
1. **Reconstruct the argument.** Before looking for fallacies, reconstruct the argument in its strongest form. State the claim, premises, and warrant. A fallacy is a flaw in reasoning, not a flaw in presentation — you must understand the reasoning before you can identify the flaw.
2. **Check for formal fallacies.** Formal fallacies are errors in logical structure. For deductive arguments: does the conclusion follow from the premises by the rules of the logical system? Common formal fallacies: affirming the consequent (if P then Q, Q is true, therefore P), denying the antecedent (if P then Q, P is false, therefore Q is false), and illicit conversion (all A are B, therefore all B are A).
3. **Check for informal fallacies.** Informal fallacies are errors in reasoning that arise from the content or context of the argument, not its logical form. Common categories: (a) fallacies of relevance — premises are irrelevant to the conclusion (ad hominem, appeal to emotion, red herring); (b) fallacies of ambiguity — terms shift meaning during the argument (equivocation, amphiboly); (c) fallacies of presumption — the argument assumes what it is trying to prove (begging the question, false dilemma, complex question).
4. **Check for probabilistic fallacies.** These are specific to reasoning under uncertainty: (a) base rate neglect — ignoring the prior probability; (b) conjunction fallacy — rating a conjunction as more probable than its conjuncts; (c) gambler's fallacy — believing independent events are dependent; (d) prosecutor's fallacy — confusing P(evidence | innocence) with P(innocence | evidence).
5. **Check for causal fallacies.** These are specific to causal reasoning: (a) post hoc ergo propter hoc — assuming causation from temporal sequence; (b) cum hoc ergo propter hoc — assuming causation from correlation; (c) ignoring a common cause; (d) reversing cause and effect.
6. **Name the fallacy specifically.** When you identify a fallacy, name it using its standard label AND explain why the argument commits it. Never just name the fallacy without explanation — fallacy-labeling without explanation is itself a fallacy (argument from fallacy: "your argument contains a fallacy, therefore your conclusion is false").
7. **Assess whether the fallacy is fatal.** Not all fallacies are equally damaging. Some fallacies are fatal to the argument — the conclusion simply does not follow. Others are fixable — the arguer could restate the argument more carefully and avoid the fallacy. Distinguish between fatal and fixable fallacies.
8. **Suggest correction (if fixable).** If the fallacy is fixable, describe how the argument could be restated to avoid the error. This is more constructive than simply naming the fallacy and moving on.

## Output
- The reconstructed argument (claim, premises, warrant)
- A list of fallacies identified, each with: the fallacy name, an explanation of why the argument commits it, and whether it is fatal or fixable
- For fixable fallacies: a suggested correction
- An overall assessment: is the argument's conclusion unsupported, or is the reasoning flawed but the conclusion might still be true?

## Strengths
- Provides precise, named critiques of reasoning errors, enabling specific feedback rather than vague dismissal
- Helps the agent avoid committing the same fallacies in its own reasoning
- Distinguishes between fatal and fixable fallacies, preventing the rejection of fixable arguments
- Covers a wide range of error types: logical, probabilistic, causal, and rhetorical

## Limitations
- Fallacy detection is vulnerable to false positives: an argument that superficially resembles a fallacy may be valid when reconstructed charitably
- The fallacy taxonomy is not exhaustive; novel reasoning errors may not fit a standard label
- Fallacy detection can be misused as a rhetorical weapon to dismiss arguments without engaging with their substance
- The context-dependence of informal fallacies makes them contestable: what looks like a straw man to one person may be a fair interpretation to another

## Common Failure Modes
- **Fallacy-labeling without explanation**: "that's a straw man" without explaining how the argument misrepresents the position. This is itself fallacious reasoning.
- **Charity failure**: interpreting the argument in the weakest possible way to make the fallacy detection easier, rather than reconstructing it in its strongest form
- **Fallacy inflation**: applying fallacy labels to arguments that are merely weak or unpersuasive, not actually fallacious. A weak argument is not necessarily a fallacious argument.
- **False equivalence**: treating a fatal fallacy and a fixable fallacy as equally damaging to the argument's conclusion
- **Over-detection in cooperative contexts**: applying fallacy detection aggressively in a brainstorming or exploratory discussion, shutting down the generation of ideas that are not yet fully formed
- **Ignoring the arguer's intent**: detecting a fallacy in the literal wording while ignoring the clear intended meaning, which was not fallacious

## Verification
- Has the argument been reconstructed in its strongest form before fallacy detection?
- Does each fallacy identification include an explanation of why the argument commits it, not just a label?
- Has each fallacy been assessed as fatal or fixable?
- If the argument is fixable, has a suggested correction been provided?
- Have you checked whether a charitable interpretation of the argument avoids the fallacy?

## Combine With
- argument-analysis for reconstructing the argument before detecting fallacies
- evidence-evaluation for assessing whether premises are factually true, independent of logical structure
- dialectic for testing the argument against its strongest counter-argument
- self-critique for applying fallacy detection to the agent's own reasoning

## Conflicts With
- Approaches that accept arguments at face value without structural analysis
- Rhetorical analysis that focuses on persuasiveness; a fallacious argument can still persuade

## Example
**Argument**: "We should adopt the new authentication system because Google uses it, and Google is a successful company."

**Reconstructed argument**:
- Claim: We should adopt the new authentication system.
- Premise 1: Google uses the new authentication system.
- Premise 2: Google is a successful company.
- Implicit warrant: If a successful company uses something, we should adopt it too.

**Fallacies identified**:

1. **Appeal to authority (ad verecundiam)** — The argument appeals to Google's authority as a successful company. Google's success does not make it an authority on authentication systems for our specific context. The fallacy is that the authority is not relevant to the claim. *Fatal*: Google's success is not relevant to whether the authentication system is right for us.

2. **False analogy (implicit)** — The argument assumes that what works for Google will work for us. Google is a multinational corporation with different scale, threat model, regulatory requirements, and engineering resources. The analogy is too weak to support the claim. *Fatal*: the differences between Google and our organization are greater than the similarities relevant to authentication system choice.

**Overall assessment**: The argument's conclusion is unsupported. The premises are true (Google does use the system, Google is successful), but they do not provide any reason to believe the system is right for us. The argument is valid in form but unsound because the warrant is false.

**Suggested correction**: A valid version of the argument would need to establish that (a) the authentication system meets our specific requirements, (b) the system has been validated in contexts similar to ours, and (c) Google's adoption provides evidence of the system's quality and reliability, not just that Google is successful.

## Selection Metadata
```
id: fallacy-detection
category: argumentation
best_for: [persuasive arguments, rhetoric vs. reasoning, critical thinking]
requires: [argument, fallacy taxonomy]
produces: [fallacy identification]
strengths: [catches errors, immunizes against rhetoric]
limitations: [false positives, context-dependent]
combine_with: [argument-analysis, self-critique]
avoid_when: [argument is purely formal, context is cooperative]
```