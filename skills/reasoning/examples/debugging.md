# Example: Debugging a Production Issue

## Problem

"Users are reporting intermittent 500 errors on the checkout page. It started about 2 hours ago. Error rate is ~5% of requests. The checkout service shows elevated latency. No recent deployments. Nothing obvious in the logs except 'Connection timeout' from the payment service."

## Classification

- **problem_type**: [what-caused-something]
- **uncertainty_profile**: epistemic (we can investigate)
- **stakes**: high (revenue-impacting, customer-facing)
- **reversibility**: N/A (diagnosis, not a decision)
- **domain**: software-engineering
- **structure**: well-defined system, unknown cause

## Selected Methods

1. **Abductive reasoning** — Generate hypotheses from symptoms
2. **Causal reasoning** — Trace symptoms to root cause
3. **Bayesian reasoning** — Update beliefs as evidence accumulates
4. **Bisection** — Isolate the fault to a specific component

## Reasoning Process

### Step 1: Observe and Characterize

**What we know**:
- Symptom: Intermittent 500 errors on checkout
- Timing: Started ~2 hours ago
- Scope: ~5% of requests, checkout service only
- Clue: "Connection timeout" from payment service
- Negative: No recent deployments (rules out code change)

**What we don't know**:
- Is the payment service healthy?
- Is the network between services healthy?
- Is there a resource constraint (connections, memory, CPU)?
- Did anything change externally (payment provider, DNS)?

### Step 2: Generate Hypotheses

**H1**: Payment service is degraded (high latency, causing timeouts)
**H2**: Network issue between checkout and payment service
**H3**: Connection pool exhaustion in checkout service
**H4**: Payment provider (external) is degraded
**H5**: Recent data change (e.g., configuration, feature flag, certificate expiry)

**Prior probabilities** (Bayesian):
- H1: 30% (most consistent with "connection timeout" + latency)
- H2: 15% (less likely if no other services affected)
- H3: 25% (connection timeouts often = pool exhaustion)
- H4: 20% (external dependency, no recent changes internally)
- H5: 10% (no deployments, but config changes are possible)

### Step 3: Gather Discriminating Evidence

**Tests to run**:
1. Check payment service metrics (latency, error rate, connections) → Tests H1, H3
2. Check network metrics between services → Tests H2
3. Check connection pool metrics in checkout → Tests H3
4. Check payment provider status page → Tests H4
5. Check recent config changes → Tests H5

### Step 4: Test and Eliminate

**Evidence gathered**:
- Payment service latency: Normal (p99 = 50ms) → weakens H1
- Payment service error rate: Normal → weakens H1
- Network: No packet loss, latency normal → weakens H2
- Connection pool in checkout: 100% utilized, 50 connections, max = 50 → **STRONG signal for H3**
- Payment provider status: Operational → weakens H4
- Config changes: No changes in last 24 hours → weakens H5

**Updated beliefs** (Bayesian update):
- H3 (connection pool exhaustion): 85% ← **Primary hypothesis**
- H1: 5%
- H2: 2%
- H4: 5%
- H5: 3%

### Step 5: Confirm Root Cause

**Why did connection pool exhaust?**
- Pool size was set to 50
- Normal load uses ~30 connections
- Checkout traffic increased 2x (Friday afternoon shopping surge)
- Each request holds a connection longer due to a slow external address validation API

**Root cause**: Connection pool too small for peak load + slow downstream dependency

### Step 6: Fix and Verify

**Immediate fix**: Increase connection pool to 100
**Verification**: Pool utilization dropped to 60%, error rate dropped to 0%
**Long-term fix**: Add circuit breaker for slow downstream, implement connection pool monitoring and auto-scaling

## Verification

- [x] Error rate returned to 0% after fix
- [x] Connection pool utilization stable at 60%
- [x] No new errors introduced
- [x] Monitoring alert added for pool utilization > 80%
- [x] Post-mortem scheduled to address the slow downstream dependency

## Method Reflection

This was a classic **Hypothesis-Driven Diagnosis** pattern:
1. Abductive reasoning generated hypotheses
2. Bayesian reasoning tracked belief updates
3. Causal reasoning confirmed the mechanism
4. Bisection isolated the fault to the connection pool

The key insight was recognizing that "connection timeout" + "no other service affected" + "intermittent" strongly suggested a resource constraint rather than a service failure. The Bayesian framework prevented anchoring on the payment service (the most obvious but wrong suspect).