# Threat Modeling

## Purpose
Systematically identify and evaluate threats to a system by modeling the adversary's perspective — their goals, capabilities, and attack paths — to prioritize defenses.

## When to Use
When designing or reviewing a system that faces intentional adversaries (attackers, competitors, malicious insiders). When security is a requirement and you need to decide where to invest defensive resources. When the system handles sensitive data, controls critical infrastructure, or could cause harm if compromised. When you are building a system and want to "shift left" on security — finding threats during design rather than after deployment. When a security incident has occurred and you need to understand what other attack paths exist.

## When Not to Use
When the system has no meaningful adversary — threats are accidental (equipment failure, human error) rather than intentional. When the system is trivial and the attack surface is minimal. When the system is already fully hardened and threat modeling would not reveal new threats. When the threat landscape is so well-understood that modeling adds no value.

## Problem Signals
The problem description mentions "how could an attacker," "what are the security risks," "we need to protect," "what's the worst that could happen if someone malicious." The system handles authentication, authorization, sensitive data, or financial transactions. There is a regulatory requirement for security assessment. The system connects to the internet or untrusted networks.

## Inputs
- **System description**: the system being analyzed — architecture, components, data flows, trust boundaries, entry points
- **Assets**: what the system protects — data, functionality, reputation, availability
- **Adversary model**: who the attackers are, their goals, their capabilities, their resources (from script kiddies to nation-states)
- **Trust boundaries**: where trust levels change — between the internet and the application, between services, between users and the system

## Procedure
1. **Model the system**: create a diagram showing components, data flows, trust boundaries, and entry points. A data flow diagram (DFD) is the standard tool. Identify assets at each component.
2. **Define the adversary**: specify who you are defending against. Be concrete: "a remote attacker with no credentials," "a malicious insider with read access to the database," "a compromised third-party dependency." The adversary model determines which threats are in scope.
3. **Identify threats**: use a structured framework to enumerate threats. STRIDE is the standard: Spoofing (pretending to be someone else), Tampering (modifying data or code), Repudiation (denying an action), Information Disclosure (leaking data), Denial of Service (disrupting availability), Elevation of Privilege (gaining unauthorized access). For each element in the system diagram, ask: how could each STRIDE category apply?
4. **Assess threats**: for each identified threat, estimate likelihood and impact. Use a consistent scale. Consider the adversary's motivation and capability when estimating likelihood.
5. **Prioritize**: rank threats by risk (likelihood x impact). Focus on the top threats — the ones that are both plausible and consequential.
6. **Design mitigations**: for each high-priority threat, propose a countermeasure. Common mitigations: authentication, authorization, encryption, input validation, rate limiting, audit logging, network segmentation.
7. **Verify mitigations**: confirm that each mitigation actually addresses the threat and does not introduce new vulnerabilities.

## Output
A system diagram with trust boundaries and data flows. A threat list, each mapped to a STRIDE category and a system element. Threat priorities (likelihood and impact ratings). A set of recommended mitigations. A residual threat assessment after mitigations.

## Strengths
Adversary-aware — the method explicitly models the attacker's perspective, which is essential for security. Systematic and structured, reducing the chance of missing classes of threats. STRIDE provides a comprehensive taxonomy that covers the full threat landscape. The system diagram is a durable artifact that supports ongoing security analysis.

## Limitations
The adversary model is inherently uncertain — you may defend against the wrong adversary or underestimate capabilities. The threat landscape evolves as new attack techniques emerge, so the model degrades over time. STRIDE is comprehensive but can generate many low-value threats that create noise. The method requires significant domain expertise to apply well — a novice will miss subtle threats. The system diagram is a simplification and may miss edge cases.

## Common Failure Modes
Using a generic adversary model ("any attacker") that is too vague to guide prioritization. Identifying threats but not prioritizing them, producing a long list that nobody acts on. Focusing only on technical threats and ignoring social engineering, insider threats, and supply chain attacks. Modeling the system as designed, not as built — the gap between architecture diagrams and reality is where threats live. Treating threat modeling as a one-time activity rather than a continuous process. Assuming mitigations work perfectly without verifying them.

## Verification
Check that every element in the system diagram has been examined through each STRIDE category. Confirm that the adversary model is specific and documented. Verify that high-priority threats have concrete mitigations. Review whether the mitigations would actually stop the threat under realistic conditions. Test whether the model would have caught a known vulnerability in a similar system.

## Combine With
- **risk-analysis**: to quantify and prioritize threats within a broader risk framework
- **game-theoretic-analysis**: to model the adversary's strategic choices when defenses are visible
- **fault-tree-analysis**: to decompose how a threat could lead to a top-level system failure
- **attack-surface-analysis**: to complement threat modeling with a focus on entry points

## Conflicts With
- **optimism-bias**: threat modeling requires a pessimistic, adversarial mindset
- **user-centered-design**: user-centered design optimizes for ease of use; threat modeling often imposes friction for security

## Example
A team is designing a file-sharing service. The system diagram shows: web client, API gateway, auth service, file storage, database. Trust boundaries: between the internet and the API gateway, between services. Adversary: remote attacker with no credentials. STRIDE analysis on the API gateway: Spoofing — attacker forges JWTs (mitigation: validate signatures, short expiry). Tampering — attacker modifies files in transit (mitigation: TLS, checksums). Information Disclosure — attacker enumerates file IDs (mitigation: random UUIDs, authorization checks per file). Denial of Service — attacker floods the upload endpoint (mitigation: rate limiting, file size caps). Elevation of Privilege — attacker exploits a deserialization bug to gain admin access (mitigation: input validation, minimal deserialization, sandboxing). The top priority is the JWT forgery threat; the team implements strict JWT validation before the MVP launch.

## Selection Metadata
```
id: threat-modeling
category: risk
best_for: [security analysis, adversarial contexts, system design, defense prioritization]
requires: [system description, adversary model, assets, trust boundaries]
produces: [threat list, STRIDE mapping, threat priorities, mitigations, system diagram]
strengths: [adversary-aware, systematic, comprehensive taxonomy, durable artifact]
limitations: [adversary model uncertainty, evolving threats, requires expertise, diagram-reality gap]
combine_with: [risk-analysis, game-theoretic-analysis, fault-tree-analysis, attack-surface-analysis]
avoid_when: [no adversary exists, system is not attackable, threat landscape is already well-understood]
```