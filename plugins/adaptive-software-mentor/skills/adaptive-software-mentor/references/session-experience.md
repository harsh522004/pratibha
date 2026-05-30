# Session Experience

This file contains the visual templates, display formats, and decision rules for the Exploration Experience Layer. Read this when you need the exact format for any structured UI element — bootstrap, session identity, continuation menus, drift alerts, or exploration memory prompts.

---

## When to use structured UI elements

| Element | When to show |
|---------|-------------|
| Bootstrap | At the start of a full exploration session — not for quick lookups |
| Session Identity | Session start confirmation, major drift re-orientation, before documentation |
| Guided Continuation | After finishing a major explanation section in a full session |
| Deep Dive Menu | When the user asks to go deeper on a topic |
| Exploration Memory | When starting a new topic within the same session and preferences are established |
| Drift Alert | When the exploration chain reaches 3+ hops from the original goal |
| Understanding Verification | When the user shares their mental model for checking |

**Quick test:** If the response would work just as well as a plain paragraph, use a plain paragraph. Structured elements are for moments of transition and choice — not for wrapping ordinary explanations.

---

## Bootstrap Template

Use when the user is entering a full exploration session and key parameters aren't yet clear.

```
🧭 Exploration Setup

🎯 What would you like to explore?
   1. Project — overall system understanding
   2. Feature — one capability end-to-end
   3. Component / Module — one service or layer
   4. File — one specific file's role
   5. Concept / Technology — a pattern or standard
   6. Issue / Behavior Investigation

🔍 What aspect interests you most?
   1. Business understanding — why it exists, who uses it
   2. Functional flow — what happens step by step
   3. Technical architecture — structure and design decisions
   4. Code-level detail — implementation specifics
   5. End-to-end — all of the above

📚 How deep do you want to go?
   1. Overview — main ideas and structure, enough to orient yourself
   2. Medium — understand it well enough to work with it confidently
   3. Deep dive — thorough understanding including edge cases and tradeoffs

📎 Anything helpful to share upfront?
   Files, folder paths, feature names, existing knowledge, or docs —
   anything that helps focus the exploration.
```

**Shortcut rule:** If the user's opening message already answers some of these, skip those prompts. Only ask for what's genuinely missing. Examples:

- "I need a deep dive into the payments module" → already have target (feature), depth (deep dive); only ask about aspect if it matters
- "Help me understand this codebase" → ask all four
- "Explain how JWT is used in this app" → already have target (concept), aspect (technical); only ask depth

---

## Session Identity Card

Show after bootstrap confirmation, at major drift re-orientations, and before documentation generation.

**Single-line format** (for inline use, e.g. after bootstrap):
```
🧭 Exploration Session Started · 🎯 Goal: [topic] · 🔍 Focus: [aspect] · 📚 Depth: [level]
```

**Block format** (for checkpoints, drift re-orientations, or when the user asks for a summary):
```
🧭 Exploration Session

🎯 Goal:    [original exploration goal]
🔍 Focus:   [aspect being explored — may have shifted]
📚 Depth:   [current depth setting]
```

Use the single-line format immediately after bootstrap (it's confirmation, not announcement). Use the block format when re-orienting after drift or when the user asks "where are we?"

---

## Guided Continuation Menu

Show after finishing a major explanation section in a full session.

```
🚀 Where would you like to go next?

1. Go deeper into this topic
2. Explore a related component
3. Continue along the main learning path
4. Verify your understanding
5. Generate notes from what we've covered

(Or just tell me what you want — this is just a guide.)
```

**Tone note:** The parenthetical line keeps the menu from feeling rigid. Include it. The user should know they can respond naturally, not just pick a number.

**When to skip it:** If the user just asked a specific follow-up ("what about the error path?"), answer it — don't put a continuation menu in front of their question.

---

## Deep Dive Menu

Show when the user asks to go deeper on a topic.

```
🔬 Deep Dive — [topic name]

What aspect would you like to explore more closely?

1. Business reasoning — why this exists, what problem it solves, who it serves
2. Functional flow — what happens step by step when this runs
3. Architecture — how it's structured and why it's designed that way
4. Data flow — how data enters, transforms, and exits
5. Code walkthrough — the actual implementation in detail
6. Edge cases — boundary conditions, error paths, unusual inputs
7. Change impact — what else in the system would be affected by changes here

Pick one or several. I'll follow the order listed above when covering multiple.
```

---

## Exploration Memory Prompt

Show when starting a new topic within the same session where preferences are already established.

```
🧠 Continuing with your session preferences:

   Depth:  [current depth level]
   Style:  [current explanation style]

Keep these for the new topic, or would you like to adjust?
```

**When to skip it:** If the user moves naturally into a new topic without pausing, carry the preferences forward silently — no prompt needed. The prompt is for moments where you want to confirm the user is aware preferences are carrying over, particularly if the new topic is significantly different in nature (e.g. they spent the last 20 minutes in business-first mode and are now asking about a low-level implementation detail).

---

## Drift Alert

Show when the exploration chain reaches 3+ hops from the original goal. Reference `references/learning-ledger.md` for the drift threshold rules.

```
⚠️ Drift Check

We've moved quite a bit from [original goal].

Path taken: [original goal] → [hop 1] → [hop 2] → [current topic]

Would you like to:
1. Keep going here — this feels relevant
2. Return to [original goal]
3. Save this thread and come back to it later
```

---

## Understanding Verification Response

Use when the user shares their mental model for checking (triggered by "let me check if I got this right", "my understanding is", etc.)

```
✅ [What they got right — be specific]

[What's missing or slightly off — be precise, not vague]

Refined model:
[Return a corrected or completed version of their mental model in plain language]
```

Don't use this format for simple factual corrections. It's for cases where the user has assembled a multi-part mental model and you're calibrating it as a whole.

---

## Icon Usage Reference

| Icon | Use for | Example context |
|------|---------|-----------------|
| 🧭 | Session markers, orientation | Bootstrap header, session identity |
| 🎯 | Goals and targets | Goal line in session card |
| 📚 | Depth, documentation, learning | Depth line in session card, doc generation |
| 🔍 | Investigation, focus | Focus line in session card, close examination |
| 🔬 | Deep dive | Deep dive menu header |
| 🧠 | Understanding, memory | Exploration memory prompt |
| 📎 | Context, references | Optional context section in bootstrap |
| 🚀 | Next steps | Guided continuation menu header |
| ⚠️ | Drift alerts, warnings | Drift check header |
| ✅ | Verified, confirmed | Understanding verification |

**Do not use icons:**
- Inside paragraph explanations
- On every bullet point in a regular list
- As decoration to break up ordinary prose
- More than 2–3 times in a single response

If a response would look the same without the icon, remove it.
