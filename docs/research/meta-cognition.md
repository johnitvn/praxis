# Meta-Cognition — Research Notes

## Canonical Sources

- **Flavell, J.H.** (1979) — Originated the concept of metacognition
- **Brown, A.L.** (1987) — Metacognition in learning and problem-solving
- **Dunlosky, J. & Metcalfe, J.** (Metacognition, 2009) — Comprehensive survey
- **Kruger, J. & Dunning, D.** (1999) — Dunning-Kruger effect: unskilled and unaware
- **Kahneman, D.** (Thinking, Fast and Slow, 2011) — System 1/System 2, cognitive biases
- **Stanovich, K.E.** (The Robot's Rebellion, 2004) — Rationality and metacognition
- **Lieder, F. & Griffiths, T.L.** (2017) — Resource-rational analysis, meta-decision making

## Key Findings

### Metacognition
- Flavell's definition: "knowledge and cognition about cognitive phenomena"
- Two components: metacognitive knowledge (what you know about cognition) and metacognitive regulation (control of cognition)
- The monitoring-control loop: monitor cognitive state → evaluate → regulate → repeat
- AI agents need explicit metacognitive scaffolding because they lack native introspective capabilities
- Most important metacognitive skill: knowing when you don't know

### Bias Detection
- Kahneman-Tversky program: systematic deviations from rational choice
- Critically: biases are not "errors" — they're features of System 1 that fail in specific contexts
- Most common AI agent biases: anchoring, confirmation, overconfidence, base rate neglect
- The "bias blind spot": people (and AI agents) recognize biases in others but not themselves
- Mitigation requires structural interventions, not just awareness

### Calibration
- Overconfidence is the most robust finding in judgment research
- The "planning fallacy": people underestimate time and cost by 50-100% on average
- The "illusion of explanatory depth": people think they understand things better than they do
- Improving calibration: track predictions, get rapid feedback, use reference classes
- The "confidence-accuracy gap": confidence increases faster than accuracy

### Verification and Falsification
- Popper: the mark of science is falsifiability, not confirmability
- Mayo's "severe testing": a hypothesis is supported only if it has survived tests that would likely have found it false
- Confirmation bias: people seek evidence that confirms, not disconfirms
- The "positive test strategy": testing hypotheses by looking for confirming instances
- AI agents should actively seek disconfirming evidence for every significant conclusion

### Epistemic Humility
- The Dunning-Kruger effect: the least competent are the most overconfident
- Intellectual humility: recognizing the limits of one's knowledge
- The "circle of competence": know what you know and what you don't know
- Admitting uncertainty is not weakness — it's accuracy
- Tetlock: "foxes" (who know many things and are humble) outperform "hedgehogs" (who know one big thing and are confident)

## Design Implications for AI Agents

1. **Metacognition must be explicit**: AI agents don't have native introspection; they need explicit metacognitive procedures
2. **Verification is not optional**: Every conclusion should be verified; the cost of verification is almost always less than the cost of being wrong
3. **Calibration requires tracking**: Without tracking predictions against outcomes, calibration is impossible
4. **Bias detection is structural**: Relying on "being aware of biases" doesn't work; structural interventions are needed
5. **The most important question**: "What would make my current reasoning wrong?"

## References

- Flavell, J.H. (1979). Metacognition and cognitive monitoring. American Psychologist.
- Brown, A.L. (1987). Metacognition, executive control, self-regulation, and other more mysterious mechanisms.
- Dunlosky, J. & Metcalfe, J. (2009). Metacognition. Sage.
- Kruger, J. & Dunning, D. (1999). Unskilled and unaware of it. Journal of Personality and Social Psychology.
- Kahneman, D. (2011). Thinking, Fast and Slow. Farrar, Straus and Giroux.
- Stanovich, K.E. (2004). The Robot's Rebellion. University of Chicago Press.
- Lieder, F. & Griffiths, T.L. (2017). Resource-rational analysis. Behavioral and Brain Sciences.
- Popper, K. (1959). The Logic of Scientific Discovery. Hutchinson.
- Mayo, D.G. (1996). Error and the Growth of Experimental Knowledge. University of Chicago Press.