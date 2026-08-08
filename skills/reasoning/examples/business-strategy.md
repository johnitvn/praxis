# Example: Business Strategy Decision

## Problem

"Our SaaS company has been growing at 30% YoY serving mid-market customers. We're at $20M ARR. We need to decide our growth strategy for the next 3 years: should we move upmarket to enterprise, expand internationally, or double down on mid-market? We have $50M in funding and 200 employees."

## Classification

- **problem_type**: [what-to-do]
- **uncertainty_profile**: knightian (fundamental uncertainty about future markets)
- **stakes**: critical (determines company direction for years)
- **reversibility**: hard to reverse (hiring, product, brand decisions compound)
- **domain**: business-strategy
- **structure**: multi-stakeholder, competitive, dynamic

## Selected Methods

1. **Strategic analysis** — Assess competitive position, market attractiveness
2. **Scenario planning** — Build multiple futures, test robustness
3. **Decision under uncertainty** — Strategy is inherently uncertain
4. **Option reasoning** — Value flexibility and staged commitment
5. **Premortem** — Challenge each strategy before committing

## Reasoning Process

### Step 1: Strategic Analysis

**External analysis**:

*Mid-market* (current):
- Market size: $5B, growing 15% YoY
- Competition: Fragmented, 3 major competitors
- Our position: #2 with 15% market share
- Customer economics: $50k ACV, 12-month payback, 110% NRR

*Enterprise* (upmarket):
- Market size: $20B, growing 10% YoY
- Competition: 2 dominant incumbents, high barriers
- Our position: No presence
- Customer economics: $200k ACV, 18-month payback, 120% NRR (estimated)
- Requirements: Enterprise sales team, SOC2/HIPAA, dedicated support

*International* (expansion):
- Market size: $15B (target regions), growing 20% YoY
- Competition: Local competitors in each region
- Our position: No presence
- Customer economics: $40k ACV, 15-month payback, 105% NRR (estimated)
- Requirements: Localization, regional sales, compliance

**Internal analysis**:
- Strengths: Strong mid-market product, efficient sales motion, high NPS
- Weaknesses: No enterprise sales capability, no international presence, product lacks enterprise features
- Opportunities: Enterprise market is larger, international is growing faster
- Threats: Mid-market competitors consolidating, enterprise incumbents may move downmarket

### Step 2: Scenario Planning

**Key uncertainties**:
1. Will enterprise incumbents move downmarket? (High uncertainty, high impact)
2. Will international markets consolidate? (Medium uncertainty, medium impact)
3. Will mid-market growth continue? (Medium uncertainty, high impact)

**Four scenarios** (2×2 matrix: "Enterprise Competition" × "Mid-Market Growth"):

| | Enterprise Incumbents Stay Upmarket | Enterprise Incumbents Move Down |
|---|---|---|
| **Mid-Market Growth Continues** | Scenario A: "Golden Age" — All strategies viable | Scenario B: "Defend the Core" — Mid-market under attack, enterprise blocked |
| **Mid-Market Growth Slows** | Scenario C: "Up or Out" — Must move upmarket | Scenario D: "Existential Threat" — Attacked on both fronts |

### Step 3: Strategy Robustness Assessment

**Option 1: Double down on mid-market**

| Scenario | Viability |
|----------|-----------|
| A (Golden Age) | ✅ Excellent |
| B (Defend Core) | ⚠️ Viable but under pressure |
| C (Up or Out) | ❌ Declining market |
| D (Existential) | ❌ Attacked from both sides |

**Robustness**: Mediocre. Only works in favorable scenarios.

**Option 2: Move upmarket to enterprise**

| Scenario | Viability |
|----------|-----------|
| A (Golden Age) | ✅ Good |
| B (Defend Core) | ⚠️ Difficult (competition from incumbents) |
| C (Up or Out) | ✅ Best option |
| D (Existential) | ⚠️ Difficult but necessary |

