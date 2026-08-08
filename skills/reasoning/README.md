# Praxis

> Practical reasoning methods and patterns for AI agents.

## What is Praxis?

Praxis is a foundation skill that gives AI agents a structured cognitive toolkit for reasoning, problem-solving, and decision-making. It provides:

- **50+ reasoning methods** across 13 categories
- **20+ problem-solving patterns** for recurring problem structures
- **10 composed workflows** for common task types
- **20 meta-reasoning capabilities** for self-monitoring and verification
- **A method selection engine** that maps problems to appropriate reasoning strategies

## Why Praxis Exists

AI agents face a fundamental challenge: they are asked to reason about diverse problems — from debugging code to making strategic decisions — but they lack a systematic framework for choosing *how* to reason.

Without a structured approach, agents default to:
- Generic "think step by step" prompting
- A single reasoning strategy applied to all problems
- No explicit verification or self-critique
- No framework for knowing when to stop or escalate

Praxis solves this by providing a comprehensive, structured cognitive toolkit.

## The Problem Praxis Solves

For any given problem, an agent needs to answer:

1. What kind of problem am I facing?
2. What is known, unknown, assumed, and uncertain?
3. What constraints and stakes exist?
4. Which reasoning method is appropriate?
5. Should multiple methods be composed?
6. In what order should they be applied?
7. What should I verify or challenge?
8. When should I search, ask, experiment, delegate, or stop?

Praxis provides the infrastructure to answer all of these questions.

## The Cognitive Model

```
Reason → Decide → Solve → Verify
```

Praxis is organized into five layers:

| Layer | Purpose | Example |
|-------|---------|---------|
| **Meta-Reasoning** | Monitor and regulate reasoning | "Am I overconfident? What would make me wrong?" |
| **Method Selection** | Match problems to methods | "This is a causal problem with high stakes → causal graph reasoning" |
| **Reasoning Methods** | Systematic reasoning procedures | Bayesian reasoning, trade-off analysis, premortem |
| **Problem Patterns** | Recurring problem structures | Hypothesis-driven diagnosis, structured decision |
| **Workflows** | Composed sequences for outcomes | Diagnose, Research, Decide, Design |

## Key Distinctions

### Methods, Patterns, and Workflows

- **A method** describes *how to reason*. It is a systematic procedure. (e.g., Bayesian reasoning, constraint analysis, premortem)

- **A pattern** describes a *recurring problem structure*. It composes multiple methods. (e.g., Hypothesis-driven diagnosis, which uses abductive reasoning, Bayesian reasoning, and causal reasoning)

- **A workflow** describes a *composed sequence for achieving an outcome*. It composes patterns and methods. (e.g., Diagnose: Observe → Generate hypotheses → Rank → Test → Eliminate → Confirm → Verify)

### Meta-Reasoning

Meta-reasoning is not a method — it's reasoning *about* your reasoning. It answers:

- Am I thinking about this the right way?
- What assumptions am I making?
- How confident should I be?
- What would make my conclusion wrong?
- Should I continue, change approach, or stop?

## Repository Structure

```
skills/reasoning/
├── ontology/          ← Machine-readable concept registry
├── router/            ← Method selection engine
├── methods/           ← 50+ reasoning methods in 13 categories
├── patterns/          ← 20+ problem-solving patterns
├── meta/              ← 20 meta-reasoning capabilities
├── workflows/         ← 10 composed reasoning workflows
├── examples/          ← Worked examples with method selection
└── tests/             ← Test suites
```

## How an Agent Uses Praxis

### 1. Recognize the Need

The agent encounters a problem that requires structured reasoning — not just a factual lookup or simple pattern match.

### 2. Classify the Problem

Using `router/classify-problem.md`, the agent determines:
- Problem type (causal, decision, diagnostic, strategic, etc.)
- Uncertainty profile
- Stakes and reversibility
- Domain

### 3. Select Methods

Using `router/select-method.md`, the agent maps the classification to specific methods.

### 4. Compose if Needed

Using `router/compose-methods.md`, the agent combines methods if the problem spans multiple types.

### 5. Apply Methods

The agent follows the procedures in the method files.

### 6. Meta-Check

Throughout reasoning, the agent monitors its own process using the meta-reasoning capabilities.

### 7. Verify

The agent verifies its conclusions using verification, falsification, and self-critique.

### 8. Decide Next Step

The agent determines whether to continue, switch methods, gather information, or stop.

## Example: Method Selection Flow

**Problem**: "Our payment service is returning intermittent 500 errors."

```
Classify:
  → Causal problem (what caused this?)
  → Epistemic uncertainty (we can investigate)
  → High stakes (revenue impact)
  → Domain: software-engineering

Select:
  → Abductive reasoning (generate hypotheses)
  → Bayesian reasoning (update beliefs)
  → Causal reasoning (confirm mechanism)

Compose:
  → Chain: Abductive → Bayesian → Causal

Pattern:
  → Hypothesis-driven diagnosis

Workflow:
  → Diagnose

Meta-check:
  → Am I anchoring on the most obvious cause?
  → Have I considered alternative hypotheses?
  → What would falsify my leading hypothesis?
```

## Example Workflows

### Diagnose

```
Observe → Define problem → Generate hypotheses → Rank → 
Gather evidence → Test → Eliminate → Confirm → Verify intervention
```

### Research

```
Question → Scope → Search → Evaluate sources → Extract evidence → 
Triangulate → Synthesize → Identify uncertainty → Report confidence
```

### Decide

```
Frame → Identify options → Define criteria → Evaluate → 
Analyze trade-offs → Assess risks → Decide → Verify → Monitor
```

## How to Extend

### Adding a New Method

1. Create the method file in the appropriate `methods/` category
2. Follow the standard method structure (Purpose, When to Use, Procedure, etc.)
3. Add metadata to `ontology/methods.yaml`
4. Add relationships to `ontology/relationships.yaml` (compositions, substitutions, conflicts)
5. Update the router if the method adds new classification signals

### Adding a New Pattern

1. Create the pattern file in the appropriate `patterns/` category
2. Reference the methods it composes
3. Add to `ontology/patterns.yaml`

### Adding a New Workflow

1. Create the workflow file in `workflows/`
2. Reference underlying methods and patterns (don't duplicate them)

## Contribution Principles

1. **Evidence over opinion**: Methods should be grounded in established disciplines (logic, probability theory, decision science, etc.)
2. **Procedure over description**: Methods should be actionable, not just descriptive
3. **Limitations are mandatory**: Every method must document when it fails
4. **Cross-reference aggressively**: Methods should reference compatible and conflicting methods
5. **Machine-readable metadata**: All methods should have ontology entries
6. **Adversarial review**: New methods should survive a "what would make this wrong?" challenge

## License

MIT

## Acknowledgments

Praxis draws on established disciplines including:
- Logic and formal reasoning
- Probability theory and statistics
- Decision theory and game theory
- Systems thinking and complexity science
- Cognitive science and metacognition research
- Forecasting and calibration research (Tetlock, IARPA)
- Risk analysis and safety engineering
- Design thinking and creative problem-solving
- Argumentation and critical thinking