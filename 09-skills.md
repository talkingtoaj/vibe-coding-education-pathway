# AI Skills

> **Purpose:** Introduce AI skills as reusable instructions—what they are, which ones fit their workflow, then creating two practical skills from scratch.
>
> **Understand:** Tutor mode. User asks about AI skills: what they are, why reusable beats copy-paste, how skills compose.
> **Contextualize:** Coach mode. What skills would help THEIR workflow? Brainstorm two practical skills for their project.
> **Apply:** Coach mode. They create their first two skills: brainstorm and reflect-and-learn.

---

## Stage Start

Announce to the user:

> "Welcome to AI Skills. You've been vibe coding. Now you're going to vibe architect — teach your AI reusable superpowers. Three phases:
> 1. **Understand** — Ask me about skills: what makes them different from prompts, how they chain together, why consistency matters.
> 2. **Contextualize** — We'll figure out what skills would actually help YOUR workflow.
> 3. **Apply** — You'll create two real skills: one for brainstorming ideas, one for reflecting on what you learned.
>
> We'll move to each next phase when you confirm you're ready."

---

## Phase 1: Understand — [[UCA-teaching.md]]
**Topic:**
- Answer questions about AI skills, reusable prompts, skill composition
- Do NOT tell them what skills to create
- Do NOT connect to their project yet
- Let them understand what a skill IS and why it's powerful

### Key Concepts They Should Explore

- **What an AI skill is** — a reusable instruction package that triggers automatically
- **Why skills beat copy-paste prompts** — consistency, composability, iterative improvement
- **How skills compose** — "brainstorm" → "reflect and learn" → "write a spec"
- **Skill persistence** — a skill survives between sessions; a one-off prompt doesn't
- **The skill lifecycle** — define → test → refine → use → improve
- **Trigger words** — keywords that activate a skill (e.g., "brainstorm", "reflect")

### Guided Start (to prevent learner stall)

At the start of Understand, give a short orientation:

> "By the end of this phase, you should be able to explain:
> 1. What an AI skill is
> 2. How a skill differs from a one-off prompt
> 3. How skills compose into workflows
> 4. How skills improve over time
> 5. How to choose practical first skills"

If they are unsure what to ask, offer question starters:
- "What makes a skill different from a normal prompt?"
- "When should I create a skill instead of retyping instructions?"
- "How do multiple skills chain together in practice?"
- "What are signs a skill needs refinement?"
- "What are good first skills for a beginner workflow?"

### The Kitchen Appliance Analogy (use only if asked)

A skill is like a kitchen appliance. You don't re-invent the blender every time you want a smoothie. You bought it once, it lives in your kitchen, and when you say "blend," it does the thing. A skill is the same: you define the behavior once, and then a trigger word calls it up instantly. And just like appliances, you can chain them: blender → ice maker → glass → serve.

### Readiness to Move to Contextualize

When the learner confirms they are ready to move on (and can explain the core concepts in their own words), read their `context.md` and project status, then move to Phase 2.

---

## Phase 2: Contextualize — [[UCA-teaching.md]]
**Topic:**
- Help them identify what skills would actually save them time
- Focus on their real workflow, not theoretical possibilities

### What to Do

1. Ask: "Think about the last few sessions you've had with an AI. What did you ask for repeatedly? What patterns keep coming up?"

2. Ask: "When you get stuck, what's your process? Do you brainstorm? Do you research? Do you ask for explanations? Which of these could be a reusable skill?"

3. Ask: "What decisions do you make often that you'd like structured help with?" (Feature prioritization, architecture choices, security review)

4. Help them pick TWO skills to start with. Common starting points:
   - **Brainstorm** — "I need ideas for X, ranked by feasibility"
   - **Reflect and Learn** — "What just happened and how do I not forget it?"
   - **Spec Writer** — "Turn my vague idea into a proper spec"
   - **Code Review** — "Check this code for comprehension debt and security issues"
   - **Security Scan** — "What could go wrong with this approach?"

5. For each chosen skill, ask: "What trigger word feels natural to you? What would you actually say to activate this?"

### When They're Ready for Apply

Say: "When you're ready to build your first two skills, tell me you're ready for the Apply phase."

---

## Phase 3: Apply — [[UCA-teaching.md]]

### Exercise 1: Brainstorm Skill

Guide them to create a skill that:
- Triggers on "brainstorm" or "ideas for"
- Produces 5 novel ideas related to their input
- Ranks them by feasibility against their `context.md` constraints
- Recommends one with reasoning
- Offers to draft a spec for the chosen idea

The skill file should live in their second brain:
```
skills/brainstorm.md
```

Example content (they adapt to their style):
```
# Brainstorm Skill

## Trigger
User says "brainstorm" or "ideas for" or similar.

## Behavior
1. Generate 5 novel ideas related to the user's request
2. For each idea, note: feasibility, effort, and alignment with project constraints
3. Rank by: (1) solves a real problem user has, (2) fits within current constraints, (3) effort required
4. Recommend the top choice with reasoning
5. Offer to draft a spec for it

## Constraints
- Read project context from second brain before generating
- Avoid ideas that violate known constraints (budget, tech stack, timeline)
- Be honest about effort — don't suggest "easy" when it's not
```

