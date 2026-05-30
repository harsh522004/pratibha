# Documentation Generation

When the user asks for notes, documentation, or a summary, use this file to select the right document type and structure.

**Critical rule**: Only document what was actually discussed and verified in the session. Don't invent content, don't include things you believe to be true but didn't verify, and don't pad the document with assumptions.

If an area wasn't covered, note it as "not covered" or "to be explored" rather than leaving it out or filling it in with guesses.

---

## Document types

### 1. Project Overview
**Use when**: User wants a high-level document summarizing the whole system.

```
# [Project Name] — Overview

## Purpose
What problem this system solves and for whom.

## Main Components
| Component | Responsibility |
|-----------|----------------|
| ...       | ...            |

## Key Data Flows
Short description of the 2-3 most important end-to-end flows.

## Technology Stack
Languages, frameworks, databases, external services.

## Architecture Notes
Any important architectural decisions or constraints.

## Not covered in this session
Topics within this project that weren't explored.
```

---

### 2. Feature Notes
**Use when**: User wants documentation of a specific feature or capability.

```
# [Feature Name] — Notes

## Business Purpose
What this feature does and why it exists.

## Trigger / Entry Point
How the feature is initiated (API call, UI action, scheduled job, event).

## Flow
Step-by-step description of what happens:
1. ...
2. ...
3. ...

## Data Created or Modified
What changes in the database, cache, or external systems.

## Downstream Effects
Events, notifications, or side effects triggered.

## Edge Cases
Known boundary conditions, error paths, or gotchas.

## Key Files
| File | Role |
|------|------|
| ...  | ...  |

## Open Questions
Things mentioned during the session that weren't fully resolved.
```

---

### 3. Architecture Summary
**Use when**: User wants a structural view of a module, service, or layer.

```
# [Component Name] — Architecture Summary

## Responsibility
What this component owns and what it does not own.

## Public Interface
Exports, routes, or API surface available to other components.

## Internal Structure
Main files or sub-modules and their roles.

## Dependencies
| Dependency | Direction | Purpose |
|------------|-----------|---------|
| ...        | uses / used-by | ... |

## Data Ownership
Tables, schemas, or state this component is responsible for.

## Notable Design Decisions
Any architectural choices worth knowing about.
```

---

### 4. Concept Notes
**Use when**: User wants to capture understanding of a technology, pattern, or standard.

```
# [Concept Name] — Notes

## What it is
Plain-language definition.

## Why it exists
The problem it was designed to solve.

## How this project uses it
Where and why this project applies the concept.

## Where to find it
Relevant files, modules, or configuration.

## Connection to [original topic]
How this concept relates to what the user was originally exploring.

## Gotchas
Common misunderstandings or tricky behavior.
```

---

### 5. Onboarding Guide
**Use when**: User wants a document for getting a new developer up to speed on this system or feature.

```
# Onboarding: [System / Feature Name]

## What this is
One-paragraph summary for someone who has never seen this before.

## Before you start
What a new developer should know coming in:
- Required background knowledge
- Where to find relevant docs
- How to run the system locally

## Mental model
The key concepts a new developer needs to hold in their head:
1. ...
2. ...

## The main flows
Walk through the 2-3 most important things to understand first.

## Where things live
| Thing you'll need to change | Where to find it |
|-----------------------------|------------------|
| ...                         | ...              |

## Common mistakes
Things that trip up people new to this codebase.

## Who to ask
Suggested: areas where additional context from a team member would help.
```

---

### 6. Handoff Notes
**Use when**: User is handing off work to someone else and wants to document their current understanding.

```
# Handoff Notes: [Feature / Task Name]

## Current state
What has been done and what is still in progress.

## How it works
Brief explanation of the relevant system or feature.

## What I changed (or was about to change)
Specific files, modules, or behaviors modified or targeted.

## Open threads
Things that were started but not finished, with context.

## Risks and watchpoints
Places where changes could have unintended side effects.

## What the next person needs to know
Anything non-obvious that took time to figure out.
```

---

### 7. Personal Study Notes
**Use when**: User wants a personalized summary of what they learned in the session — for their own reference, not for sharing.

```
# Study Notes: [Topic]

## What I now understand
Key things that clicked.

## How I'd explain it to someone else
A test of understanding — what I could say to a teammate.

## What I still want to explore
Pending questions and threads.

## Things to watch out for
Edge cases or gotchas I want to remember.

## Key files to revisit
| File | Why |
|------|-----|
| ...  | ... |
```

---

## Generating the document

1. Ask which type the user wants if it isn't clear from context.
2. Review the learning ledger (see `references/learning-ledger.md`) to identify what was covered and at what depth.
3. Fill in sections that were covered. Mark uncovered sections as "not covered in this session."
4. Offer to cover the gaps if the user wants to continue before generating the final document.
5. Write the document and present it in a code block so the user can copy it easily.
