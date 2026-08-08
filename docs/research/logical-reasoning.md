# Logical Reasoning — Research Notes

## Canonical Sources

- **Aristotle** (Organon) — Foundation of syllogistic logic and deductive reasoning
- **Peirce, C.S.** (Collected Papers) — Formalized abduction as distinct from deduction and induction
- **Gentzen, G.** — Natural deduction and sequent calculus
- **Gentner, D.** (Structure-Mapping Theory) — Analogical reasoning as structural alignment
- **Tarski, A.** — Formal semantics and logical consequence
- **Allen, J.F.** — Temporal interval algebra for temporal reasoning

## Key Findings

### Deductive Reasoning
- Truth-preserving: if premises are true and inference rules are valid, conclusion is necessarily true
- Most commonly misapplied when premises are uncertain but treated as certain
- AI agents should use deductive reasoning for: formal systems, logical consequence, necessity proofs
- AI agents should NOT use deductive reasoning for: empirical claims, uncertain domains, probabilistic reasoning

### Inductive Reasoning
- Ampliative: conclusion goes beyond premises (not truth-preserving)
- Strength depends on sample representativeness, sample size, and pattern consistency
- Most commonly misapplied when sample is biased or unrepresentative
- The "problem of induction" (Hume) — inductive conclusions are never certain

### Abductive Reasoning
- Inference to the best explanation
- Generates hypotheses from observations
- Quality depends on domain knowledge completeness
- Most commonly misapplied when domain knowledge is incomplete or biased
- Key insight from Peirce: abduction generates hypotheses, deduction derives predictions, induction tests them

### Analogical Reasoning
- Structure-mapping: relational similarity, not surface similarity
- Gentner's key finding: people (and AI) often confuse surface similarity with structural similarity
- Most powerful when source and target domains share deep relational structure
- Most commonly misapplied when analogy is based on superficial features

### Temporal Reasoning
- Allen's interval algebra: 13 possible relations between time intervals
- Critical for scheduling, planning, and causality (causes precede effects)
- AI agents commonly fail to reason about concurrency and partial ordering

## Method Boundaries

- **Deductive vs. Inductive**: Deduction preserves truth; induction amplifies knowledge. Use deduction when premises are certain; use induction when generalizing from data.
- **Abductive vs. Bayesian**: Both generate explanations. Abduction is qualitative; Bayesian is quantitative. Use abduction when probabilities are unavailable; use Bayesian when they are.
- **Analogical vs. First-Principles**: Analogy transfers knowledge from known to unknown; first principles rebuilds from fundamentals. Use analogy for speed; use first principles for depth.

## References

- Aristotle. Organon. ~350 BCE.
- Peirce, C.S. (1931-1958). Collected Papers. Harvard University Press.
- Gentner, D. (1983). Structure-mapping: A theoretical framework for analogy. Cognitive Science.
- Allen, J.F. (1983). Maintaining knowledge about temporal intervals. Communications of the ACM.
- Gentzen, G. (1935). Investigations into logical deduction.
- Tarski, A. (1956). Logic, Semantics, Metamathematics. Oxford University Press.