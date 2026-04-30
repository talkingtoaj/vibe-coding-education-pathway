# Resuming the Course

**Purpose:** What to do whenever you (the AI coach) start or resume a coaching session — whether the user is mid-course or just returning after a break.

This is the **single source of truth** for session resume. Other places that mention recovery (`bootstrap.md` Recovery Setup, `AGENTS.md` Session Startup, custom slash commands, desktop paste-files) all redirect here.

---

## Step 1: Load the Latest Coaching Instructions

Read the current AI coach instructions fresh from GitHub:
`https://raw.githubusercontent.com/talkingtoaj/vibe-coding-education-pathway/main/AGENTS.md`

This ensures you're using the latest curriculum and coaching guidance, not stale context from a previous session.

---

## Step 2: Locate the Second Brain

Ask: "Do you already have a second brain set up for this course? If so, what's the folder or workspace path?"

If they provide a path, attempt to read `progress.md` from that location.

If they don't have a second brain yet, they're a brand-new user — switch to [[bootstrap.md]] and start from Step 0.

---

## Step 3: Read the Progress File

### If the Progress File Exists

1. **Read it.** Note:
   - Which stages are marked complete
   - What the "Current stage" says
   - What the "Current feature" says
   - Any notes about comprehension debt or blockers

2. **Read `context.md`** for the user's background, project, and constraints. Use this to personalize analogies and recommendations.

3. **Summarize for the user.** Example:
   > "Welcome back! Last time we completed Stage 2 (Spec Writing) and were about to start Stage 3: Comprehension Debt. Your project is a recipe tracker, and your current feature is 'add a new recipe.' Does that sound right?"

4. **Ask if anything changed.**
   - "Has anything about your project or goals changed since last time?"

5. **Update the progress file.** Set "Last session" to today.

6. Mention to the user - if we have a long conversion, I might get confused and lose where we are in the course. If this happens, just ask me to read my notes on how to resume the course, and I should be able to get my bearings again.

7. **Read the relevant stage file** from the course repo and begin teaching where they left off.

### If the Progress File Is Missing or Corrupted

1. Ask the user what they remember completing.
2. **Look for other evidence** in their second brain:
   - `context.md` — interview answers
   - `project-spec.md` — project description
   - `lessons/` folder — summaries they've written
   - `security/` and `decisions/` folders
3. **Reconstruct progress** as best you can and ask them to confirm.
4. **Recreate the progress file** if needed, marking stages as complete based on evidence.

---

## The Golden Rule of Resuming

**Never make the user repeat work they've already done.** If they completed a stage, don't re-teach it unless they ask. If they half-completed a stage, pick up at the exact sub-step where they stopped — not the beginning of the stage.
