# Abductive Reasoning

## Purpose
Abductive reasoning infers the most likely explanation for a set of observations. Unlike deduction (which proves conclusions) or induction (which generalizes patterns), abduction works backward from effects to probable causes — it answers "what would best explain this?"

## When to Use
- When you have observations that need explaining and no direct access to the cause.
- When diagnosing failures, bugs, or anomalies.
- When generating hypotheses to test.
- When the problem is "why did this happen?" rather than "what will happen?" (induction) or "what must be true?" (deduction).

## When Not to Use
- When you have no domain knowledge to constrain possible explanations — abduction without domain knowledge is unbounded guessing.
- When the explanation must be certain — abduction produces the best explanation, not the only possible one.
- When you can directly observe the cause — if you can see it, you don't need to infer it.
- When the cost of the wrong explanation is catastrophic and no verification is possible.

## Problem Signals
- The problem asks "why," "what caused," "how did this happen," or "what explains."
- The user presents a surprising observation: "The system was working yesterday, now it's broken, and nobody changed anything."
- The problem is a diagnostic puzzle: symptoms are known, root cause is unknown.
- The user has ruled out the obvious explanations and needs a new hypothesis.

## Inputs
- A set of observations (symptoms, effects, anomalies) that need explaining.
- Domain knowledge: what kinds of causes are plausible in this domain? What is the causal structure?
- A set of candidate explanations (hypotheses) — or the ability to generate them.

## Procedure
1. **Enumerate observations.** List every observation that needs explaining. Be precise: "the API returns 500 errors" not "the system is broken."
2. **Generate candidate explanations.** For each observation, ask: what could cause this? Use domain knowledge to constrain the search. List multiple hypotheses — do not fixate on the first one.
3. **Evaluate each hypothesis against criteria:**
   - **Explanatory power:** How many observations does it explain? Does it explain the most surprising ones?
   - **Simplicity:** Does it require fewer assumptions than alternatives? (Occam's razor)
   - **Plausibility:** How likely is this explanation given prior knowledge? Has it happened before?
   - **Testability:** Can the hypothesis be tested? What evidence would confirm or disconfirm it?
   - **Consilience:** Does it explain observations from multiple independent sources?
4. **Rank hypotheses.** The best explanation is not necessarily the most likely a priori — it is the one that would make the observations most expected.
5. **Identify the best explanation.** State it explicitly: "The best explanation for [observations] is [hypothesis], because [reasoning]."
6. **Specify tests.** What would confirm this explanation? What would rule it out? Abduction without follow-up testing is incomplete.

## Output
- The best explanation(s) for the observations, ranked by explanatory power.
- For each hypothesis: what it explains, what it does not explain, and what assumptions it requires.
- Testable predictions: if this explanation is correct, what else should be true?
- Alternative explanations that were considered and why they were rejected.

## Strengths
- Handles incomplete information — you don't need to see the cause to infer it.
- Generates hypotheses that can be tested.
- The natural reasoning mode for diagnosis and debugging.
- Works with a single surprising observation, unlike induction which requires multiple instances.

## Limitations
- Multiple explanations may fit the data equally well — abduction does not guarantee uniqueness.
- Quality depends entirely on domain knowledge — without it, abduction is speculation.
- The best explanation is not necessarily the true explanation.
- Susceptible to the "base rate fallacy" — ignoring how common an explanation is in general.

## Common Failure Modes
- **Anchoring on the first hypothesis.** The agent generates one explanation and stops. Always generate at least three competing hypotheses.
- **Ignoring base rates.** A hypothesis that fits the data perfectly may be astronomically unlikely. "The server crashed because of cosmic rays" explains the observation but is implausible.
- **Explanation without testing.** Treating abduction as the endpoint rather than the beginning. The best explanation is a hypothesis to test, not a conclusion.
- **Overfitting the explanation.** Adding epicycles to make a favored hypothesis fit. If the hypothesis requires many auxiliary assumptions, it is probably wrong.
- **Confusing correlation with causation.** Observing that A and B co-occur and concluding that A explains B, without considering that B might cause A, or C might cause both.

## Verification
- Does the explanation account for all significant observations? If key observations are unexplained, the hypothesis is incomplete.
- Are there alternative explanations that fit the data equally well with fewer assumptions?
- What would disconfirm this explanation? If nothing would, the explanation is unfalsifiable and therefore unscientific.
- Does the explanation make novel predictions that can be tested?

## Combine With
- **Bayesian reasoning** — use Bayes' rule to formally compare hypotheses given evidence.
- **Causal-graph reasoning** — use a causal model to constrain which explanations are structurally possible.
- **Deductive reasoning** — once a hypothesis is selected, deduce its consequences to generate testable predictions.
- **Hypothesis testing** — follow abduction with formal tests to confirm or reject the explanation.

## Example
**Problem:** A web application returns 500 errors for all users. The database is responsive. The application logs show "connection refused" for the cache service. The cache service was restarted 5 minutes ago.

**Application:**
1. Observations: (a) 500 errors for all users, (b) database is responsive, (c) "connection refused" for cache, (d) cache restarted 5 minutes ago.
2. Candidate hypotheses:
   - H1: The cache service failed to restart properly and is not accepting connections.
   - H2: A network partition is blocking the application from reaching the cache.
   - H3: The application's cache connection pool did not reconnect after the restart.
3. Evaluation:
   - H1 explains (a), (c), (d). Plausible: restarts can fail. Simple.
   - H2 explains (a), (c). Does not explain (d) — network partition is unrelated to restart timing. Less parsimonious.
   - H3 explains (a), (c), (d). Plausible: connection pools often fail to reconnect. Explains timing.
4. Best explanation: H3 (connection pool failure after restart) — it explains all observations, is plausible, and is testable.
5. Test: Check if the application's cache connection pool has active connections. If zero, H3 is confirmed.

## Selection Metadata
```
id: abductive-reasoning
category: logical
best_for: [explanation, diagnosis, hypothesis generation]
requires: [observations, domain knowledge]
produces: [best explanation]
strengths: [handles incomplete information, generates hypotheses]
limitations: [multiple explanations possible, dependent on domain knowledge quality]
combine_with: [bayesian-reasoning, causal-graph-reasoning]
avoid_when: [domain knowledge is absent, explanation must be certain]
```