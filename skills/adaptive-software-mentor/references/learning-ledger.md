# Learning Ledger

The learning ledger is the internal state you maintain throughout a mentoring session. It is not a UI overlay — it's the scaffolding that lets you give coherent, connected explanations across a long conversation.

---

## What to track

```
LEARNING LEDGER
───────────────
Original goal:        [what the user said they wanted to understand]
Current topic:        [what you are explaining right now]
Covered topics:       [list of topics explained so far, with confidence]
Pending topics:       [topics in the original scope not yet covered]
Open side topics:     [branches taken that haven't been fully resolved]
Drift chain:          [sequence of hops from original goal to current topic]
Preferred depth:      [simple | balanced | deep — inferred or user-stated]
Familiarity by area:  [per-topic assessment — see explanation-adaptation.md]
Open questions:       [things mentioned but not yet answered]
```

---

## Tracking rules

**Original goal** — Set once at the start of the session. Never change it, even as the conversation evolves. This is the anchor.

**Current topic** — Update every time you shift to a new explanation. Track detours as separate from the main thread.

**Covered topics** — Mark a topic covered when you have explained it and the user has either accepted it, asked follow-ups (indicating engagement), or verified it themselves. Include a note on how deeply it was covered: *surface*, *functional*, or *deep*.

**Pending topics** — Things that fall within the original goal scope that haven't been addressed yet. These are what you return to after detours.

**Open side topics** — Side questions that came up during explanation. Track their status: *explained*, *partially explained*, *saved for later*, *user dropped it*.

**Drift chain** — The sequence of hops from the original goal. Example: `marketplace flow → royalties → ERC2981 → EIP history`. Update this as the conversation moves. Reset when you return to the main thread.

**Preferred depth** — Inferred from the conversation (see `explanation-adaptation.md`). Update when the user asks for a style change.

**Familiarity by area** — Per-topic familiarity score, not a single global level. Example: React: high, database schema: low, Solidity: medium.

**Open questions** — Anything the user mentioned that deserves a future answer but wasn't addressed in the current flow.

---

## When to display the ledger

**Do not show after every response.** The ledger is internal.

Show it when:

1. **User asks for a checkpoint** — "Where are we?", "What have we covered?", "Can you summarize our progress?"
2. **Session is getting complex** — You've covered 5+ topics and the thread is long. Offer a checkpoint proactively: "We've covered a lot — want a quick summary of where we are before continuing?"
3. **Significant drift occurred** — When you surface the drift alert, include the drift chain so the user can see the path they traveled.
4. **Documentation requested** — Use the ledger to know what can and cannot be included in the document.
5. **User wants to pause and resume** — Summarize the full ledger so the user can pick up later.

---

## Display format

When showing the ledger, use this compact format. Don't dump raw fields — present it as a readable summary:

```
─── Session checkpoint ───────────────────────────────
Goal:         Understand the marketplace flow

Covered:
  ✓ Business purpose of the marketplace (deep)
  ✓ Listing creation flow (functional)
  ✓ Royalty calculation logic (deep)
  ~ ERC2981 standard — partially explained, still open

Pending:
  → Purchase and settlement flow
  → Error handling and edge cases

Side topics:
  ✓ What is ERC2981 — explained and connected back
  → EIP governance process — user asked, not yet covered

Depth preference:  balanced
─────────────────────────────────────────────────────
```

Keep it scannable. The user should be able to understand where they stand in about 10 seconds.

---

## Detour tracking

When a user branches into a side topic, note it internally:

```
[Detour: royalty calculation]
[Main thread paused at: step 3 of marketplace purchase flow]
```

When you return from the detour:

```
[Detour: royalty calculation — resolved]
[Resuming: step 3 of marketplace purchase flow]
```

This keeps the main thread intact even after multiple detours.

---

## Drift threshold

Drift is measured by the number of hops from the original goal.

- 1 hop: Normal side question — follow freely
- 2 hops: Deep detour — fine to continue, note internally
- 3+ hops: Drift — surface it to the user with the three-option prompt

Drift prompt:
> "We've moved quite a bit from [original goal] — we're now in [current topic] via [drift chain]. Want to keep going here, head back to [original goal], or bookmark this thread for later?"
