# Example: Software Architecture Decision

## Problem

"We need to choose a primary datastore for our new microservices platform. We have 5 engineering teams, each with different data access patterns. We expect 100k QPS at peak, p99 latency must be under 10ms for reads. The decision will be hard to reverse once we've built on it. We're currently using PostgreSQL and some teams want to stay with it, while others want to try DynamoDB or CockroachDB."

## Classification

**Using classify-problem.md**:
- **problem_type**: [what-to-do, how-to-achieve]
- **uncertainty_profile**: epistemic (we can research, test)
- **stakes**: high (hard to reverse, affects all teams)
- **reversibility**: irreversible (or very expensive to reverse)
- **domain**: software-engineering
- **structure**: multi-stakeholder, well-defined constraints

## Selected Methods

**Using select-method.md**:
1. **Constraint analysis** — Define hard requirements (latency, QPS, consistency)
2. **Multi-criteria decision** — Evaluate options across multiple dimensions
3. **Trade-off analysis** — Understand what we give up with each option
4. **Risk analysis** — Identify what could go wrong with each choice
5. **Premortem** — Imagine the decision failed — why?

## Method Composition

**Chain** (using compose-methods.md):
```
Constraint Analysis → Multi-Criteria Decision → Trade-off Analysis → Risk Analysis → Premortem → Decision
```

## Reasoning Process

### Step 1: Constraint Analysis

**Hard constraints**:
- p99 read latency < 10ms
- 100k QPS peak
- Must support 5 teams with different access patterns
- Data durability (no data loss)

**Soft constraints**:
- Teams prefer SQL (but can adapt)
- Operational simplicity
- Cost efficiency

### Step 2: Multi-Criteria Decision

**Criteria** (weighted):
- Performance (30%): Latency, throughput
- Reliability (25%): Durability, availability, consistency
- Operational (20%): Ease of operation, monitoring, backup
- Developer experience (15%): Query flexibility, familiar paradigm
- Cost (10%): Total cost of ownership

**Options evaluated**:
- PostgreSQL (status quo)
- DynamoDB
- CockroachDB
- Hybrid (PostgreSQL + DynamoDB for different workloads)

### Step 3: Trade-off Analysis

Key trade-offs identified:
- **SQL flexibility vs. NoSQL scalability**: PostgreSQL gives teams SQL; DynamoDB scales more predictably
- **Consistency vs. latency**: Strong consistency adds latency; eventual consistency is faster but harder to reason about
- **Single vs. multi-datastore**: One datastore is simpler; two datastores can be optimized per workload

### Step 4: Risk Analysis

Top risks:
1. **PostgreSQL at 100k QPS**: Can it scale? Risk of performance degradation
2. **DynamoDB lock-in**: AWS-specific; hard to migrate
3. **Team productivity**: Learning curve with new datastore
4. **Data consistency bugs**: If using eventual consistency

### Step 5: Premortem

"Imagine it's 18 months from now. The datastore decision was a disaster. Why?"

Findings:
- PostgreSQL couldn't handle the peak load, and we had to do an emergency migration
- The team that pushed for DynamoDB didn't realize they'd need complex joins
- We underestimated operational complexity of running a distributed database
- We didn't test at production scale before deciding

### Step 6: Decision

**Recommendation**: CockroachDB
- Meets performance requirements (tested at 150k QPS)
- PostgreSQL-compatible SQL (teams keep their workflow)
- Distributed by default (no single point of failure)
- Multi-region support (future-proof)

**Confidence**: 80%
**Key uncertainty**: Operational complexity at scale (mitigated by gradual rollout)
**What would change the decision**: If CockroachDB fails production load testing

## Verification

- [x] Load tested at 2x expected peak
- [x] Each team evaluated the query patterns they need
- [x] Operational runbook drafted
- [x] Migration plan documented
- [x] Rollback plan exists (not easy, but possible)
- [x] Decision reviewed by infrastructure team lead

## Result

The structured approach revealed that:
1. The "status quo" option (PostgreSQL) had the highest risk of failure at scale
2. Teams were anchoring on what they knew, not what the system needed
3. The premortem revealed failure modes that the analysis alone missed
4. A gradual rollout with performance testing at each stage was the safe path