**Robustness**: Good. Works in most scenarios, especially the dangerous ones.

**Option 3: Expand internationally**

| Scenario | Viability |
|----------|-----------|
| A (Golden Age) | ✅ Good |
| B (Defend Core) | ✅ Good (diversification) |
| C (Up or Out) | ⚠️ Doesn't address core vulnerability |
| D (Existential) | ⚠️ Doesn't address enterprise threat |

**Robustness**: Moderate. Good diversification but doesn't address the main threat.

### Step 4: Option Reasoning

**Key insight**: The decision is not binary. We can stage our commitment.

**Option value of starting enterprise now**:
- Start with 5 enterprise deals (12 months)
- If successful, scale enterprise team (creates option to go all-in)
- If unsuccessful, we've learned and can pivot
- Cost: ~$5M (5% of funding)
- This is a real option — small investment to create a large future opportunity

**Option value of international**:
- Start with 1 region (UK/English-speaking)
- 6-month pilot
- If successful, expand to 3 more regions (creates scaling option)
- Cost: ~$3M

### Step 5: Premortem

**"We chose to double down on mid-market. It's 3 years later. The company is struggling. Why?"**

1. Two enterprise incumbents launched "mid-market" versions at half our price
2. Mid-market growth slowed as the segment matured
3. We had no diversification and no enterprise capability to pivot
4. Our best salespeople left because there was no career growth selling to mid-market
5. We were acquired for 1/3 of our peak valuation

**"We chose to go enterprise. It's 3 years later. It failed. Why?"**

1. We underestimated the enterprise sales cycle (24 months, not 12)
2. Our product lacked 30+ features that enterprise RFPs require
3. We lost mid-market focus and our core business declined
4. Our mid-market culture clashed with enterprise customers
5. We spent $30M and had nothing to show

**"We chose international. It's 3 years later. It failed. Why?"**

1. Each region required near-complete product rebuilds (compliance, language, payments)
2. Local competitors had deeper customer relationships
3. We spread too thin — 5 regions, no critical mass in any
4. Mid-market back home was neglected and competitors took share

### Step 6: Decision

**Recommendation**: Staged approach — "Protect the core, option on enterprise"

1. **Protect mid-market**: Continue investing in core (60% of resources)
2. **Enterprise option**: Start 5-enterprise-deal pilot (25% of resources, $5M)
3. **International scout**: One region, 6-month pilot (15% of resources, $3M)
4. **Decision points**:
   - Month 12: Review enterprise pilot. If 3+ deals closed, scale. If not, pivot.
   - Month 6: Review international pilot. If strong PMF, continue. If not, exit.

**Rationale**:
- The premortems revealed that each pure-play strategy has a plausible failure mode
- The enterprise threat (Scenario B/D) is the most dangerous
- The enterprise option creates a hedge against the most dangerous scenarios
- We preserve the core business while building options
- Clear decision points prevent escalation of commitment

**Confidence**: 70% (high uncertainty is inherent in strategy)
**Key uncertainty**: Enterprise sales cycle length and win rate
**What would change the decision**: If enterprise pilot shows <1 deal in 12 months, exit enterprise

## Verification

- [x] Each strategy tested against multiple scenarios
- [x] Premortems revealed failure modes for each option
- [x] Staged approach preserves flexibility
- [x] Clear decision points with criteria
- [x] Core business protected during exploration
- [x] Resource allocation is explicit and monitored

## Result

After 12 months:
- Enterprise pilot: 4 deals closed, ACV $180k, sales cycle 14 months (longer than expected but workable)
- International pilot: UK market showed strong PMF, 30 customers
- Decision: Scale enterprise to 30% of resources, international to 20%, mid-market to 50%
- The staged approach prevented the "bet the company" risk while building real options

The key insight was that **option reasoning** transformed an "all or nothing" strategy decision into a portfolio of staged investments with clear exit criteria. The premortems were essential in revealing that each strategy had a plausible failure mode — which justified the staged approach over a full commitment.