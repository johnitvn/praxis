# Causal Discovery

## Purpose
Causal discovery infers causal structure from observational (and optionally experimental) data when the causal graph is unknown. It uses patterns of conditional independence and distributional properties to narrow down the set of causal graphs compatible with the data.

## When to Use
- When the causal structure is unknown and must be learned from data.
- When domain knowledge is incomplete — you know some variables are related but not how.
- When exploring a new dataset to generate causal hypotheses.
- When you have observational data and want to know what causal structures are consistent with it.

## When Not to Use
- When the data is insufficient — causal discovery requires enough samples to reliably test conditional independencies.
- When the assumptions of the discovery algorithm are violated (causal sufficiency, faithfulness, no feedback).
- When you need a definitive causal graph — causal discovery typically returns an equivalence class, not a single graph.
- When you have strong domain knowledge that already specifies the graph — use causal-graph reasoning instead.

## Problem Signals
- The problem asks: "What causes what?" without a pre-existing theory.
- The user has a dataset with many variables and wants to understand the causal relationships.
- The user says: "We don't know the causal structure, but we have a lot of data."
- The problem is exploratory: generating hypotheses about causal structure for later testing.

## Inputs
- Data: observations of multiple variables across many units.
- A set of variables whose causal relationships are to be discovered.
- Algorithm choice: constraint-based (PC, FCI), score-based (GES), or functional (LiNGAM).
- Optional: background knowledge about some causal relationships (known edges, forbidden edges, temporal ordering).

## Procedure
1. **Define the variable set.** Which variables are in the system? Be complete — omitted variables become latent confounders.
2. **Choose the discovery algorithm based on assumptions:**
   - **Constraint-based (PC algorithm):** Assumes causal sufficiency (no latent confounders), faithfulness, and acyclicity. Tests conditional independence for each pair of variables given all possible subsets of other variables. Returns a CPDAG (completed partially directed acyclic graph).
   - **FCI (Fast Causal Inference):** Relaxes causal sufficiency — allows latent confounders. Returns a PAG (partial ancestral graph). Use when you suspect unmeasured variables.
   - **Score-based (GES):** Searches over graph structures to maximize a score (BIC, BDeu). Assumes causal sufficiency. Returns a CPDAG.
   - **LiNGAM (Linear Non-Gaussian Acyclic Model):** Exploits non-Gaussianity of error terms to identify causal direction. Returns a fully directed graph when assumptions hold. Use when relationships are linear and errors are non-Gaussian.
3. **Preprocess the data.** Handle missing values. Check for outliers. Consider whether variables need transformation.
4. **Run the algorithm.** Apply the chosen algorithm to the data. Provide any background knowledge as constraints.
5. **Interpret the output.** The output is typically an equivalence class — a set of graphs that are observationally equivalent. Directed edges are those that have the same orientation in all graphs in the class. Undirected edges are those whose orientation varies.
6. **Integrate domain knowledge.** Use domain expertise to orient undirected edges. Temporal order (causes precede effects) is especially powerful: if A occurs before B, A → B is the only possible orientation.
7. **Validate the discovered graph.** Check whether the graph implies conditional independencies that hold in the data. Test the graph on held-out data if available. Design experiments to distinguish between graphs in the equivalence class.
8. **Report uncertainty.** State which edges are reliably oriented and which are ambiguous. Report the equivalence class size — a smaller class means more informative results.

## Output
- A causal graph (or equivalence class of graphs) representing the discovered causal structure.
- Edge classifications: directed (causal direction identified), undirected (direction unknown), bidirected (latent confounding).
- The algorithm used and the assumptions it requires.
- A plan for distinguishing between equivalent graphs (experimental interventions).

## Strengths
- Learns causal structure from data without requiring a pre-specified graph.
- Handles observational data — no experiments required for discovery.
- Multiple algorithms available for different assumption sets.
- Generates testable causal hypotheses that can guide subsequent experiments.

