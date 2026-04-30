# Using Your Second Brain

> **Purpose:** Move from scattered notes to a working project knowledge base—organization strategy for their vault and a summary a stranger could understand in minutes.
>
> **Understand:** Tutor mode. User asks about knowledge management, external memory, why notes matter, the PARA method.
> **Contextualize:** Coach mode. How will THEY organize their project's knowledge? What goes where?
> **Apply:** Coach mode. They create their project's second brain structure and write their first project summary.

---

## Stage Start

Announce to the user:

> "Welcome to Using Your Second Brain. You've been writing notes, but now we're making them WORK for you. Three phases:
> 1. **Understand** — Ask me about second brains: why external memory beats your brain, how to organize notes, what makes a note useful vs. useless.
> 2. **Contextualize** — We'll design the organization system for YOUR project's knowledge.
> 3. **Apply** — You'll create the structure and write a summary so good that a stranger could understand your project in 5 minutes.
>
> We'll move to each next phase when you confirm you're ready."

---

## Phase 1: Understand — [[UCA-teaching.md]]
**Topic:**
- Answer questions about knowledge management, note-taking systems, external memory
- Do NOT review their current notes or suggest reorganization yet
- Do NOT tell them to create specific folders
- Let them understand the philosophy first

### Key Concepts They Should Explore

- **Why external memory matters** — your brain is for having ideas, not holding them
- **What makes a note useful** — searchable, linked, written in your own words, with context
- **What makes a note useless** — copy-pasted, no context, no links, can't find it later
- **The PARA method** (or similar): Projects, Areas, Resources, Archives
- **The difference between a reference note and a thinking note** — reference stores facts; thinking stores reasoning and decisions
- **Linking notes** — connections between ideas are more valuable than the ideas themselves
- **Weekly review** — knowledge decays if you don't revisit it; consider using a flashcard app like CrowdCards (https://crowdcards.app/), which lets you practice recall of key concepts.

### Guided Start (to prevent learner stall)

At the start of Understand, give a short orientation:

> "By the end of this phase, you should be able to explain:
> 1. Why external memory helps long projects
> 2. What makes notes useful versus disposable
> 3. The difference between reference notes and thinking notes
> 4. Why linking notes matters
> 5. How review habits keep a second brain alive"

If they are unsure what to ask, offer question starters:
- "Why isn't memory alone enough for a long project?"
- "What makes one note genuinely useful six weeks later?"
- "How should I separate reference notes from decision notes?"
- "What are practical ways to link notes without overcomplicating it?"
- "How often should I review my notes and what should I look for?"

### The Kitchen Analogy (use only if asked)

Your brain is a kitchen counter. You can keep a few things on it — the recipe you're currently using, the ingredients for today's meal. But if you pile everything on the counter (all your passwords, all your project ideas, all your meeting notes), you can't cook. A second brain is like building cabinets and a pantry. Everything has a place. When you need the recipe for sourdough, you know which cabinet. When you're done with today's recipe, you file it. The counter stays clear for cooking (thinking).

### Readiness to Move to Contextualize

When the learner confirms they are ready to move on (and can explain the core concepts in their own words), read their current notes if they exist, then move to Phase 2.

---

## Phase 2: Contextualize — [[UCA-teaching.md]]
**Topic:**
- Help them design a knowledge system that fits their project and their working style
- Don't impose a rigid system — help them discover what they need

### What to Do

1. Ask: "What kinds of information does your project generate?" (Specs, decisions, lessons learned, bugs fixed, research, ideas, security notes)

2. Ask: "When you've tried to find something you wrote down before, what was hardest to find?" (This reveals their actual pain, not theoretical pain)

3. Read what already exists in their second brain. This lesson *extends* that structure — it does NOT replace it.

   Suggestions for useful files:
  - ideas.md               # a place to quickly jot down ideas as they come to you, leaving the task of filing them till later, or for your AI to do for you.
  - project-next-steps.md  # a record of what you want to focus on getting done next
  - lessons/               # a place to save lesson notes
  - decisions/             # a place to record decisions on your project, and the reasons why they were made
4. Help them establish conventions:
   - **Date every decision note** — context changes; "why we chose SQLite" from March might not apply in June
   - **Link related notes** — `[[decisions/database-choice]]` connects to `[[lessons/sqlite-performance]]`
   - **Write in your own words** — if you can't explain it simply, you don't understand it
   - **One idea per note** — makes linking and finding possible

5. Ask: "What's the ONE note you wish you'd written last week but didn't?" Have them write it now.

### When They're Ready for Apply

Say: "When you're ready to build your second brain, tell me you're ready for the Apply phase."

---

## Phase 3: Apply — [[UCA-teaching.md]]

### Exercise 1: Create the Structure

Have them create the folder/note structure in their chosen tool (Obsidian, Notion, or plain markdown files). It doesn't need to be perfect — it needs to exist.

### Exercise 2: The Project Summary

Update `home.md` (already created during setup) — review whether it still accurately describes the project. It should answer:
- What is this project?
- Why does it exist?
- What's the current status?
- Where are the important files?
- What decisions are pending?
- What would a new person (or future you) need to know?

Prompt for them:
> "Write this as if you're briefing a friend who is smart but knows nothing about your project. They have 5 minutes. What do they need to know?"

You review it. Is it clear? Is it honest about what's uncertain? Does it link to other notes?

### Exercise 3: The Decision Log

Have them write at least ONE decision note:
- What we decided
- Why we decided it (with context)
- What we considered and rejected
- Date
- What would make us revisit this

Example:
```
# Decision: SQLite over JSON files

**Date:** 2026-04-15
**Context:** App needs to store notes with timestamps and search by date.
**Decision:** Use SQLite instead of JSON files.
**Why:** JSON would require loading the entire file to search. SQLite handles queries natively.
**Rejected:** Firebase (needs internet, too complex for now), plain files (no querying).
**Revisit if:** We need multi-device sync OR our data exceeds SQLite's limits.
```

### Exercise 4: Link Three Notes

Find three pairs of notes where one note's understanding is improved by linking to another. If you can't find three, the second brain is too small or too disconnected — that *is* the lesson. The value of a second brain is in connections, not isolated facts.

**Prompt for them:** "Find a decision note and a lesson note that relate to the same feature. Link them. Explain in one sentence why the connection matters."

---

## What They Should Write

**In their second brain:**
- `home.md` — updated project summary
- `decisions/[topic].md` — at least one decision log
- `lessons/[topic].md` — at least one lesson from previous stages
- Links between at least three notes

---

## Gate

Can the user:
1. Explain why external memory matters for a long-term project?
2. Create a simple folder structure for their project's knowledge?
3. Write a project summary that a stranger could understand in 5 minutes?
4. Write one decision log with context, reasoning, and revisit triggers?
5. Create at least three links between notes?

If yes, mark Using Your Second Brain complete in `progress.md` and move to [[09-skills]].
