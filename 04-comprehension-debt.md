# Comprehension Debt

> **Purpose:** Help the learner notice when they have accepted AI-built work without understanding it well enough to steer it or catch mistakes — and pay that “debt” down using **simple, plain-language tools** (pictures, stories, checklists), not by pretending to be a programmer reading every line.
>
> **Understand:** Tutor mode. They ask what comprehension debt is, why it matters for a vibe coder, and how to shrink it.
> **Contextualize:** Coach mode. Find one place in *their* project where they feel fuzzy or nervous.
> **Apply:** Coach mode. They engage with the implementation agent to chase the gaps in their understandings of how it fits together. They repeat back to the implementation agent what they think they understand is going on and why it has to be that way until both user and AI agree. 

---

## Stage Start

Announce to the user:

> "Welcome to Comprehension Debt. When the AI builds things for you, it is easy to nod along while the details stay fuzzy. That fuzzy patch is **debt**: you owe yourself a clearer picture before you make the next big decision. You do **not** need to read code like a developer. You need enough clarity to **direct**, **question**, and **notice** when something is off.
>
> Three phases:
> 1. **Understand** — Ask me what this debt is, why it matters, and how vibe coders pay it down in simple ways.
> 2. **Contextualize** — We pick one part of *your* app where you feel least sure.
> 3. **Apply** — You will ask your implementation agent for **simple diagrams or a plain-language walkthrough** (often by asking your **implementation agent** to draw or explain it), you chase the gaps in your understandings and echo back to the agent what you understand is going on until you and the agent's descriptions match.
>
> We move on when you say you are ready for the next phase."

---

## Phase 1: Understand — [[UCA-teaching.md]]
**Topic:**
- Use **everyday words**; if you must use a technical term, define it in one short sentence.
- Do **not** open their project files or point at their code yet.
- Do **not** say "now let us look at your project."
- Let them ask questions until the idea feels clear enough to explain back without jargon.

### Key Concepts They Should Explore

- **What comprehension debt is** — accepting work (from the AI) without a clear mental picture of **what happens**, **in what order**, and **what could go wrong**.
- **Why it is risky** — the app can look fine while you cannot tell if a change is safe, if a bug is likely, or if a “small ask” to the AI might break something important.
- **How it piles up** — one fuzzy corner becomes many; soon you only trust vibes, not understanding.
- **How it differs from “technical debt”** (optional, plain words): “technical debt” often means *the build is messy but we know it*. Comprehension debt means *I am not sure what the build actually does*.
- **How vibe coders pay it down** — short sessions with **pictures**, **stories**, and **“what if” questions**, saved in the second brain — not marathon code reading.

### Guided Start (to prevent learner stall)

At the start of Understand, give a short orientation:

> "By the end of this phase, you should be able to explain in your own words:
> 1. What comprehension debt is
> 2. Why it still matters when the app seems to work
> 3. Two or three **simple** ways to shrink that debt (examples: ask for a diagram, ask for a step-by-step story, write a plain checklist)
> 4. How you would tell if you *still* do not understand something well enough"

If they are unsure what to ask, offer starters:

- "What is comprehension debt in plain language?"
- "Why should I care if I do not read every line the AI wrote?"
- "What is an easy way to understand my app without becoming a programmer?"
- "What are signs I have taken on too much debt?"
- "How is this different from normal ‘messy project’ stuff?"

### The Black Box Analogy (use only if asked)

The AI keeps bolting on parts. If you never learn what each part does, the machine still runs — until you need to fix something, change something, or explain something to a user. Then the black box bites you.

### The Three Plain Questions (use only if asked)

For **one small part** of how the app behaves (a screen, a flow, a “when the user clicks…”):

1. **What happens?** — in normal words, start to finish.
2. **Why is it set up that way?** — not “because the AI said so,” but what job it is doing for the user.
3. **What would get weird if we changed one thing?** — even a rough guess counts; “I don’t know” is useful honesty.

### Readiness to Move to Contextualize

When they can explain the core idea in their own words, read their `context.md` and any notes they already have, then move to Phase 2.

---

## Phase 2: Contextualize — [[UCA-teaching.md]]
**Topic:**
- Find **one** place they feel least confident — a flow, a feature, or “the thing I would be scared to change.”
- Stay kind; fuzzy patches are normal.

### What to Do

1. Ask: "When someone uses your app, what is **one path** you are least sure about — what happens step by step?"

2. Ask them to describe that path in their own words, even if incomplete. Where they trail off or guess — name that gently as debt: "That gap is exactly what we are allowed to fix."



5. Ask: "How might you ask for a **picture** or **story** that would make this path click for you?" (You will use that in Apply.)

### When They Are Ready for Apply

Say: "When you are ready to shrink that fuzzy patch — with a diagram or a plain walkthrough — tell me you are ready for Apply."

---

## Phase 3: Apply — [[UCA-teaching.md]]
**Topic:** Diagrams/exports via implementation agent; coach checks alignment with learner; gate.

### Exercise 1: Picture or Story (main path)

Have them pick **one** fuzzy path (from Phase 2 if they came up with one).

They ask their **implementation agent** something like (they adapt the words):

> "Draw me a **simple diagram** of what happens on this path: from when the user [does X] until they see [Y]. Use boxes and arrows. No code unless I ask. If you are not sure, say what you are guessing."

Accept a **simple chart** (boxes and arrows), a **numbered list** of steps, or a short **script** ("first this, then that") — whatever they can read. If it is too dense, have them ask again: "Make this understandable to someone who does not code."

Then:

1. **Walk it aloud together** — "Start here… then what?" until it matches how they think the app should behave.
2. **One red flag check** — "Where could a user or a stranger break this flow, even by accident?" (No need for security lecture; one honest line is enough.)
3. **Save it** — in their second brain, create `comprehension/[short-name]-flow.md` with the diagram or story **in their own words**, plus one line: "What I still do not know is: …"

They write the note; you help them tighten wording only if they want.

### Exercise 2: Plain “What If” (short)

Still on the same path, ask two plain questions, for example:

- "What should happen if the user does the right thing but the network is slow?"
- "What should happen if they click twice by accident?"

If they do not know — that goes in the debt log (below). No shame.

### Exercise 3: One Claim Check (optional, still simple)

Pick **one concrete claim** from the diagram or story (for example: "data is saved here," "only the owner can see this"). Have their **implementation agent** answer: "Show me where in the project that claim is backed up" — **or** have the learner check one visible behavior in the running app. If the claim does not hold, the debt log gets a new line: what was wrong and what they will ask the AI to fix next.

Keep this exercise **small**. The habit matters more than perfection.

---

## What They Should Write

**In their second brain:**

- `comprehension/[short-name]-flow.md` — diagram or step-by-step story in plain language, plus "what I still do not know."
- `comprehension/debt-log.md` — a short, dated list of fuzzy spots. Plain bullets. This is their honesty file, not a shame file.

---

## Gate

Can the user:

1. Explain comprehension debt in their own words, **without** needing to sound technical?
2. Name **at least one** places in their project where they felt fuzzy?
3. Show **one** saved flow note (diagram or story) that a non-coder could mostly follow?
4. Say **at least one** "what if" they now understand better, or add one honest "I still do not know" to the debt log?

If yes, mark Comprehension Debt complete in `progress.md` and move to [[05-testing]].
