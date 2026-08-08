# Deductive Reasoning

## Purpose
Deductive reasoning derives conclusions that are necessarily true when premises are true and inference rules are valid. It is truth-preserving: if you start with true premises and apply valid rules, the conclusion cannot be false.

## When to Use
- When premises are known to be true with certainty.
- When the domain has formal rules (mathematics, logic, type systems, legal statutes).
- When you need a proof that something must be the case, not merely that it is likely.
- When reasoning about necessity, impossibility, or logical consequence.

## When Not to Use
- When premises are uncertain, probabilistic, or contested.
- When the domain is empirical and evidence is incomplete.
- When you need to generate hypotheses rather than verify them.
- When the inference rules are ambiguous or undefined.

## Problem Signals
- The problem contains "must," "necessarily," "if and only if," "therefore," or "it follows that."
- The problem involves formal systems: code that must satisfy a specification, a mathematical claim, a logical puzzle.
- The user asks for a proof, a guarantee, or a demonstration that something cannot be otherwise.
- The problem is structured as a syllogism: "All X are Y. Z is X. Therefore..."

## Inputs
- A set of premises (statements accepted as true).
- A set of valid inference rules (modus ponens, modus tollens, syllogism, etc.).
- Optionally, a target conclusion to verify or falsify.

## Procedure
1. **State premises explicitly.** Write each premise as a declarative sentence. Do not leave any premise implicit.
2. **Identify the inference rules available.** Which logical rules are valid in this domain? Name them.
3. **Check premise truth.** Are the premises actually true? If any premise is false or uncertain, stop — deductive reasoning cannot guarantee the conclusion.
4. **Apply inference rules step by step.** Each step must cite exactly which rule is applied to which premises. No leaps.
5. **Track the derivation chain.** Maintain an explicit chain from premises to intermediate conclusions to final conclusion.
6. **Verify each step.** For each inference: does the rule actually apply? Are there counterexamples to the rule in this domain?
7. **State the conclusion with its certainty qualifier.** If all premises are true and all rules are valid, the conclusion is necessary. Otherwise, qualify.

## Output
- A conclusion explicitly marked as "necessary" (if premises are true and rules valid) or "conditional on premises" (if premises are assumed).
- The derivation chain showing each inference step.
- Identification of any implicit premises that were surfaced.

## Strengths
- Truth-preserving: if premises are true, the conclusion is guaranteed.
- Definitive: produces certainty, not probability.
- Checkable: each step in the derivation is mechanically verifiable.

## Limitations
- Cannot generate new knowledge beyond what is implicit in the premises.
- Useless when premises are uncertain — the conclusion inherits all uncertainty.
- Limited to domains with formal inference rules.
- The "garbage in, garbage out" property: false premises produce valid but unsound conclusions.

## Common Failure Modes
- **Implicit premise smuggling.** The agent treats an unstated assumption as a premise without surfacing it. Always enumerate premises.
- **Rule misapplication.** Applying an inference rule outside its domain of validity (e.g., using modus ponens on probabilistic statements).
- **Confusing validity with soundness.** A valid argument with false premises produces a conclusion that may be false. Always check premise truth.
- **Scope creep.** Using deductive reasoning when the problem is actually inductive or abductive. If the user says "probably," deduction is the wrong tool.

## Verification
- Can each inference step be justified by naming the exact rule applied?
- Are all premises explicitly stated, with no hidden assumptions?
- Would a counterexample to the conclusion break any premise or rule? If not, the derivation is invalid.
- Reverse-check: assume the negation of the conclusion. Does it contradict the premises? If not, the conclusion does not follow.

## Combine With
- **Inductive reasoning** — use induction to establish premises, then deduction to derive consequences.
- **Abductive reasoning** — use abduction to generate candidate explanations, then deduction to test their logical consequences.
- **Argument analysis** — use deduction to test whether an argument's conclusion follows from its premises.

## Conflicts With
- **Bayesian reasoning** — deduction assumes certainty; Bayesian reasoning assumes uncertainty. Do not mix them in the same inference step. Use deduction for logical structure, Bayesian for empirical claims.

## Example
**Problem:** "If the database transaction committed, then the audit log has a record. The audit log has no record. What can we conclude?"

**Application:**
1. Premise 1: If transaction committed, then audit log has record. (P → Q)
2. Premise 2: Audit log has no record. (¬Q)
3. Inference rule: Modus tollens — from (P → Q) and (¬Q), infer (¬P).
4. Conclusion: The transaction did not commit. (¬P)
5. The conclusion is necessary (assuming both premises are true).

## Selection Metadata
```
id: deductive-reasoning
category: logical
best_for: [certain premises, formal systems, necessity proofs]
requires: [premises, inference rules]
produces: [necessary conclusions]
strengths: [truth-preserving, definitive]
limitations: [requires true premises, limited to formal domains]
combine_with: [inductive-reasoning, abductive-reasoning]
avoid_when: [premises are uncertain, domain is informal]
```