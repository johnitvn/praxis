# Risk Analysis — Research Notes

## Canonical Sources

- **Kaplan, S. & Garrick, B.J.** (1981) — Risk = scenario × likelihood × consequence (the "risk triplet")
- **Taleb, N.N.** (The Black Swan, 2007; Antifragile, 2012) — Tail risk, fragility, unknown unknowns
- **Rasmussen, J.** (1997) — Risk management in dynamic systems, safety models
- **Reason, J.** (Human Error, 1990; Managing the Risks of Organizational Accidents, 1997) — Swiss cheese model, human error
- **Klein, G.** (2007) — Premortem technique, prospective hindsight
- **Shostack, A.** (Threat Modeling, 2014) — STRIDE, threat modeling methodologies
- **Vesely, W. et al.** (Fault Tree Handbook, 1981) — Fault tree analysis methods

## Key Findings

### Risk Analysis
- Kaplan & Garrick: risk is not a single number; it's a set of triplets (scenario, likelihood, consequence)
- Risk matrix: likelihood × impact grid — but beware the "risk matrix fallacy" (ordinal scales don't multiply)
- Risk = hazard × exposure × vulnerability (in some domains)
- Key distinction: risk assessment (what could happen) vs. risk management (what to do about it)
- Unknown unknowns: the most dangerous risks are the ones you haven't identified
- Taleb's critique: conventional risk analysis underestimates tail risk systematically

### Premortem
- Klein's technique: imagine the plan/decision has failed; generate reasons why
- Prospective hindsight: imagining an event has occurred increases identification of reasons by ~30%
- Counteracts overconfidence and groupthink
- Procedure: individual generation first, then group sharing (prevents anchoring)
- Not a substitute for risk analysis; complements it by surfacing risks that formal analysis misses

### Threat Modeling
- STRIDE: Spoofing, Tampering, Repudiation, Information disclosure, Denial of service, Elevation of privilege
- Adversary model: capabilities, motivations, resources of potential attackers
- Trust boundaries: where data crosses from trusted to untrusted zones
- Attack trees: systematic decomposition of attack paths (structure mirrors fault trees)
- Key insight: threat modeling is about adversary reasoning, not just system analysis

### Fault Tree Analysis
- Top-down: start with the undesired event (top event), decompose into contributing causes
- AND gates: all inputs must occur; OR gates: any input is sufficient
- Minimal cut sets: smallest combinations of basic events that cause the top event
- Quantitative: assign failure probabilities to basic events; compute top event probability
- Common cause failures: events that defeat multiple branches simultaneously
- Key limitation: fault trees are static; event trees handle dynamic scenarios

## Method Boundaries

- **Risk vs. Uncertainty**: Risk has known probabilities (Knight); uncertainty does not. Use risk analysis when probabilities are estimable; use decision under uncertainty when they are not.
- **Premortem vs. Risk Analysis**: Premortem is prospective and imaginative; risk analysis is analytical and systematic. Both are needed for comprehensive risk assessment.
- **Threat Modeling vs. Fault Trees**: Threat modeling is adversary-focused; fault trees are failure-focused. Use threat modeling for security; use fault trees for reliability.
- **Fault Trees vs. Event Trees**: Fault trees are top-down from the undesired event; event trees are forward from an initiating event. Use both for comprehensive analysis.

## References

- Kaplan, S. & Garrick, B.J. (1981). On the quantitative definition of risk. Risk Analysis.
- Taleb, N.N. (2007). The Black Swan. Random House.
- Taleb, N.N. (2012). Antifragile. Random House.
- Reason, J. (1990). Human Error. Cambridge University Press.
- Reason, J. (1997). Managing the Risks of Organizational Accidents. Ashgate.
- Klein, G. (2007). Performing a project premortem. Harvard Business Review.
- Shostack, A. (2014). Threat Modeling: Designing for Security. Wiley.
- Vesely, W. et al. (1981). Fault Tree Handbook. U.S. Nuclear Regulatory Commission.