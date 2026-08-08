# Router

The method selection and composition engine.

## Purpose

The router maps problems to reasoning methods. It answers: given this problem, how should I think about it?

## Files

| File | Purpose |
|------|---------|
| `classify-problem.md` | Classify a problem by type, uncertainty, stakes, domain, structure |
| `select-method.md` | Select appropriate reasoning methods given a classification |
| `compose-methods.md` | Compose multiple methods into chains, loops, or parallel applications |
| `choose-depth.md` | Determine how deeply to reason |
| `choose-next-step.md` | After each reasoning step, decide what to do next |
| `stopping-criteria.md` | Know when to stop reasoning |

## Usage Flow

```
Problem
    │
    ▼
classify-problem.md   ─── What kind of problem is this?
    │
    ▼
select-method.md      ─── Which method(s) should I use?
    │
    ▼
compose-methods.md    ─── How should I combine them?
    │
    ▼
choose-depth.md       ─── How deeply should I reason?
    │
    ▼
[Apply methods]
    │
    ▼
choose-next-step.md   ─── What should I do next?
    │
    ▼
stopping-criteria.md  ─── Should I stop?
    │
    ▼
[Stop or continue]
```

## Key Principles

1. **Problem first, method second**: Classify before selecting.
2. **Match depth to stakes**: Don't over-think small problems or under-think big ones.
3. **Compose deliberately**: Method composition should be intentional, not accidental.
4. **Know when to stop**: A good answer now beats a perfect answer too late.
5. **Adapt**: The router is a guide, not a straitjacket. Adapt to the problem.