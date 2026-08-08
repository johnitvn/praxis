# Example: Research Investigation

## Problem

"We need to understand whether Rust or Go is the right choice for our new high-throughput data processing service. We need to process 1M events/second with p99 latency under 5ms. The team has experience in Python and Java, not Rust or Go. We need a recommendation with clear rationale."

## Classification

- **problem_type**: [what-is-true, what-to-do]
- **uncertainty_profile**: epistemic (can research, benchmark)
- **stakes**: high (language choice is hard to reverse)
- **reversibility**: hard to reverse (rewriting is expensive)
- **domain**: software-engineering
- **structure**: well-defined, evidence-based

## Selected Methods

1. **Evidence evaluation** — Assess quality of claims about each language
2. **Literature review** — Survey existing comparisons and case studies
3. **Evidence synthesis** — Combine findings into coherent assessment
4. **Trade-off analysis** — Compare languages across dimensions
5. **Uncertainty quantification** — Be explicit about what we don't know

## Reasoning Process

### Phase 1: Question Formulation

**Primary question**: For a high-throughput (1M events/s), low-latency (p99 < 5ms) data processing service, should we use Rust or Go?

**Sub-questions**:
1. Which language meets the performance requirements?
2. Which language has better ecosystem for data processing?
3. Which language has a gentler learning curve for Python/Java developers?
4. What are the operational characteristics of each? (debugging, profiling, deployment)
5. What do teams with similar requirements use?

### Phase 2: Search and Source Evaluation

**Sources identified**:
- Official language documentation and benchmarks
- TechEmpower benchmarks (independent, standardized)
- Case studies from Discord, Cloudflare, Dropbox (Rust); Uber, Twitch, Kubernetes (Go)
- Developer surveys (Stack Overflow, JetBrains)
- Published comparisons (authoritative tech blogs, not opinion pieces)

**Source quality assessment**:
- High quality: Official docs, TechEmpower benchmarks, detailed case studies
- Medium quality: Developer surveys, published comparisons
- Low quality: Reddit/HN threads, unsupported claims

### Phase 3: Evidence Extraction

**Performance**:
- Rust: Consistently top-tier in benchmarks. Zero-cost abstractions. No GC pauses.
- Go: Very good performance. Occasional GC pauses. Generally 2-3x slower than Rust for CPU-bound work.
- For our use case (1M events/s, p99 < 5ms): Both are capable. Rust has more headroom. Go's GC may cause latency spikes.

**Ecosystem**:
- Rust: Strong data processing libraries (tokio, rayon, serde). Growing ecosystem. Smaller community.
- Go: Excellent concurrency primitives. Mature standard library. Large ecosystem. Strong cloud-native tooling.
- For our use case: Go has more mature data processing ecosystem. Rust's ecosystem is younger but adequate.

**Learning curve**:
- Rust: Steep. Borrow checker is a new concept. 3-6 months to productivity.
- Go: Gentle. 2-4 weeks to productivity for experienced developers.
- For our team (Python/Java): Go is significantly easier. Rust's learning curve is a real cost.

**Operational**:
- Rust: Excellent debugging (gdb, lldb). Excellent profiling (perf, flamegraph). Binary deployment.
- Go: Excellent debugging (delve). Excellent profiling (pprof). Binary deployment. Superior observability ecosystem.
- For our use case: Both are strong. Go has slightly better observability tooling.

### Phase 4: Triangulation

**Cross-checking claims**:
- "Rust is always faster than Go" → Mostly true for CPU-bound, but Go is competitive for I/O-bound. Our workload is mixed.
- "Go's GC is a problem for low latency" → True at p99. GC pauses can exceed 5ms. Go 1.19+ has improved this.
- "Rust is too hard for teams" → Contested. Discord and Cloudflare report successful adoption. Learning curve is real but surmountable.

### Phase 5: Synthesis

**Trade-off analysis**:

| Dimension | Rust | Go |
|-----------|------|-----|
| Raw performance | Superior | Very good |
| Latency predictability | Superior (no GC) | Good (GC improvements ongoing) |
| Developer productivity | Lower initially | Higher initially |
| Hiring difficulty | Harder | Easier |
| Ecosystem maturity | Growing | Mature |
| Operational tooling | Good | Excellent |
| Long-term performance headroom | High | Moderate |

**Key finding**: Both languages meet the technical requirements. The decision is primarily about team dynamics and risk tolerance.

### Phase 6: Uncertainty Assessment

**What we're confident about**:
- Both languages can meet the performance requirements
- Go has a significantly easier learning curve
- Rust has more predictable latency (no GC)
- Go has a more mature ecosystem

**What we're uncertain about**:
- Actual performance on our specific workload (haven't benchmarked)
- Team's ability to learn Rust within the timeline
- Long-term maintenance cost of each

### Phase 7: Recommendation

**Recommendation**: Go, with Rust as a fallback if Go's GC proves problematic.

**Rationale**:
1. Go meets the performance requirements (with monitoring)
2. Go's learning curve is 1/10th of Rust's for the team
3. Go's ecosystem is more mature for data processing
4. Go's operational tooling is superior
5. The risk of GC latency spikes can be mitigated and monitored
6. If Go's GC is a problem, we can rewrite the hot path in Rust (via cgo or separate service)

**Recommendation confidence**: 75%
**Key uncertainty**: Go GC pause behavior at our specific workload
**Mitigation**: Benchmark with production-like workload before committing
**What would change the recommendation**: If Go benchmarks show p99 latency > 5ms due to GC

## Verification

- [x] Multiple independent sources consulted
- [x] Claims cross-checked across sources
- [x] Both languages evaluated against our specific requirements
- [x] Team context considered (not just technical comparison)
- [x] Fallback plan documented
- [x] Key uncertainties identified with mitigation plan
- [x] Benchmark plan created before final commitment

## Result

The team benchmarked Go with a production-like workload and found that Go 1.21's GC pauses were under 1ms at p99, well within the 5ms requirement. The Go recommendation was confirmed. The team was productive in Go within 3 weeks. The structured research approach prevented a premature decision based on "Rust is faster" without considering the team context.