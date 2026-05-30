# Adaptive Software Mentor

A Claude Code skill that helps you build a real understanding of any software system — a project, feature, module, file, or concept — by guiding you through it the way a senior engineer would.

---

## What it does

When you ask to understand something in a codebase, this skill changes how Claude approaches the explanation:

- Starts from **business purpose** before diving into code
- Follows the path: *why it exists → what it does → how it works*
- Reads available docs (README, CLAUDE.md) before reading code
- Scales the exploration to what you actually asked — doesn't dump the whole codebase when you asked about one file
- Remembers where you were in an explanation when you branch into a side question
- Lets you verify your own understanding and get it corrected precisely
- Can generate structured notes or documentation from the session on demand

It does **not** write code, fix bugs, or implement features — it's purely for building understanding.

---

## Installation

**Option A — One session (no install needed)**

Start Claude Code with:

```bash
claude --plugin-dir "path/to/skills/adaptive-software-mentor.skill"
```

The skill will be active for that session only.

**Option B — Permanent (available in every session)**

Coming soon — local plugin installation guide.

---

## How to trigger it

The skill activates automatically when you ask to understand something. You don't need to name the skill explicitly.

**Phrases that work:**

```
Help me understand this project
Walk me through how authentication works here
Explain the payment module to me
I'm new to this codebase, where do I start?
What does this file do and why does it exist?
I need to understand the order flow before I touch it
Orient me on how the notification service fits in
```

**It also activates when you share your understanding:**

```
Let me check if I got this right — my understanding is...
So basically what happens is... is that correct?
Can you verify whether I understand this correctly?
```

**And when you want documentation:**

```
Generate notes for this feature
Create onboarding docs for this module
Give me a summary of what we just went through
```

---

## How a session works

1. **You state a goal** — what you want to understand
2. **It asks one clarifying question** if the goal is ambiguous — not a form, just one question
3. **It reads docs first** — README, CLAUDE.md, any available specs
4. **It explains** starting from the business reason the code exists
5. **You ask follow-ups** — it follows naturally, keeps track of the main thread
6. **You verify your understanding** whenever you want — it confirms what's right, corrects what's off
7. **You ask for notes** if you want the session turned into a document

---

## Exploration depth

The skill scales to what you asked:

| What you asked | What it does |
|---|---|
| "What does this function do?" | Direct 2–4 sentence answer — no exploration session |
| "Explain the auth flow" | Explores the relevant files, explains the full flow |
| "Help me understand this module" | Covers structure, dependencies, key logic, edge cases |
| "Walk me through this whole project" | Full system overview: modules, data flows, integrations |

It won't scan your entire codebase when you asked about one file.

---

## Adjusting explanation style

You can change how it explains at any time during a session:

| Say this | Effect |
|---|---|
| "Simpler" | Adds analogies, reduces jargon, stays at business layer |
| "More technical" | Goes deeper into implementation specifics |
| "Business-first" | Leads with user impact and problem before any code |
| "Code-first" | Jumps straight to the relevant files and functions |
| "More detail" | Expands the current topic before moving on |
| "Keep it high-level" | Stays at architecture level, skips implementation |

---

## Side questions and detours

If you jump to a related topic mid-explanation, the skill follows you there and connects it back:

> *"So that's how royalties work, and the reason it matters here is... — anyway, back to the marketplace flow..."*

If you drift far from your original question (3+ topic hops), it will gently surface that and offer to return or keep going.

---

## Documentation generation

At any point you can ask for a document based on what's been covered:

- **Feature notes** — business purpose, flow, data changes, edge cases, key files
- **Architecture summary** — component responsibilities, interfaces, dependencies
- **Onboarding guide** — what a new developer needs to know to start working on this
- **Handoff notes** — current state, open threads, risks, what the next person needs to know
- **Personal study notes** — what you now understand, what to revisit, gotchas to remember
- **Concept notes** — what a technology or pattern is and how this project uses it

It only documents what was actually discussed — it won't invent content for sections that weren't covered.

---

## Important considerations

**It works best with a real codebase open.**
The skill explores files, reads docs, and verifies things against actual code. Using it without a codebase defaults to general knowledge, which is less useful.

**Start by telling it what you already know.**
If you say "I know the frontend is React but I don't understand the backend," it won't waste time re-explaining React to you.

**You drive the depth.**
The default is a balanced explanation — not too shallow, not overwhelming. You can push it deeper or pull it back at any point.

**Verification mode is genuinely useful.**
If you've read some code and formed a mental model, tell the skill your understanding. It will confirm what's right, correct what's off, and return a refined version. This is faster than asking it to explain from scratch.

**It won't write code.**
If mid-explanation you want to implement something based on what you learned, you'll need to switch back to normal coding mode. The skill stays in explanation mode by default.

---

## Example sessions

**Starting fresh on a new codebase:**
> "I just joined this team. Help me understand what this system does and how it's structured before I start."

**Before touching something you didn't build:**
> "I need to understand the payment flow end-to-end before I add a refund feature. Walk me through it."

**After reading code on your own:**
> "I've been reading the auth code. My understanding is: user logs in → server checks credentials → issues a JWT → frontend stores it → sends it in every request. Is that the full picture?"

**Turning a learning session into a document:**
> "Can you turn what we just covered into onboarding notes I can hand to the next developer?"
