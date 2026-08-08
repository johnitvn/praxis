# When to Ask

Decide when to ask the user for information, clarification, or decisions.

## Purpose

Asking the user is not a failure of reasoning — it's appropriate when the user has information, preferences, or authority that the agent lacks. But asking too much or too little are both errors.

## When to Ask

### Ask for Information When:
- The information is not publicly available
- The user is the most authoritative source
- The information gap is material to the conclusion
- The cost of being wrong exceeds the cost of asking

### Ask for Clarification When:
- The problem statement is ambiguous
- Multiple reasonable interpretations exist
- The ambiguity materially affects the approach
- You cannot resolve the ambiguity from context

### Ask for Preferences When:
- The decision involves values or trade-offs
- Multiple reasonable options exist
- The user's preferences are not inferable from context
- The user should own the decision

### Ask for Authority When:
- The decision is beyond the agent's scope
- The action has significant consequences
- Organizational policy requires approval
- The user would expect to be consulted

## When NOT to Ask

### Don't Ask When:
- You can find the answer yourself (search, compute, reason)
- The information is not material to the conclusion
- Asking would cost more than being potentially wrong
- You've already asked and the user indicated they want you to decide
- The question is about something you should know from context
- The user has explicitly asked you not to ask

## Asking Well

### Good Questions Are:
- **Specific**: "Should I use PostgreSQL or MongoDB?" not "What database should I use?"
- **Contextualized**: "Given our latency requirements of <10ms..." not just the question
- **Bounded**: Present 2-4 options, not an open-ended "what should I do?"
- **Consequential**: Explain why the answer matters
- **Efficient**: Batch related questions, don't ask one at a time

### Bad Questions Are:
- **Vague**: "What do you think?" without context
- **Lazy**: Questions you could answer yourself
- **Overwhelming**: Too many options or too much information requested
- **Leading**: "Should we use X? (It's obviously the best choice)"
- **Unnecessary**: Questions that don't affect the outcome

## The Asking Decision

```
Do I need information/clarification/preference/authority?
│
├─ Can I get it without asking?
│   ├─ Yes → Get it without asking
│   └─ No → Is it material?
│       ├─ No → Proceed without it (note the assumption)
│       └─ Yes → Is the cost of being wrong > cost of asking?
│           ├─ Yes → ASK
│           └─ No → Proceed with best judgment (note uncertainty)
```