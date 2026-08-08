# When to Experiment

Decide when to run experiments, tests, or simulations to gather information.

## Purpose

Experimentation generates new information that doesn't exist yet. It is the most expensive information-gathering method but sometimes the only way to resolve critical uncertainties.

## When to Experiment

### Experiment When:
- The information doesn't exist and can't be found
- The uncertainty is material to an important decision
- The cost of the experiment is less than the value of the information
- You can design a valid experiment
- The experiment can be completed before the decision deadline
- The stakes justify the cost

### Types of Experiments

| Type | Description | When to Use |
|------|-------------|-------------|
| **A/B test** | Randomized comparison of two options | Comparing alternatives with measurable outcomes |
| **Simulation** | Computational model of the system | System is too complex or expensive to test directly |
| **Prototype** | Simplified version to test a concept | Early-stage design, uncertain feasibility |
| **Stress test** | Test at extreme conditions | Safety-critical systems, reliability assessment |
| **Thought experiment** | Logical exploration of implications | Testing consistency, exploring edge cases |
| **Pilot** | Small-scale deployment | Testing before full rollout |

## When NOT to Experiment

### Don't Experiment When:
- The information is available through cheaper means (search, ask)
- The experiment cost exceeds the value of information
- The experiment would take longer than the decision can wait
- The experiment cannot be designed to be valid
- The experiment is unethical or harmful
- The experiment would change the system in ways you can't undo
- The uncertainty is not material to the decision

## Experiment Design

### Valid Experiments Have:
1. **Clear hypothesis**: What are you testing?
2. **Measurable outcome**: How will you know the result?
3. **Control for confounding**: What else could explain the result?
4. **Sufficient sample/power**: Will the experiment detect the effect?
5. **Defined stopping condition**: When is the experiment done?

### Common Design Failures

| Failure | Description |
|---------|-------------|
| **Confounding** | Not controlling for alternative explanations |
| **Underpowered** | Sample too small to detect the effect |
| **Measurement error** | Outcome measure is noisy or invalid |
| **Hawthorne effect** | The act of experimenting changes behavior |
| **Overgeneralization** | Extending results beyond the experimental conditions |
| **Peeking** | Stopping the experiment when results look favorable |
| **Survivorship bias** | Only measuring subjects that complete the experiment |

## The Experiment Decision

```
Is there a material information gap?
│
├─ Can it be filled by search or ask?
│   ├─ Yes → Use cheaper method
│   └─ No → Can I design a valid experiment?
│       ├─ No → Proceed with uncertainty
│       └─ Yes → Is value of information > cost of experiment?
│           ├─ No → Proceed with uncertainty
│           └─ Yes → Is there time to run it?
│               ├─ No → Proceed with uncertainty
│               └─ Yes → RUN EXPERIMENT
```