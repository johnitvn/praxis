# Assumption Checking

Identify, make explicit, and challenge the assumptions underlying reasoning.

## Purpose

Every reasoning process rests on assumptions — propositions accepted as true without proof. Unchecked assumptions are the most common source of reasoning failures.

## Why Assumptions Matter

An assumption is not necessarily wrong. But an unexamined assumption is a hidden risk. The goal is not to eliminate assumptions (impossible) but to make them explicit and assess their risk.

## Assumption Types

| Type | Description | Example |
|------|-------------|---------|
| **Factual** | Assumptions about what is true | "The database can handle 10k QPS" |
| **Causal** | Assumptions about cause and effect | "Adding caching will reduce latency" |
| **Structural** | Assumptions about how things are organized | "Teams are independent" |
| **Temporal** | Assumptions about time and sequence | "Migration will take 2 hours" |
| **Behavioral** | Assumptions about how people will act | "Users will adopt the new feature" |
| **Environmental** | Assumptions about the context | "The network is reliable" |
| **Value** | Assumptions about what matters | "Performance matters more than cost" |

## Procedure

### Step 1: Surface Assumptions

For each element of your reasoning, ask:
- What must be true for this to be valid?
- What am I taking for granted?
- What would surprise me if it were false?

### Step 2: Classify Assumptions

For each assumption, assess:
- **Impact**: If wrong, how much does it affect the conclusion?
- **Uncertainty**: How confident are you that it's true?
- **Verifiability**: Can you check it?

### Step 3: Prioritize

Focus on assumptions that are:
- High impact AND high uncertainty → Critical risk
- High impact AND low uncertainty → Worth verifying
- Low impact → Can accept

### Step 4: Challenge

For critical assumptions:
- Why do I believe this?
- What evidence supports it?
- What would disprove it?
- What if the opposite were true?

### Step 5: Mitigate

For critical uncertain assumptions:
- Verify: Can you check it now?
- Monitor: Can you detect if it's wrong later?
- Hedge: Can you make the conclusion robust to it being wrong?
- Escalate: Should you ask the user?

## Assumption Checklist

Before finalizing any significant conclusion:
- [ ] I have listed my key assumptions
- [ ] I have assessed the impact and uncertainty of each
- [ ] I have challenged the high-impact, high-uncertainty assumptions
- [ ] I have a plan for assumptions that cannot be verified now
- [ ] I can state what would happen if my most critical assumption is wrong

## Common Failure Modes

- **Invisible assumptions**: Not realizing you're making an assumption
- **Assumption blindness**: Seeing assumptions in others' reasoning but not your own
- **False certainty**: Treating assumptions as facts
- **Assumption overload**: Listing too many assumptions without prioritizing
- **Assumption paralysis**: Being so aware of assumptions that you can't reason at all