# Explanation Adaptation

This skill adapts explanation depth and style to the user's familiarity with each topic. This file defines how to track familiarity, how to switch depth levels, and how to infer the right style from the conversation.

---

## Three depth levels

### Simple
Use when the user is unfamiliar with the domain, technology, or pattern being discussed.

Characteristics:
- Lead with analogy or real-world parallel before using technical terms
- Avoid jargon — if a term is necessary, define it immediately
- Emphasize the "why" over the "how"
- Keep examples concrete and close to the user's experience
- Don't assume knowledge of adjacent technologies

**Example (explaining pub/sub):**
> "Think of it like a newspaper subscription. Publishers write articles and drop them into a distribution center. Subscribers sign up for specific topics and get notified when something relevant arrives. Neither side needs to know who's on the other end — the distribution center handles the routing. In this codebase, that distribution center is the event bus."

### Balanced
Use when the user has working software knowledge but is new to this specific system or domain.

Characteristics:
- Use technical terms without defining every one
- Explain the domain-specific reasoning, not just the mechanism
- Mix business context with implementation detail
- Assume general programming knowledge; don't assume project-specific knowledge

### Deep
Use when the user has strong familiarity with the technology and domain and wants precise, detailed explanation.

Characteristics:
- Go directly to mechanism — skip the business preamble once it's established
- Reference specific functions, types, and data structures by name
- Discuss tradeoffs, edge cases, and non-obvious behavior
- Treat the user as a peer who can fill in context themselves

---

## Per-topic familiarity tracking

Track familiarity per topic area, not as a single global level. A developer may be a React expert and a Solidity beginner. Don't assume overall skill level maps to every domain.

Track each topic independently:

```
Familiarity map:
  React:           high
  Node.js:         high
  Solidity:        low
  NFT standards:   low
  Database schema: medium
  Business domain: unknown
```

Update familiarity based on signals in the conversation:

**Signals of high familiarity:**
- User uses correct terminology unprompted
- User asks questions about edge cases or tradeoffs, not basics
- User's mental model is already close to correct when they verify it
- User skips over explanations ("yeah I know how JWT works, skip to how this app uses it")

**Signals of low familiarity:**
- User asks what a basic term means
- User's understanding verification contains fundamental errors
- User asks "why does it work that way?" about standard patterns
- User is surprised by expected behavior

**Signals of medium familiarity:**
- User follows explanations without questions
- User asks follow-ups at the functional level, not the deep implementation level
- User's verification shows correct high-level model but misses implementation detail

---

## Style switching

The user can ask to change explanation style at any time. Apply the change immediately and maintain it for the rest of the session.

| User says | How to respond |
|---|---|
| "Explain it simpler" / "I'm lost" | Switch to Simple. Add analogy. Back up one level. |
| "More technical please" / "Get into the details" | Switch to Deep. Go to mechanism and code-level specifics. |
| "Business-first" | Lead with problem/impact/users before any implementation. |
| "Code-first" / "Just show me where in the code" | Lead with file/function/line, then explain what it does. |
| "More detail on X" | Expand the current topic before moving forward. |
| "Keep it high-level" | Skip the implementation layer. Stay at architecture and functional behavior. |

---

## Inferring depth from behavior

When the user doesn't explicitly state a preference, infer it from the conversation:

- If they ask follow-up questions at the business level → stay in Simple/Balanced
- If they ask "but how exactly does it do that?" → move toward Deep
- If they verify their understanding with accurate technical detail → stay in Deep
- If they verify with inaccurate detail → move toward Balanced or Simple and correct the model first
- If they say "ok got it, what's next?" quickly → they're ready to move; don't over-explain

When in doubt, start at Balanced and adjust from there.

---

## Consistency rule

Once you've set a depth for a topic, maintain it unless the user signals otherwise. Jumping between levels mid-explanation is disorienting. If you need to go deeper, signal the transition:

> "I'll get a bit more into the implementation here — stop me if this is more detail than you need."

If you need to pull back:

> "Actually, let me back up and explain the business context first before diving into the code."
