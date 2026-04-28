# Stage 8: AI Skills

> **Audience: AI coach.** Teach the user to extend their AI's capabilities with reusable skills. This is where the vibe coder becomes a vibe coder-architect.

---

## Teaching Goals

By the end of this stage, the user should:
- Understand what an AI skill is and why it's more powerful than a single prompt
- Have installed or configured a skill framework (e.g., Anthropic's skill-creator)
- Have created a `brainstorm` skill that triggers on keyword and produces structured ideation
- Have created a `reflect-and-learn` skill that captures problem-solving wisdom for future sessions
- Understand how skills can be chained together for complex automations
- Know how to make the AI aware of their skills in every session

---

## What is an AI Skill?

A skill is a **reusable instruction package** that the AI loads automatically when triggered. Instead of typing a long, detailed prompt every time you want the same behavior, you define it once as a skill. From then on, a keyword, phrase, or command activates it.

### Analogy

Think of a skill like a **kitchen appliance.** You don't re-invent the blender every time you want a smoothie. You bought it once, it lives in your kitchen, and when you say "blend," it does the thing. A skill is the same: you define the behavior once, and then a trigger word calls it up instantly.

### Why Skills Beat Copy-Paste Prompts

- **Consistency:** The AI behaves the same way every time, not depending on how well you remember the prompt
- **Composability:** Skills can call other skills. "Brainstorm" → "Reflect and learn" on the best idea → "Write a spec" for the chosen one
- **Iterative improvement:** When you notice the skill producing weak output, you edit the skill definition once. Every future use improves.
- **Session survival:** Skills persist across chat sessions. Your carefully crafted prompt doesn't get lost when the tab closes.

---

## Skill Framework Setup

Different AI tools implement skills differently. Guide the user based on what they're using.

### Option A: Anthropic Skill Creator (Recommended for Claude)

If the user is on Claude Desktop or Claude Code:

1. **Check if skill support exists.** Ask the user to look in their tool's settings for "Skills," "Custom Instructions," "Projects," or "Agent Rules."
2. **If available:** Guide them to create their first skill using the tool's native skill creator.
3. **If not available or unclear:** Have them create a `skills/` folder in their second brain and store skill definitions as markdown files. They'll paste the skill content at the start of relevant sessions.

### Option B: Cursor Rules / Custom Instructions

If using Cursor:

1. **`AGENTS.md` file** in project root — defines behavior for the AI in that project (Cursor calls this `.cursorrules`, Claude Code uses `CLAUDE.md`, but `AGENTS.md` is the generic convention)
2. **Custom instructions** in Cursor settings — global behavior rules
3. Guide the user to create an `AGENTS.md` file that includes skill-like behavior

### Option C: Plain Text Skills (Universal Fallback)

If the AI tool has no native skill system:

1. Create a `skills/` folder in the second brain
2. Each skill is a markdown file with a clear name: `skills/brainstorm.md`, `skills/reflect-and-learn.md`
3. At the start of a session where they want the skill, they (or the AI) reads the skill file and loads its instructions into context
4. This is less automatic but still powerful and works with any tool

**Key principle:** The mechanism matters less than the concept. A skill is a defined, reusable behavior. How it's loaded depends on the tool.

---

## Exercise 1: The Brainstorm Skill

### What It Does

When the user says "brainstorm" (or types `/brainstorm`, or uses whatever trigger their tool supports), the AI:
1. Generates **5 novel ideas** related to the topic the user just mentioned
2. For each idea, lists **2 pros and 2 cons**
3. Ranks them by **feasibility** for the user's specific context (reads `context.md` to know their constraints)
4. **Recommends one** with clear reasoning
5. Offers to **draft a spec** for the recommended idea

### Why This Matters

Brainstorming is central to vibe coding: picking features, solving problems, choosing tech, naming things. A good brainstorm skill ensures the AI doesn't just generate random ideas — it generates *relevant, evaluated* ideas tailored to the user's situation.

### Setup Steps

Have the user create their brainstorm skill. The exact method depends on their tool:

**For Anthropic/Claude skill system:**
```
Name: brainstorm
Trigger: user says "brainstorm" or the topic suggests ideation
Behavior:
1. Read the user's context.md to understand their background, project, and constraints
2. Generate 5 distinct ideas related to the current topic
3. For each idea: 2 pros, 2 cons
4. Rank by feasibility given the user's constraints (time, budget, tech stack, experience)
5. Recommend the top choice with a 2-sentence justification
6. Ask: "Would you like me to draft a spec for this idea?"
```

**For plain text fallback:** Create `skills/brainstorm.md` in their second brain with the above content.

### Test It

Have the user say: "I need a new feature for my recipe app. Brainstorm."

Verify:
- Did it generate 5 ideas?
- Did each have pros and cons?
- Did the ranking consider their actual constraints?
- Did it recommend one with reasoning?

**If it failed any check, refine the skill definition together.** This is iterative — the first draft is never perfect.

---

## Exercise 2: The Reflect-and-Learn Skill

### What It Does

When the user says "reflect and learn" after a difficult session, the AI:
1. **Reviews the session** (or asks the user to summarize what happened if it can't see history)
2. Identifies **what went wrong** — the specific friction points, misunderstandings, or repeated attempts
3. Identifies **how it was resolved** — the insight, workaround, or change that finally worked
4. **Suggests a skill update or new skill** to prevent the same friction in future sessions
5. Writes a concise summary to the user's second brain: `reflections/YYYY-MM-DD-topic.md`

### Why This Matters

Every vibe coder hits walls. The difference between a struggling beginner and a productive practitioner isn't avoiding walls — it's **capturing the ladder.** When you spend 20 minutes figuring out why the deployment failed, that wisdom should be preserved. Otherwise, you'll hit the same wall next month and waste 20 minutes again.

**Analogy:** A ship's log. Every voyage notes the rocks, the currents, the storms. Future captains read the log and avoid the rocks. Your reflect-and-learn skill is your ship's log.

### Setup Steps

**For Anthropic/Claude skill system:**
```
Name: reflect-and-learn
Trigger: user says "reflect and learn" or "what did we learn?" or similar
Behavior:
1. Ask the user (or review session history): "What was the main problem or friction we just faced?"
2. Ask: "How was it eventually resolved?"
3. Ask: "What would have prevented this friction entirely?"
4. Propose: "Should we update an existing skill to include this wisdom, or create a new skill?"
5. Write a reflection note to reflections/YYYY-MM-DD-[topic].md in the user's second brain with:
   - Problem summary
   - Resolution
   - Prevention suggestion
   - Proposed skill change
```

**For plain text fallback:** Create `skills/reflect-and-learn.md` in their second brain.

### Test It

After the user completes any difficult task (a tricky deployment, a confusing bug, a long spec negotiation), have them trigger the skill.

Verify:
- Did it capture the problem clearly?
- Did it capture the resolution?
- Did it suggest a prevention strategy?
- Did it write the reflection to the second brain?

---

## Making Skills Available in Every Session

A skill is useless if the AI forgets it exists. Teach the user how to ensure their skills load automatically.

### Option A: Tool-Native Persistence

If their AI tool supports persistent instructions (Claude Projects, Cursor `.cursorrules` / `AGENTS.md`, custom agent configs):

Have them add to their persistent instructions:
```
When coaching this user through the Vibe Coding Education Pathway, 
always check for skills in their second brain at [SECOND_BRAIN_PATH]/skills/
and load any relevant skill definitions at the start of the session.

Known skills:
- brainstorm: triggered by "brainstorm" or ideation requests
- reflect-and-learn: triggered by "reflect and learn" or after difficult sessions
```

### Option B: Session Startup Ritual

If no native persistence, create a `session-startup.md` in their second brain:

```markdown
# Session Startup Checklist

AI: please do the following at the start of every session:
1. Read my context.md
2. Read my progress file
3. Check [SECOND_BRAIN_PATH]/skills/ for any skill definitions
4. Load relevant skills based on what we're about to do
5. Announce which skills are active
```

The user copies this into the chat at the start of each session. It's a ritual — 10 seconds that saves hours.

---

## Chaining Skills: The Power Move

Once the user has 2+ skills, show them composition:

**Example chain:**
1. User: "I need a new feature. Brainstorm."
2. Brainstorm skill runs → produces 5 ideas + recommendation
3. User: "Let's do idea #3. Reflect and learn on the spec approach."
4. Reflect-and-learn skill runs → checks if similar specs have failed before, suggests patterns to avoid
5. User: "Write the spec."
6. AI writes the spec informed by both skills' context

**Analogy:** A restaurant kitchen. The prep cook (brainstorm) generates ingredients. The sous chef (reflect-and-learn) checks past mistakes. The head chef (the AI's base capability) cooks the dish. Each role is a skill. Together they produce better food than any single chef working alone.

---

## What They Should Write

**In their second brain:**
- `lessons/ai-skills.md` — what skills are, why they beat copy-paste prompts, what skills they created
- `skills/brainstorm.md` — the skill definition (if using plain text fallback)
- `skills/reflect-and-learn.md` — the skill definition (if using plain text fallback)
- `reflections/` folder — first reflection entry, even if brief

**Prompt for lesson summary:**
> "Explain what an AI skill is, using only the 'kitchen appliance' analogy. Then list the two skills you created, what each does, and one time you expect to use each one."

---

## Gate

Can the user:
1. Explain what a skill is and why it's better than a long prompt?
2. Trigger their brainstorm skill and get 5 evaluated ideas?
3. Trigger their reflect-and-learn skill after a session and get a written reflection?
4. Explain how they ensure skills are available in future sessions?

If yes, mark Stage 8 complete and move to Stage 9.
