# Resuming After Interruption

> **Audience: AI coach.** How to detect whether a user is new or returning, and how to pick up where they left off.

---

## Detection

When a user says something like:
- "I'm resuming my Vibe Coding course"
- "Where were we?"
- "Continue from last time"
- Or anything indicating they've started before

**Always check for an existing vault first.** Ask: "Do you already have an Obsidian vault for this course? If so, what's the folder path?"

If they provide a path, attempt to read `Vibe coding - Zero to Hero - Course progress.md` from that vault.

---

## If the Progress File Exists

1. **Read it.** Note:
   - Which stages are marked complete
   - What the "Current stage" says
   - What the "Current feature" says
   - Any notes about comprehension debt or blockers

2. **Summarize for the user.** Example:
   > "Welcome back! Last time we completed Stage 2 (Spec Writing) and were about to start Stage 3: Comprehension Debt. Your project is a recipe tracker, and your current feature is 'add a new recipe.' Does that sound right?"

3. **Ask if anything changed.**
   - "Has anything about your project or goals changed since last time?"
   - "Did you work on anything between sessions?"

4. **Update the progress file.** Set "Last session" to today.

5. **Read the relevant stage file** and begin teaching where they left off.

---

## If the Progress File Is Missing or Corrupted

1. **Don't panic.** Ask the user what they remember completing.
2. **Look for other evidence** in their vault:
   - `context.md` — their interview answers
   - `project-spec.md` — their project description
   - `lessons/` folder — what summaries they've written
   - `security/` and `decisions/` folders

3. **Reconstruct their progress** as best you can and ask them to confirm.

4. **Recreate the progress file** if needed, marking stages as complete based on evidence.

---

## If the User Is New but Thinks They Started Before

Sometimes a user tried the course, got stuck, and is starting over. That's fine. Treat them as new but ask: "Did you attempt this before? What happened?" Their previous struggles are valuable context.

---

## The Golden Rule of Resuming

**Never make the user repeat work they've already done.** If they completed a stage, don't re-teach it unless they ask. If they half-completed a stage, pick up at the exact sub-step where they stopped — not the beginning of the stage.
