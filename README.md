# pratibha

A personal collection of skills for Claude Code. Each skill here is built around a specific workflow that I kept wishing worked better during day-to-day engineering — things like understanding an unfamiliar codebase, navigating someone else's feature, or building a real mental model before making changes.

The name *pratibha* (प्रतिभा) means intelligence or insight in Sanskrit. That felt right for a collection of tools built around understanding things, not just doing things.

---

## What are skills?

Claude Code skills are behavioral plugins — they change how Claude approaches a specific type of task when you trigger them. Instead of getting a generic AI response, you get a structured, purposeful workflow designed for that particular kind of work.

Skills live in this repo and install in two commands. Once installed, they activate automatically when you say the right kind of thing — no need to remember a command name or format your request in a special way.

---

## Skills in this collection

### 🧭 Adaptive Software Mentor

**Install name:** `adaptive-software-mentor@pratibha`

Helps you build a real understanding of any software system — a project, a feature, a module, a single file, or a concept — by guiding you through it the way a senior engineer would.

Most of the time when you're trying to understand code, you either get a raw code dump or a surface-level summary. Neither actually helps you reason about the system. This skill changes the approach: it starts from *why the code exists*, follows a structured explanation path (business purpose → functional flow → architecture → implementation), tracks where you are in the explanation when you branch into side questions, and lets you verify your own mental model against what's actually happening.

It also runs a proper exploration session for deeper goals — it reads your docs first, checks the code, builds an internal model, then explains. And when you're done, it can turn the whole session into structured notes you can keep or share.

It's not a coding assistant. It won't write or fix anything. It's purely for understanding.

**→ Full details, usage examples, and session walkthrough: [plugins/adaptive-software-mentor/README.md](plugins/adaptive-software-mentor/README.md)**

---

## Installation

Add this repo as a plugin marketplace source, then install the skill you want:

```bash
claude plugin marketplace add harsh522004/pratibha
claude plugin install adaptive-software-mentor@pratibha
```

That's it. No restart needed. The skill is available in every Claude Code session from that point on.

**To update to the latest version:**

```bash
claude plugin update adaptive-software-mentor@pratibha
```

---

## Using a skill

Skills activate automatically from natural language — you don't need to type a slash command or use any special format. Just describe what you're trying to do and the right skill picks up.

For the Adaptive Software Mentor, anything like these works:

```
Help me understand this project
Walk me through how authentication works here
I'm new to this codebase — where do I start?
Explain the payment module before I touch it
What does this file do and why does it exist?
Let me check if I understand this correctly — my understanding is...
Generate notes for what we just covered
```

---

## More skills

This collection will grow over time. Each new skill here will be built around a real workflow gap — something that comes up regularly during engineering work and that a well-designed skill can genuinely improve.

If you have ideas or run into something that feels like it should work better, feel free to open an issue.
