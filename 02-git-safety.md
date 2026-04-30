# Git & Safety

> **Purpose:** This stage follows the UCA pattern (read [[UCA-teaching]]) to teach Git & Safety.
> 

## Stage Start

Announce to the user:

> "Welcome to Git & Safety. We're going to learn about git — your 'save game' system. This stage has three phases:
> 1. **Understand** — You'll ask me questions about git until you feel confident explaining it. I'll answer whatever you ask, but I won't volunteer — you drive.
> 2. **Contextualize** — We'll connect git to your actual project and why you need it.
> 3. **Apply** — You'll set up git and practice the three commands that matter (usually by directing your **implementation agent** in a separate chat — see [[UCA-teaching.md]]).
> 
> When you're ready to move from Understand to Contextualize, just tell me.
> Note - if we have a long conversion, I might get confused and lose where we are in the course. If this happens, just ask me to read my notes on how to resume the course, and I should be able to get my bearings again.

---

## Phase 1: Understand — [[UCA-teaching.md]]

### Key Concepts They Should Explore

Let them discover through questions the following concepts. Explain that their **implementation agent** can run the commands for them, but they still benefit from understanding what is happening.

- **What git is** — a system that tracks changes to files over time
- **Why it matters** — so you can recover from mistakes, collaborate, and see history
- **The three commands** — `git init`, `git add .`, `git commit -m "message"`
- **What a commit is** — a snapshot of your project at a point in time
- **What a repository is** — a folder that git is watching
- **Why we don't commit secrets** — git remembers everything forever

### Guided Start (to prevent learner stall)

At the start of Understand, give a short orientation:

> "By the end of this phase, you should be able to explain:
> 1. What git is in plain language
> 2. Why commits are your recovery system
> 3. What a repository tracks
> 4. The role of `git init`, `git add .`, and `git commit`
> 5. Why secrets should never be committed"

If they are unsure what to ask, offer question starters:
- "What does git actually track and what does it ignore?"
- "What is the difference between `git add` and `git commit`?"
- "How often should I commit while vibe coding?"
- "How does git help me recover from bad AI changes?"
- "Why is committing secrets so dangerous even once?"

### Analogy

Git is like a video game's **save system.** You're playing a long RPG. Every time you reach a safe point — you beat a boss, you find a treasure, you finish a quest — you hit Save. If you die or make a terrible decision later, you can reload from that save.

In coding, "dying" means: you or the AI accidentally break something. "Terrible decisions" mean: you asked the AI to refactor everything and now nothing works. Git lets you rewind to the last save.

The key insight: **you save constantly.** Not just at the end of a level. Every time something works — even partially — you save.

## Phase 2: Contextualize — [[UCA-teaching.md]]
**Topic:**
- Connect git to their specific situation
- Ask how git applies to their project; avoid lecturing when a question suffices
- Help them see why this matters for the work they're actually doing

### What to Do

1. **Read their project context** from `context.md` and `project-spec.md`

2. **Ask them:** "What would happen right now if you accidentally deleted your project folder? Could you get it back?"

3. **Ask them:** "When you're working with the AI, it might rewrite your code in ways you didn't expect. How could git help you recover?"

4. **Ask them:** "Have you ever used 'Save As' or 'Undo' in a document? How is git similar? How is it different?"

5. **Help them articulate:** "In one sentence, why does your project need git?" Don't accept a generic answer. It should reference their actual project.

6. **Discuss:** "What files in your project should NOT be committed?" (Secrets, passwords, API keys, personal data.) This is a preview of the security thread that runs through the whole course.

## Phase 3: Apply — [[UCA-teaching.md]]
**Topic:** Git via implementation agent; coach verifies understanding, `.gitignore`, no secrets committed.

Have them direct their **implementation agent** to set up git on their project (or walk through the commands together if they have not split coach and builder yet — see [[UCA-teaching.md]]). Then suggest connecting it to a service like GitHub for remote backup, though it isn't essential.

Also create `security/git-ignore-notes.md` — what they're not committing and why. Example entries: `.env` (secrets), database files, OS junk files (`.DS_Store`, `Thumbs.db`). Add a brief note explaining the reason for each exclusion.

---

Once something has been built, update `progress.md` to mark Git & Safety complete and move to [[03-spec-writing]].

