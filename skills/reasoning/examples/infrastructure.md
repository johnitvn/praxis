# Example: Infrastructure Decision

## Problem

"We run 200 microservices on Kubernetes. Our incident rate has increased 3x in the last quarter as the system has grown. Most incidents are cascading failures: one service goes down, calls timeout, callers exhaust their connection pools, and the failure cascades. We need to improve system resilience."

## Classification

- **problem_type**: [what-caused-something, what-to-do]
- **uncertainty_profile**: mixed (we understand the pattern but not all interactions)
- **stakes**: high (reliability, customer impact)
- **reversibility**: somewhat reversible (can change architecture incrementally)
- **domain**: infrastructure
- **structure**: dynamic, interconnected, complex

## Selected Methods

1. **Systems thinking** — Map the system and identify feedback loops and vulnerabilities
2. **Fault tree analysis** — Trace cascading failures to root causes
3. **Risk analysis** — Identify and prioritize failure modes
4. **Constraint analysis** — Define what must be true of any solution
5. **Trade-off analysis** — Balance resilience against cost and complexity

## Reasoning Process

### Step 1: Systems Thinking

**System map**:
- 200 services, 50 "critical path" services
- Synchronous HTTP calls between services (no message queue)
- Default timeouts (30s) are too long
- No circuit breakers
- Connection pools sized for normal load, not degraded load
- Retry logic without backoff or jitter

**Feedback loops identified**:
- **Reinforcing loop**: Service A slow → Service B waits → Service B's connection pool fills → Service B times out for other callers → Service C, D, E also fail
- **Reinforcing loop**: Service fails → retries → more load on failing service → fails harder
- **Balancing loop**: Kubernetes restarts pods → temporarily reduces capacity → more load on remaining pods → they also fail

**Leverage points**:
- Circuit breakers (stop the cascade at the source)
- Shorter timeouts (fail fast instead of slow)
- Retry with backoff + jitter (reduce thundering herd)
- Bulkheads (isolate failures to one part of the system)

### Step 2: Fault Tree Analysis

**Top event**: Cascading failure affecting multiple services

**AND gate**: Service A fails AND Service B is vulnerable to Service A's failure

**Service A failure causes** (OR gate):
- Resource exhaustion (CPU, memory, connections)
- Dependency failure (database, downstream service)
- Deployment issue (bad config, bad code)
- Traffic spike (thundering herd, DDoS)

**Service B vulnerability causes** (OR gate):
- No circuit breaker
- Timeout too long
- Connection pool too small
- No retry backoff
- Synchronous dependency on A

**Minimal cut sets** (minimum combinations that cause the top event):
1. The most common cut set: {No circuit breaker, Timeout > acceptable delay}
2. {No circuit breaker, Connection pool exhaustion}
3. {Retry without backoff, Service A degraded}

### Step 3: Risk Analysis

**Risk register**:

| Risk | Likelihood | Impact | Priority |
|------|-----------|--------|----------|
| Cascading failure from circuit breaker absence | High | Critical | **P0** |
| Retry storms | High | High | **P0** |
| Connection pool exhaustion | Medium | High | **P1** |
| Long timeouts causing thread starvation | Medium | High | **P1** |
| Single point of failure in critical path | Medium | Critical | **P1** |
| Lack of observability during cascades | High | Medium | **P2** |

### Step 4: Constraint Analysis

**Hard constraints**:
- Must not increase p99 latency > 10% in normal operation
- Must not require rewriting all services (incremental adoption)
- Must not introduce new single points of failure
- Must be operable by the current team (no new specialized skills required)

**Feasible region**: Solutions that improve resilience without requiring a full rewrite, introducing significant latency, or adding operational complexity the team can't handle.

### Step 5: Trade-off Analysis

**Options evaluated**:

| Option | Resilience Gain | Implementation Cost | Latency Impact | Operational Complexity |
|--------|----------------|-------------------|----------------|------------------------|
| Circuit breakers | High | Medium | None | Low |
| Shorter timeouts | High | Low | None | Low |
| Retry with backoff | High | Low | Slight | Low |
| Service mesh (Istio) | Very High | High | Slight | High |
| Message queue (async) | Very High | Very High | Increases | High |
| Bulkheads | Medium | Medium | None | Medium |

**Dominated options eliminated**:
- Full async rewrite: Eliminated (too expensive, violates incremental constraint)
- Service mesh: Not eliminated but deferred (high operational complexity)

### Step 6: Decision

**Recommendation**: Phased approach

**Phase 1 (Immediate — 2 weeks)**: "Quick wins" that address the highest-priority risks
1. Add circuit breakers to all critical-path services (library-level, not service mesh)
2. Reduce default timeouts from 30s to 5s
3. Add exponential backoff + jitter to all retries

**Phase 2 (Medium-term — 1 month)**:
1. Right-size connection pools for degraded mode
2. Implement bulkheads for critical-path services
3. Add observability for circuit breaker state, retry rates, connection pool utilization

**Phase 3 (Long-term)**: Evaluate service mesh if needed

**Confidence**: 85%
**Key uncertainty**: Whether library-level circuit breakers are sufficient or a service mesh is needed
**What would change the decision**: If Phase 1 doesn't reduce cascading failures by >80%

## Verification

- [x] Fault tree analysis identified root causes, not just symptoms
- [x] Solutions address the highest-priority risks first
- [x] Phased approach respects constraints (incremental, team capability)
- [x] Success criteria defined (>80% reduction in cascading failures)
- [x] Monitoring plan for Phase 1 effectiveness
- [x] Fallback: If Phase 1 insufficient, accelerate service mesh evaluation

## Result

Phase 1 reduced cascading failures by 85% within 2 weeks. The circuit breakers stopped the cascade propagation, shorter timeouts prevented connection pool exhaustion, and retry backoff eliminated the thundering herd. The service mesh was never needed. The key insight from the systems thinking analysis was that the system had reinforcing feedback loops that amplified small failures — and the fix was to break those loops, not to make individual services more reliable.