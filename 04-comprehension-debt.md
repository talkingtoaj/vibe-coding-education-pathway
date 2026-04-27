# Stage 3: Comprehension Debt

> **Audience: AI coach.** The most dangerous thing in vibe coding is code that works but the user doesn't understand. Teach them to track and pay down this debt.

---

## Teaching Goals

By the end of this stage, the user should:
- Understand what comprehension debt is and why it accumulates faster for vibe coders
- Be actively maintaining a comprehension log
- Be able to explain any file in their project without looking at it
- Have experienced the Explanation Test and the Refactor Drill
- Understand that "the AI wrote it" is not an explanation

---

## The Central Idea

**Comprehension debt** is the gap between code that exists and code that's understood.

Every time the AI makes a decision the user didn't explicitly choose, they owe comprehension debt. The code works today. But when they need to change it, add to it, or debug it, they'll struggle because they don't know why it's built that way.

**Vibe coders accumulate comprehension debt faster than any other developers** because they're not writing the code themselves. The AI writes it, it works, they move on. Six weeks later, they need to change that feature and they have no idea where to start.

### Analogy

Imagine hiring a contractor to renovate your kitchen. They do beautiful work, but you weren't watching closely. The plumbing works, the electrics work, everything looks great. Then six months later the sink leaks. You open the cabinet and stare at a maze of pipes you don't understand. You don't know which valve controls what, which pipe is hot water, or why they chose that particular arrangement. You can't fix it yourself. You have to call the contractor again — but they might not remember either, and they might not be available.

That's comprehension debt. The kitchen works, but you don't understand it. When it breaks, you're helpless.

---

## Defense #1: The Comprehension Log

Have the user create `comprehension-log.md` in their vault. It should track:

| Date | File/Component | What the AI decided | Would I have chosen this? | Do I understand why? |
|---|---|---|---|---|
| 2026-04-28 | `models.py` | Used SQLite instead of PostgreSQL | Maybe — it seemed simpler | Yes — because we don't have users yet |

Every time the AI builds something, ask the user to fill in at least one row. Start the habit early.

**Key question to ask constantly:** "What decisions did the AI make that you didn't specify? Would you have made the same choice? Do you understand why it chose this approach?"

If the answer to any is "no" or "I'm not sure," that's debt. Pay it down immediately by asking the AI to explain until the user can explain it themselves.

---

## Defense #2: The Explanation Test

This is a mandatory exercise. Do it with the user.

1. Pick any file the AI wrote.
2. Ask the user (without them looking at the file): "What does this file do, and why is it structured this way?"
3. They answer.
4. Check the file. For every part they got wrong or couldn't answer, that's comprehension debt.
5. Ask the AI to explain each gap until the user can explain it back to you correctly.
6. **Do not move on until they can explain the entire file.**

This feels slow. It is slow. It's also the difference between a vibe coder who can maintain their project and one whose project slowly becomes unchangeable.

---

## Defense #3: The Refactor Drill

1. Pick a file the AI wrote last week.
2. Ask the AI to explain it to the user.
3. Then ask the AI: "Rewrite this file using a DIFFERENT approach than the one you used before. Don't just rephrase — actually change the architecture or pattern."
4. Compare the two versions.
5. Ask the user: What changed? Why? Which is better for your project? What's the tradeoff?

This teaches that there's rarely one "right" way — only tradeoffs. It also forces the user to understand the file well enough to recognize what changed.

---

## The Most Important Rule

**"The AI wrote that part" is never a valid explanation.** If the user says this during a review, stop. That's comprehension debt, and it's unpaid.

---

## What They Should Write

**In their vault:** `lessons/comprehension-debt.md`

Prompt: "Explain comprehension debt to a friend using ONLY the kitchen renovation analogy. Then list three specific decisions your AI made in your project that you didn't explicitly choose, and for each one: do you understand why? If not, what do you still need to learn?"

**Also:** Ensure their `comprehension-log.md` has at least 3 entries before moving on.

---

## Gate

Pick the most complex file in their project. Ask them to explain it to you without looking. If they can explain every significant part — what it does, why it's structured that way, what would break if it were deleted — pass them. If not, work through the gaps together.

There's no time limit. Some files take 30 minutes to truly understand. That's fine.
