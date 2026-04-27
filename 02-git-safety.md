# Stage 1: Git & Safety

> **Audience: AI coach.** Teach git as a "save game" system. Focus on exactly three commands.

---

## Teaching Goals

By the end of this stage, the user should:
- Understand git as "Save As with a memory"
- Know three commands: `git init`, `git add .`, `git commit -m "description"`
- Have initialized git in their project folder
- Have made their first commit
- Understand that git history is permanent (security implication)
- Be able to explain git to a friend without jargon

---

## Analogy

Git is like a video game's **save system.** You're playing a long RPG. Every time you reach a safe point — you beat a boss, you find a treasure, you finish a quest — you hit Save. If you die or make a terrible decision later, you can reload from that save.

In coding, "dying" means: you or the AI accidentally break something. "Terrible decisions" mean: you asked the AI to refactor everything and now nothing works. Git lets you rewind to the last save.

The key insight: **you save constantly.** Not just at the end of a level. Every time something works — even partially — you save.

---

## What to Teach

### Installation

**Windows:**
- Download Git from git-scm.com
- Run the installer. Accept defaults for almost everything.
- One important choice: when it asks about "Adjusting your PATH environment," choose "Git from the command line and also from 3rd-party software."
- After installation, open PowerShell and type: `git --version`
- If it says something like `git version 2.x.x`, you're done.

**Mac:**
- Open Terminal (Cmd+Space, type "Terminal")
- Type: `git --version`
- If not installed, it will prompt you to install developer tools. Click "Install."

**Linux:**
- Usually pre-installed. If not: `sudo apt install git`

### The Three Commands

These are the only ones they need for now. Don't teach branches, merges, pull requests, or anything else.

1. **`git init`** — Turn a folder into a tracked project. Run once, in the project folder.
2. **`git add .`** — Stage changes for saving. The dot means "everything in this folder."
3. **`git commit -m "description"`** — Save a checkpoint with a note about what changed.

**When to commit:**
- Before the AI writes any code (empty commit: "Initial commit")
- Every time something works
- Before trying something risky ("Before refactoring the data model")
- At the end of every session

### What NOT to Commit

This is a security lesson. Explain:

"Git remembers everything you commit. Forever. Even if you delete it later, it's still in the history. So you must never commit files containing passwords, API keys, or secrets."

Show them `.gitignore` — a file that tells git "ignore these files." The AI should create one that ignores:
- `.env` files (environment variables, often contain secrets)
- Any file with "secret" or "key" in the name
- Database files (if local SQLite, sometimes)
- `__pycache__` and similar generated folders

Have the AI create the `.gitignore` and explain every line.

---

## Exercises

### Exercise 1: First Commit

1. Navigate to the project folder in PowerShell/Terminal
2. Run `git init`
3. Run `git add .`
4. Run `git commit -m "Initial commit before any code"`
5. Verify: run `git log` — they should see their commit

### Exercise 2: The Disaster Recovery Drill

This is the most important exercise. They must actually do it.

1. Create a file called `test.txt` with the words "This is important."
2. Add and commit it: `git add test.txt && git commit -m "Added test file"`
3. Delete `test.txt`
4. Panic appropriately (encourage them to actually feel the "oh no" moment)
5. Recover it: `git checkout -- test.txt` or ask the AI to help recover
6. Verify the file is back
7. Delete `test.txt` again
8. Commit the deletion: `git add . && git commit -m "Deleted test file (on purpose)"`
9. Recover from the previous commit: `git checkout HEAD~1 -- test.txt`
10. Explain: we can recover from *any* commit, not just the most recent

### Exercise 3: Commit Habit

For the rest of this session, make a rule: **every time the AI implements something that works, commit immediately.** The user should type the commit command themselves — this builds muscle memory.

---

## What They Should Write

**In their vault:** `lessons/git-basics.md`

Prompt them with: "Explain git to a friend who has never coded, using only the 'video game save' analogy. Don't use the words 'repository,' 'version control,' or 'branch.'"

They write it. You review it. If they use forbidden words, ask them to rewrite.

---

## Gate

Can the user:
1. Initialize git in a new folder?
2. Add files and make a commit?
3. Recover a deleted file from a previous commit?
4. Explain what git is without using jargon?

If yes, mark Stage 1 complete in their progress file and move to Stage 2.

If no, practice more. There's no rush.
