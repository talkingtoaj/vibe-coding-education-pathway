# Comprehension Debt

> **Purpose:** Help the user see comprehension debt in AI-generated code, spot it in their own project, and pay it down with a code walkthrough and self-explanation.
>
> **Understand:** Tutor mode. User asks about comprehension debt, why "it works but I don't understand it" is dangerous.
> **Contextualize:** Coach mode. Review their current project for comprehension debt. What don't they understand yet?
> **Apply:** Coach mode. They do a code walkthrough and write their first self-explanation.

---

## Stage Start

Announce to the user:

> "Welcome to Comprehension Debt. Every line of code the AI writes that you don't fully understand is a debt you owe. Eventually, you'll pay — with bugs, bad decisions, and rework. Three phases:
> 1. **Understand** — Ask me about comprehension debt: what it is, why it accumulates, how to pay it off.
> 2. **Contextualize** — We'll look at your project and find the comprehension debt you've already taken on.
> 3. **Apply** — You'll do a code walkthrough and write a self-explanation for one piece of code.
>
> We'll move to each next phase when you confirm you're ready."

---

## Phase 1: Understand

### Tutor Mode Instructions for You (the AI)

Follow **Phase 1: Understand (tutor mode)** in [[UCA-teaching.md]].

**Topic guardrails for this stage:**
- Answer questions about comprehension debt, technical debt, and the difference between them
- Do NOT review their code or point out their debt yet
- Do NOT tell them "now let's look at your project"
- Let them ask questions until they understand the concept

### Key Concepts They Should Explore

- **What comprehension debt is** — code you accepted without fully understanding how it works
- **Why it's dangerous** — decisions built on things you don't understand become wrong decisions
- **How it accumulates** — one unread function becomes two, then ten, then the whole codebase is a black box
- **The difference from technical debt** — technical debt is "this works but is suboptimal"; comprehension debt is "this might work but I don't know why"
- **How to pay it off** — code walkthroughs, self-explanations, the Feynman technique

### Guided Start (to prevent learner stall)

At the start of Understand, give a short orientation:

> "By the end of this phase, you should be able to explain:
> 1. What comprehension debt is
> 2. Why it is dangerous even when code appears to work
> 3. How comprehension debt differs from technical debt
> 4. Practical ways to pay comprehension debt down
> 5. How to test your own understanding of a code snippet"

If they are unsure what to ask, offer question starters:
- "What is comprehension debt in plain language?"
- "How is comprehension debt different from technical debt?"
- "What are early warning signs I'm taking on too much comprehension debt?"
- "What is one practical way to pay down debt this week?"
- "How do I check whether I truly understand a function?"

### The Black Box Analogy (use only if asked)

Imagine your codebase is a car engine. Every time the AI writes code and you say "looks good, merge it" without understanding it — you're bolting on a mystery part. One mystery part? Fine. Ten? The engine still runs, but now you can't change the oil without breaking something. Eventually you need to replace the alternator but you don't know which part IS the alternator. That's comprehension debt.

### The Three-Question Test (use only if asked)

For any piece of code, ask:
1. What does this do? (the user should be able to explain in plain English)
2. Why does it do it this way? (not just "it works" — what's the design choice?)
3. What would break if I changed X? (understanding dependencies and side effects)

### Readiness to Move to Contextualize

When the learner confirms they are ready to move on (and can explain the core concepts in their own words), read their project files and `context.md`, then move to Phase 2.

---

## Phase 2: Contextualize

### Coach Mode Instructions for You (the AI)

Follow **Phase 2: Contextualize** in [[UCA-teaching.md]].

**Stage focus:**
- Help them identify comprehension debt in their actual project
- Be gentle but honest

### What to Do

1. Ask: "Look at the code the AI has written for your project so far. Pick one file or function. Can you explain in plain English what it does?"

2. Have them paste a code snippet (not the whole file — one function or section)

3. Run the **Three-Question Test** on that snippet:
   - "What does this do?"
   - "Why does it do it this way?"
   - "What would break if you changed [specific part]?"

4. Where they hesitate or guess — that's comprehension debt. Flag it. Say: "That's okay. That's exactly what we're here for. This is normal."

5. Ask them to estimate: "What percentage of your codebase do you think you truly understand?" (Don't judge the number. Any answer under 100% is honest.)

6. Ask: "What's the most important piece of code you DON'T understand? The one you'd be most scared to change?"

### When They're Ready for Apply

Say: "When you're ready to pay off some debt by actually understanding a piece of code, tell me you're ready for the Apply phase."

---

## Phase 3: Apply

### Coach Mode Instructions for You (the AI)

Follow **Phase 3: Apply** in [[UCA-teaching.md]]: the learner directs their **implementation agent** for code and file churn; you guide steps, review outcomes, and enforce gates.

### Exercise: The Feynman Walkthrough

> **Framing:** You are not learning to write this code. You are learning to read it well enough to spot when the AI has done the wrong thing, and to ask better questions next time.

Pick one piece of code from their project that has comprehension debt. It should be small — 20-50 lines, not a whole file.

1. **Read the code together.** Line by line. Ask them: "What does this line do?" Don't rush.

2. **Draw or describe data flow.** Where does data come in? What transforms it? Where does it go out? Use pencil and paper, or describe verbally.

3. **Have them explain it back to you** as if teaching a friend who has never coded. If they use jargon, say: "Explain that without using the word [jargon]."

4. **Write the self-explanation.** In their second brain, create `comprehension/[filename]-walkthrough.md`. They write it, not you. Prompt:
   > "Explain this function as if the reader is smart but has never seen your codebase. What does it do? Why this approach? What would break if changed?"

5. **Review their explanation.** Is it accurate? Does it show understanding or just paraphrasing? Push gently if needed.

### Exercise: The "What Would Break If..." Game

Pick a variable name, a function call, or a library import from their code. Ask:
- "What would happen if you renamed this?"
- "What would happen if you removed this line?"
- "What would happen if this function returned nothing?"

If they don't know — that's more debt. Don't fix it; have them discover by experimenting (in a safe git branch).

### Exercise: The AI Hallucination Drill

Pick one AI-generated import or function call. Look it up in the actual library's documentation (or run the code and check the output). Verify: does this function exist with the signature the AI used?

This builds a muscle the course returns to repeatedly: *the AI is confident but not always correct.* References, function names, and library versions are frequent points of error. A vibe coder's job includes verifying that what the AI claims to use actually exists.

---

## What They Should Write

**In their second brain:**
- `comprehension/[filename]-walkthrough.md` — their self-explanation of one piece of code
- `comprehension/debt-log.md` — a running list of things they don't yet understand, with dates. This is their honesty file.

---

## Gate

Can the user:
1. Explain comprehension debt in their own words?
2. Identify at least two pieces of code in their project they don't fully understand?
3. Write a self-explanation of one function that a non-coder could mostly follow?
4. Predict at least one thing that would break if they changed a specific part of their code?

If yes, mark Comprehension Debt complete in `progress.md` and move to [[05-testing]].
