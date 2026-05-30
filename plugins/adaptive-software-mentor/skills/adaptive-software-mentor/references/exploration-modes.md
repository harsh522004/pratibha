# Exploration Modes

Read this file when starting an exploration session to select the right path for the user's goal.

---

## Mode 1: Project Discovery

**When to use**: User wants an overall picture of the system — how it's organized, what the main pieces do, how they relate.

**Typical phrases**: "Help me understand this project", "I'm new here, what is this system?", "Give me an overview"

**Exploration path:**
1. README and top-level docs — project purpose, technology choices, setup
2. Folder structure — identify main modules or services
3. Entry points — where does execution start? (main, index, server, app)
4. Core data models — what are the key entities?
5. Major data flows — how does data move through the system?
6. External integrations — third-party services, APIs, databases
7. Configuration — environment setup, feature flags

**Explanation order:**
- What problem does this system solve?
- Who uses it and how?
- Main components and their responsibilities
- How components connect
- Key data flows end-to-end
- Important constraints or architectural decisions

---

## Mode 2: Feature Discovery

**When to use**: User wants to understand a specific business capability — the full end-to-end path for one thing the system does.

**Typical phrases**: "Explain the premium import flow", "Walk me through how orders work", "How does authentication work in this app?"

**Exploration path:**
1. Entry point — where does this feature start? (API route, UI action, scheduled job)
2. Input validation — what is accepted, what is rejected?
3. Business logic — what transformation or decision happens?
4. Persistence — what gets written to the database, cache, or external system?
5. Downstream effects — what else happens as a result? (events, notifications, side effects)
6. Error paths — what happens when things go wrong?

**Explanation order:**
- What is this feature for, and who uses it?
- Step-by-step user or system journey
- Validation and constraints
- What data is produced or changed
- What downstream events are triggered
- Edge cases and failure modes

---

## Mode 3: Component Discovery

**When to use**: User wants to understand one module, service, or layer — what it does, how it's structured, how it connects to the rest.

**Typical phrases**: "Explain the marketplace contract", "What does the payment service do?", "How is the auth middleware structured?"

**Exploration path:**
1. Component entry points — public interface (exports, routes, API surface)
2. Internal structure — main files, sub-modules, key classes or functions
3. Dependencies — what does it import/call? what calls it?
4. Data it owns — schemas, tables, state
5. Configuration — what does it need to be configured with?
6. Error handling and edge cases

**Explanation order:**
- What is the responsibility of this component?
- Where does it fit in the larger system?
- How other components interact with it
- Internal structure and key logic
- Dependencies and risks
- Notable edge cases

---

## Mode 4: File Discovery

**When to use**: User wants to understand one specific file — what it does and why it matters.

**Typical phrases**: "Explain Marketplace.sol", "What is this auth.middleware.ts doing?", "What is routes/orders.js for?"

**Exploration path:**
1. File purpose — what problem does this file solve?
2. Related files — what imports this? what does it import?
3. Key exports — what does it expose to the rest of the system?
4. Important functions or classes — what are the main pieces of logic?
5. Side effects — does it write state, trigger events, call external services?

**Explanation order:**
- What is this file's job in the system?
- How it connects to the files around it
- Its main exports and what they do
- Important implementation details
- Things that could break or change impact

---

## Mode 5: Technology or Concept Discovery

**When to use**: User wants to understand a specific technology, pattern, or standard as it applies to this project.

**Typical phrases**: "What is ERC2981?", "Explain how we use JWT here", "What is CQRS and how does this project use it?"

**Exploration path:**
1. What is this technology/concept in general terms?
2. Why does it exist — what problem does it solve?
3. How does this project use it specifically?
4. Where is it implemented in the codebase?
5. What would change if this wasn't used?
6. Common gotchas or misunderstandings

**Explanation order:**
- Plain-language definition
- The problem it solves (motivation)
- How the project applies it
- Where to find it in the code
- Connection back to the main topic if this came up as a side question

---

## Mode 6: Issue Investigation

**When to use**: User wants to understand a bug, unexpected behavior, or suspicious outcome — not to fix it, but to understand what is happening and why.

**Typical phrases**: "Why is royalty calculation failing?", "I don't understand why this returns null", "Help me understand what's supposed to happen here vs what's happening"

**Exploration path:**
1. Expected behavior — what should happen according to docs, tests, or spec?
2. Actual behavior — what is actually happening?
3. Code path — trace the execution path for the affected scenario
4. Likely impact area — which component or boundary seems to be failing?
5. Docs vs implementation gap — does the code match the spec?
6. Edge cases — is this a boundary condition, a race condition, or a missing case?

**Explanation order:**
- What was supposed to happen
- What is actually happening
- The code path involved
- Where the gap or failure point seems to be
- Related edge cases and failure modes

Note: This mode is for building understanding, not for fixing the bug. If the user decides they want to fix it after understanding, they can ask to switch to a coding mode.

---

## Mode 7: Documentation Mode

**When to use**: User wants to capture the learning session as a document they can share, reference later, or hand to a teammate.

**Typical phrases**: "Create notes for this feature", "Generate onboarding docs for this module", "I want to document what we just went through"

**How to handle:**
- Identify what has already been covered in the session
- Ask which document type they want (if not specified)
- Generate output based only on what was discussed and verified
- Don't invent content that wasn't covered

For document types and output format templates, see `references/documentation-generation.md`.

---

## Depth matching

| Goal scope | Exploration depth |
|---|---|
| Single file or small concept | File + immediate dependencies only |
| Feature (1-2 services) | Full feature path: input → logic → persistence → output |
| Module or component | Component internals + external interface |
| Full project | All major modules, data flows, key integrations |

When in doubt, start narrow and expand if the user needs more. Don't front-load everything.