## Limitations
- Returns equivalence classes, not unique graphs — many causal structures are observationally indistinguishable.
- Requires strong assumptions (causal sufficiency, faithfulness, acyclicity) that are often violated in practice.
- Sample size matters: conditional independence tests require large samples, especially for high-dimensional conditioning sets.
- Cannot distinguish between graphs in the same equivalence class without experimental data or strong assumptions.
- The faithfulness assumption can be violated in real systems (e.g., when causal paths exactly cancel).

## Common Failure Modes
- **Treating the output as a single definitive graph.** The output is an equivalence class. Undirected edges mean the orientation is unknown, not that the edge is bidirectional.
- **Ignoring assumption violations.** Running PC on data with latent confounders produces spurious edges. Check whether the algorithm's assumptions are plausible for the domain.
- **Over-interpreting small samples.** Conditional independence tests are unreliable with small samples. The algorithm may find spurious dependencies or miss real ones.
- **Confusing temporal precedence with causation.** If A precedes B, causal discovery may orient A → B, but A could be an effect of a common cause that also causes B earlier. Temporal order is strong evidence but not definitive.
- **Using causal discovery as a substitute for experiments.** Discovery is hypothesis generation. Causal claims from discovery should be tested with interventions or experiments.

## Verification
- Do the discovered conditional independencies hold in the data? Check the key independencies implied by the graph.
- Does the discovered graph change substantially when the algorithm's parameters (significance threshold, score function) are varied?
- Does the graph make sense given domain knowledge? Implausible edges suggest either the algorithm is wrong or your domain knowledge is incomplete.
- Can the ambiguous edges be resolved by collecting additional data (e.g., interventions, temporal data)?

## Combine With
- **Causal-graph reasoning** — once a graph is discovered, use it for intervention planning and effect estimation.
- **Statistical reasoning** — use statistical tests for conditional independence as the engine of constraint-based discovery.
- **Experimental design** — use the discovered equivalence class to design experiments that distinguish between remaining candidate graphs.
- **Bayesian reasoning** — use Bayesian methods for causal discovery to incorporate prior knowledge about graph structure.

## Example
**Problem:** A data scientist has data on website metrics: Page Load Time (PLT), Bounce Rate (BR), and Session Duration (SD). They want to understand the causal relationships. Does slow load time increase bounce rate? Does bounce rate affect session duration? What causes what?

**Application:**
1. Variables: PLT, BR, SD. 100,000 sessions.
2. Algorithm choice: PC algorithm (constraint-based, assumes causal sufficiency and faithfulness).
3. Preprocessing: Log-transform PLT and SD to handle skew. No missing data.
4. Run PC with alpha = 0.01:
   - PLT and BR are dependent unconditionally.
   - PLT and BR are still dependent given SD → no edge removed.
   - PLT and SD are dependent unconditionally.
   - PLT and SD are still dependent given BR → no edge removed.
   - BR and SD are dependent unconditionally.
   - BR and SD are independent given PLT → edge removed. PLT screens off BR from SD.
5. Output: PLT → BR and PLT → SD. The edge between BR and SD is removed (they are conditionally independent given PLT).
6. The CPDAG has directed edges from PLT to BR and PLT to SD. No undirected edges — the structure is fully oriented.
7. Domain knowledge integration: This makes sense — page load time is a technical metric that causally affects user behavior metrics (bounce rate, session duration). Bounce rate and session duration are correlated only because they share a common cause (load time).
8. Validation: Check that BR ⟂ SD | PLT holds in a held-out sample. It does.
9. Recommendation: The causal graph is identified. Optimization efforts should target page load time, which causally affects both behavioral metrics. Improving PLT will reduce bounce rate and increase session duration.

## Selection Metadata
```
id: causal-discovery
category: causal
best_for: [unknown causal structure, observational data, exploratory analysis]
requires: [data, conditional independence tests]
produces: [candidate causal structures]
strengths: [learns structure from data, handles observational data]
limitations: [equivalence classes, requires assumptions]
combine_with: [causal-graph-reasoning, statistical-reasoning]
avoid_when: [data is insufficient, assumptions are violated]
```