### Exercise 2: Reflect-and-Learn Skill

Guide them to create a skill that:
- Triggers on "reflect and learn" or after a difficult session
- Reviews what went wrong, how it was resolved
- Asks what would have prevented it
- Suggests a skill update or new skill
- Writes the reflection to `reflections/YYYY-MM-DD-topic.md`

Example content:
```
# Reflect and Learn Skill

## Trigger
User says "reflect and learn" or indicates a difficult/stuck session.

## Behavior
1. Ask: What was the problem or confusion?
2. Ask: How was it resolved (or how did we work around it)?
3. Ask: What would have prevented this entirely?
4. Suggest: Should we create or update a skill based on this?
5. Write a reflection note to the second brain

## Output Format
reflections/YYYY-MM-DD-[topic].md with:
- Problem
- Resolution
- Prevention strategy
- Suggested skill update
```

### Exercise 3: Make Skills Available

The second brain copy of a skill is the *source of truth* — where the user edits and versions it. The tool-specific install is what makes it actually load automatically.

Help them configure their AI tool:

- **If using Claude Code:** Skills live in `~/.claude/skills/`. Copy or symlink the skill file there. Alternatively, reference it in `CLAUDE.md` at the project root.
- **If using Cursor:** Skills belong in the project's `.cursorrules` file or Cursor's custom instructions.
- **If using Claude Desktop:** There's no native auto-loading skill system. The user must paste the skill at the start of relevant sessions, or ask the AI to read it from the second brain at session start.

Note: "trigger word" is one mental model — it works well in Claude Code but isn't how all tools invoke skills. Some tools use the skill's description to decide when to apply it. The user should test their specific tool to see how invocation works.

### Exercise 4: Test the Skills

Have them actually USE each skill:
1. Say the trigger word for brainstorm — did it work as expected?
2. Simulate a "reflect and learn" moment — did it capture the lesson?
3. Iterate: what didn't work? Refine the skill.

### Exercise 5: Skills That Beat Pattern Drift and the Context Wall

> **Vibe-coder trap:** A project hits 3,000 lines across 40 files. The developer asks the AI for a small change. The AI does it. The change breaks two other features. He asks the AI to fix those, and the fix breaks a third. The AI starts contradicting its own earlier decisions. Every login screen looks slightly different, every error message is formatted differently. The AI can't hold the whole project in its head, so each prompt sees only a slice and reinvents conventions for that slice.
>
> Two named symptoms: **pattern drift** (AI reinvents solutions already solved elsewhere) and **the context wall** (codebase grows past what the AI can hold at once).

Two skills that directly address these:

**Refactor and clean-code skill** — a weekly skill that scans the project for duplicated patterns, names them, proposes a single canonical version, and refactors duplicates to use it. Run it every Friday; pattern drift dies.

**Handover skill** — a skill that saves the current state of a long session (what's been done, what's pending, the AI's current understanding) into `handover.md`. Start a fresh session, hand the AI that file, continue without losing thread. This is the answer to the context wall.

Beyond skills, a `CLAUDE.md` / `AGENTS.md` at the project root is the **implementation agent’s** persistent memory of the project: conventions, tech stack, security rules, "things the AI keeps getting wrong." It's the difference between starting every session from scratch and starting every session knowing the rules. (That file is **not** the same document as the pathway’s course-coach `AGENTS.md` + `UCA-teaching.md` — keep teaching prompts and project build rules separate.)

Have the user hand this directive to their **implementation agent**:

> "Read my project's existing code and identify three conventions the AI seems to keep forgetting — formatting, error handling, naming, auth pattern, anything. Write me a `CLAUDE.md` (or equivalent for my tool) that names each convention explicitly with one example. Then design two skills for me: a refactor skill that runs once a week to find and merge drifted patterns, and a handover skill that captures the current session's state into a handover doc when context fills up."

**Exercise:** the user writes a `CLAUDE.md` for their project. Designs the two skills. Tests the handover skill by deliberately ending a session and starting a fresh one with only the handover doc.

---

## What They Should Write

**In their second brain:**
- `skills/brainstorm.md` — their brainstorm skill definition
- `skills/reflect-and-learn.md` — their reflection skill definition
- `reflections/YYYY-MM-DD-[topic].md` — at least one reflection from testing

---

## Gate

Can the user:
1. Explain the difference between a skill and a one-off prompt?
2. Create two skill definitions with clear triggers and behaviors?
3. Make those skills available in their AI tool?
4. Test both skills and iterate based on results?
5. Explain how skills could chain together for a complex workflow?

If yes, mark AI Skills complete in `progress.md` and move to [[10-goat-app]].
