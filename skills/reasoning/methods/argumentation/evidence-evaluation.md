# Evidence Evaluation

## Purpose
Assess the quality, relevance, and credibility of evidence used to support or refute a claim. This method determines how much weight to give a piece of evidence by examining its source, methodology, corroboration, and relationship to the claim it is meant to support.

## When to Use
- When a claim is supported by evidence of unknown quality (a study, a statistic, an expert opinion, an anecdote)
- When you need to decide between competing claims backed by different evidence
- When you are gathering evidence and need to distinguish between strong and weak sources
- When an argument's validity depends on the truth of its factual premises

## When Not to Use
- When the evidence is direct observation and you can verify it yourself
- When the claim is purely logical or definitional and does not depend on empirical evidence
- When the source is irrelevant to the claim (e.g., evaluating a mathematical proof by the author's credentials)
- When the evidence is so clearly strong or weak that formal evaluation adds no value

## Problem Signals
- The user says "according to a study..." or "experts say..." without specifying which study or which experts
- The user presents a statistic without context (sample size, methodology, source)
- The user is deciding between two conflicting claims, each supported by different evidence
- The user describes a situation where evidence quality is disputed ("they cite a study, but is it any good?")

## Inputs
- A piece of evidence and the claim it is meant to support or refute
- Information about the evidence's source, methodology, and context
- Domain knowledge sufficient to assess the evidence's quality within its field

## Procedure
1. **Clarify the relationship.** What claim is this evidence meant to support? Is the evidence direct (the claim itself is being measured) or indirect (the evidence is a proxy for the claim)? Direct evidence is stronger than indirect.
2. **Assess the source.** Evaluate the evidence's origin on three dimensions: (a) competence — does the source have the expertise to produce this evidence? (b) motivation — does the source have a reason to produce biased evidence (financial interest, ideological commitment, career incentive)? (c) track record — has the source produced reliable evidence in the past? A source can be competent and well-motivated but still produce poor evidence if the methodology is flawed.
3. **Assess the methodology.** How was the evidence produced? For quantitative evidence: sample size, sampling method, measurement validity, statistical analysis, confounding controls. For qualitative evidence: selection of cases, triangulation, saturation, reflexivity. For expert judgment: basis of expertise, use of evidence, calibration. The key question is: could the same methodology have produced this evidence even if the claim were false?
4. **Assess relevance.** Does the evidence actually bear on the claim? Four relevance criteria: (a) temporal — is the evidence from the relevant time period? (b) population — does the evidence apply to the relevant population? (c) context — were the conditions under which evidence was produced similar to the conditions of the claim? (d) mechanism — does the evidence speak to the causal mechanism the claim depends on, or just to a correlation?
5. **Assess corroboration.** Is the evidence consistent with other evidence? Independent corroboration from different sources using different methods strengthens the evidence. Contradictory evidence from a credible source weakens it. Absence of corroboration is not disconfirmation — it may mean the question has not been studied.
6. **Assess the counter-evidence.** What evidence would the other side present? Actively search for disconfirming evidence. If you cannot find any, you may not have looked hard enough, or the question may be one-sided. The strongest evidence survives a good-faith search for disconfirming evidence.
7. **Assign an evidence strength rating.** Synthesize the assessments into a rating: strong (multiple independent sources, rigorous methodology, direct relevance), moderate (single source with good methodology, some relevance concerns), weak (anecdotal, indirect, methodological flaws), or indeterminate (insufficient information to assess). Do not confuse "I want this to be true" with "this evidence is strong."

## Output
- A summary of the evidence and its relationship to the claim
- Source assessment (competence, motivation, track record)
- Methodology assessment (could the method have produced this evidence if the claim were false?)
- Relevance assessment (temporal, population, context, mechanism)
- Corroboration assessment (consistent with other evidence? contradictory evidence?)
- Overall evidence strength rating with rationale

## Strengths
- Provides a systematic framework for evaluating evidence, reducing reliance on intuition
- Distinguishes between different dimensions of evidence quality (source, method, relevance, corroboration)
- Actively searches for disconfirming evidence, countering confirmation bias
- Produces a strength rating that supports decision-making about which claims to accept

## Limitations
- Requires domain knowledge to assess methodology; without it, the assessment is superficial
- Source assessment can devolve into ad hominem ("this source is biased, therefore the evidence is wrong")
- Corroboration assessment is vulnerable to the "echo chamber" effect if all evidence sources share the same bias
- Evidence strength is a continuum; the rating categories are rough approximations

## Common Failure Modes
- **Source confusion**: dismissing evidence because the source is imperfect (all sources are imperfect) rather than assessing whether the imperfection is severe enough to undermine the evidence
- **Methodological perfectionism**: rejecting evidence because the methodology has a flaw, without assessing whether the flaw is fatal to the conclusion
- **Relevance neglect**: accepting strong evidence for a related-but-different claim as if it were evidence for the actual claim
- **Corroboration bias**: treating multiple sources that all cite the same original study as independent corroboration
- **Counter-evidence asymmetry**: searching diligently for counter-evidence against claims you disagree with but not against claims you agree with
- **Precision-weighting**: overweighting precise but weak evidence (a survey with a 3% margin of error but a biased sample) over imprecise but strong evidence (a rough estimate from a well-designed experiment)

## Verification
- Is the evidence's relationship to the claim explicitly stated (direct or indirect)?
- Has the source been assessed on all three dimensions (competence, motivation, track record)?
- Has the methodology been assessed for the specific question: "could this method produce this evidence if the claim were false?"
- Has a genuine search for disconfirming evidence been conducted?
- Does the evidence strength rating reflect the assessment, not the desired conclusion?

## Combine With
- argument-analysis for evaluating how the evidence fits into the argument's structure
- fallacy-detection for identifying when evidence is being misused (e.g., cherry-picking, base rate neglect)
- bayesian-reasoning (from probabilistic category) for quantifying the evidential weight as a likelihood ratio
- calibration for assessing the credibility of expert sources

## Conflicts With
- Approaches that accept evidence at face value without evaluating its quality
- Relativism that treats all evidence as equally valid or invalid

## Example
**Claim**: Remote work reduces employee productivity.

**Evidence**: A study of 10,000 employees at a Chinese call center found that remote workers handled 13% fewer calls per hour than office workers (Bloom et al., 2023).

**Relationship to claim**: Direct. The study measures productivity (calls handled) in a remote-vs-office comparison.

**Source assessment**:
- Competence: High. The authors are economists at Stanford with a track record of labor productivity research. Published in a peer-reviewed journal.
- Motivation: Low risk of bias. The study was funded by the National Science Foundation, not by a company with a stake in the outcome.
- Track record: Strong. The authors have published related work with consistent findings.

**Methodology assessment**:
- Design: Randomized controlled trial. Employees were randomly assigned to remote or office work. This is the gold standard for causal inference.
- Sample size: 10,000 employees. Large enough for precise estimates.
- Measurement: Calls per hour is an objective productivity metric, not self-reported.
- Confounding: Randomized assignment controls for selection bias (more productive workers might choose remote work).
- Could the method produce this evidence if the claim were false? The randomization makes this unlikely. The difference is statistically significant and practically meaningful.

**Relevance assessment**:
- Temporal: Study conducted in 2021-2022. Relevant to the current remote work context.
- Population: Chinese call center employees. Call center work is highly structured and easily monitored — the results may not generalize to knowledge work (software engineering, design, strategy).
- Context: The remote workers were truly remote (no hybrid option). The office workers were fully in-office. This is a clean comparison but may not reflect typical hybrid arrangements.
- Mechanism: The study found that remote workers took more breaks and had lower call resolution rates. The mechanism (reduced monitoring and collaboration) is plausible for call center work but may not apply to other types of work.

**Corroboration**: Mixed. Other studies of remote call centers find similar results. Studies of remote knowledge workers find mixed results — some show productivity increases, others show decreases, depending on the type of work and the measurement method.

**Counter-evidence**: A study of a US technology company found that remote workers produced 22% more code commits but fewer collaborative innovations (Choudhury et al., 2024). A meta-analysis of 45 studies found that remote work effects depend heavily on task type, with structured tasks showing small negative effects and creative tasks showing small positive effects.

**Overall strength**: Moderate. The evidence is methodologically strong for call center work but has limited relevance to other types of work. The claim "remote work reduces employee productivity" is too broad — the evidence supports a narrower claim: "remote work reduces productivity in highly structured, easily monitored tasks."

## Selection Metadata
```
id: evidence-evaluation
category: argumentation
best_for: [source credibility, evidence quality, claim verification]
requires: [evidence, source, claim]
produces: [evidence strength, credibility assessment]
strengths: [systematic, source-aware]
limitations: [requires domain knowledge, source access]
combine_with: [argument-analysis, bayesian-reasoning]
avoid_when: [evidence is direct observation, source is irrelevant]
```