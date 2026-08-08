# Bias Detection

Detect cognitive biases in your own reasoning.

## Purpose

Cognitive biases are systematic patterns of deviation from normatively correct reasoning. They affect everyone, including AI agents. The first step in mitigating bias is detecting it.

## Bias Categories

### 1. Information Processing Biases

| Bias | Description | Detection Question |
|------|-------------|-------------------|
| **Anchoring** | Over-relying on the first piece of information | Did I start with a number or estimate? |
| **Availability** | Overweighting easily recalled information | Am I weighting recent/vivid examples too heavily? |
| **Framing** | Being influenced by how information is presented | Would I decide differently if this were framed differently? |
| **Base rate neglect** | Ignoring base rates in favor of specific information | What is the base rate? |

### 2. Belief Biases

| Bias | Description | Detection Question |
|------|-------------|-------------------|
| **Confirmation bias** | Seeking evidence that confirms existing beliefs | Am I looking for evidence against my view? |
| **Belief perseverance** | Maintaining beliefs despite contrary evidence | What evidence would change my mind? |
| **Overconfidence** | Excessive confidence in one's own judgments | What is my calibration? |
| **Hindsight bias** | Seeing past events as more predictable than they were | Would I have predicted this beforehand? |

### 3. Decision Biases

| Bias | Description | Detection Question |
|------|-------------|-------------------|
| **Sunk cost** | Continuing because of past investment | Would I choose this if I were starting fresh? |
| **Loss aversion** | Overweighting losses relative to gains | Am I disproportionately afraid of losses? |
| **Status quo bias** | Preferring things to stay the same | Is "no change" actually better? |
| **Endowment effect** | Overvaluing what you already have | Would I pay this much for it if I didn't own it? |

### 4. Social Biases

| Bias | Description | Detection Question |
|------|-------------|-------------------|
| **Groupthink** | Conforming to group consensus | Am I agreeing because others do? |
| **Authority bias** | Overweighting authority opinions | Am I evaluating the argument or the source? |
| **Halo effect** | Letting one positive trait color everything | Am I generalizing from one good quality? |

## Procedure

### Step 1: Bias Scan

Before finalizing a conclusion, scan for biases:
- Run through the categories above
- Ask the detection questions
- Note any that trigger

### Step 2: Bias-Specific Mitigation

| Bias | Mitigation |
|------|-----------|
| Anchoring | Generate estimate from scratch, compare |
| Confirmation | Actively search for disconfirming evidence |
| Overconfidence | Calibrate against past accuracy |
| Sunk cost | Reframe: "What would I do if starting fresh?" |
| Framing | Reframe the problem in multiple ways |
| Base rate neglect | Explicitly compute base rate |
| Groupthink | Play devil's advocate |
| Availability | Ask: "What am I not thinking of?" |

### Step 3: Structural Mitigations

These help regardless of which bias is present:
- **Consider the opposite**: What if the opposite conclusion were true?
- **Pre-mortem**: Imagine the conclusion was wrong — why?
- **Outside view**: What would a typical case look like?
- **Independent red team**: Have another process critique the reasoning

## Common Failure Modes

- **Bias blindness**: "I'm not biased" — everyone is
- **Bias whack-a-mole**: Fixing one bias while introducing another
- **Overcorrection**: Over-adjusting for a detected bias
- **Bias fatigue**: Giving up because biases are everywhere
- **Using bias labels as conclusions**: "That's just confirmation bias" without actually re-evaluating