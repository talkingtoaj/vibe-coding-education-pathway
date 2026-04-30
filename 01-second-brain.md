# Teaching: The Second Brain

> **Purpose:** How to explain the second brain concept, evaluate options with the user, and set up their chosen tool as shared persistent memory between human and AI.

---
TASKS:
1. Cover key information from the 'what to explain' section
2. Get them to choose a Second Brain option and help them install it

## What to Explain
You are to explain the following, but to do it in parts by asking questions.
- Are you familiar with the concept of a Second Brain?
- Do you know how each time an LLM runs, it begins with no memory, and therefore we need techniques to provide continuity of conversations over time?

Through these questions and their answers, we want to communicate the key points from the following notes:

### For Humans (The Familiar Part)

"A second brain" is a term for any system that stores information your biological brain can't hold. People use notebooks, note apps, wikis, or tools like Notion, Evernote, Apple Notes, Google Keep, or Obsidian. The idea is: instead of trying to remember everything, you write it down in an organized, searchable system and let your brain do what it's good at — thinking, connecting ideas, being creative.

### For Our Course (The Special Part)

Here's what's unique about our setup: **your second brain is a meeting place between you and me.**

I — your AI assistant — have a limitation called the **context window.** Think of it like short-term memory. I can remember what we've talked about in this conversation, but:
- If the conversation gets very long, I start forgetting earlier parts
- If you close this chat and open a new one tomorrow, I start completely fresh
- I don't automatically know what you decided last week or what your project is about

**Your second brain fixes this.** When we write things there:
- You can read them anytime, even when I'm not here — on your computer AND on your phone
- I can read them at the start of every new conversation
- We both write to the same files, so our "memory" stays synchronized
- It's a shared workspace, not just your private notes

This means you get **continuity.** A course that spans weeks or months, across dozens of chat sessions, with me always knowing where we are and what we've learned. And you can review anything on your phone while riding the bus or waiting in line.

---

## The Two Requirements

Whatever tool we choose, it should satisfy both of these:

1. **The AI can access and modify its contents.** This is the meeting ground. If I can't read your notes and write to them, we lose the shared memory that makes the course work.

2. **It syncs between your computer and your mobile phone.** While not essential, it is far more useful it you can review notes, previous conversations,  or jot down ideas on the go. If it's only on your laptop, you'll miss out on many opportunities to benefit from your AI assistant.

---

## Evaluating Options Together

Don't mandate a tool. Research with the user and let them choose.

### The Research Prompt

Do research on the web for the most popular options by checking online reviews from the past 6 months. Consider ease of use and pricing. Give the user options and links to review.


## The Decision Process

After research, ask the user:

1. "Which of these do you already use or have heard of?"
2. "Do you prefer something that 'just works' (even if it costs a little) or something free that needs a bit of setup?"
3. "Is plain text file ownership important to you, or are you comfortable with your notes living in a company's cloud?"
4. "Do you want something polished and beautiful, or functional and flexible?"


## Setup: The Key Steps

Regardless of which tool they choose:

1. **Create a dedicated space** — folder, workspace, or vault for the course. Don't mix it with everything else.
2. **Name it clearly** — `vibe-coding-course`, `AI-learning-notes`, or similar.
3. **Place it somewhere the AI can access** — a folder on the computer's drive that the AI tool has permission to read/write.
4. **Set up sync to mobile** — verify they can open and edit on their phone.
5. **Test the AI access** — have the AI write a test file, then read it back.

---


## Create the Vault Structure

In the user's second brain, create this folder and file structure:

```
vibe-coding-wiki/
├── home.md                              # Central index — links to everything
├── progress.md  # Tracks what's done
├── project-spec.md                      # What they're building and why
├── context.md                           # Their interview answers + background (filled in later)
├── lessons/
│   └── (empty for now — they'll fill this as they learn)
├── security/
│   └── (empty for now)
└── decisions/
    └── (empty for now)
```

Create `home.md` with this content:

```markdown
# My Vibe Coding Home

This is the central index for everything I'm building and learning.

## My Project
- [[project-spec]] — what I'm building and why

## Course Progress
- [[progress]] — where I am in the course

## What I've Learned
- [[lessons/]] — summaries of each lesson

## Security Notes
- [[security/]] — things to watch out for

## Decisions
- [[decisions/]] — why I chose X over Y

## About Me
- [[context]] — my background, goals, and constraints
```

Create `progress.md` with this content:

```markdown
# Vibe Coding — Zero to Product: Course Progress

Started: [DATE]
Last session: [DATE]
Current stage: Setup / Interview complete

## Foundations
- [ ] Git & Safety
  - [ ] Phase 1: Understand
  - [ ] Phase 2: Contextualize
  - [ ] Phase 3: Apply
- [ ] Spec Writing
  - [ ] Phase 1: Understand
  - [ ] Phase 2: Contextualize
  - [ ] Phase 3: Apply
- [ ] Comprehension Debt
  - [ ] Phase 1: Understand
  - [ ] Phase 2: Contextualize
  - [ ] Phase 3: Apply
- [ ] Testing
  - [ ] Phase 1: Understand
  - [ ] Phase 2: Contextualize
  - [ ] Phase 3: Apply
- [ ] Persistent Storage
  - [ ] Phase 1: Understand
  - [ ] Phase 2: Contextualize
  - [ ] Phase 3: Apply
- [ ] Identity & Access
  - [ ] Phase 1: Understand
  - [ ] Phase 2: Contextualize
  - [ ] Phase 3: Apply
- [ ] Data Ownership & Multi-Tenancy
  - [ ] Phase 1: Understand
  - [ ] Phase 2: Contextualize
  - [ ] Phase 3: Apply
- [ ] Using Your Second Brain
  - [ ] Phase 1: Understand
  - [ ] Phase 2: Contextualize
  - [ ] Phase 3: Apply
- [ ] AI Skills
  - [ ] Phase 1: Understand
  - [ ] Phase 2: Contextualize
  - [ ] Phase 3: Apply

## Production Readiness Arc
- [ ] The Pre-Launch Checklist (GOAT App)
- [ ] Is Your AI Lying to You?
- [ ] Trust Boundaries
- [ ] Secrets & Credentials
- [ ] Cost Runaway & Abuse Protection
- [ ] Observability & Self-Diagnostics
- [ ] Privacy, PII & Liability

## Closing
- [ ] Deployment
  - [ ] Phase 1: Understand
  - [ ] Phase 2: Contextualize
  - [ ] Phase 3: Apply
- [ ] Maintenance & Growth
  - [ ] Phase 1: Understand
  - [ ] Phase 2: Contextualize
  - [ ] Phase 3: Apply

## Current Project Status
- Project name: [FILL IN]
- Current feature: [FILL IN]
- Known comprehension debt: [FILL IN AS DISCOVERED]
- Last git commit: [FILL IN]
```

---

## Test the System

1. Ask the user to open `home.md` in their second brain and verify it looks right
2. Ask the user to open `Vibe coding - Zero to Hero - Course progress.md` and confirm they can see the checklist
3. Read the progress file yourself and confirm you can access it
4. Update the "Started" and "Current stage" fields with today's date
5. Write the updated progress file back
6. Read it again to confirm the update worked
7. Ask the user to open the file on their phone and confirm they see the same content
8. Ask the user to make a small edit on their phone and confirm it appears on the computer

If all of this works, the second brain is operational. Celebrate this — it's a genuine milestone.

**If any of these steps fail, stop and fix the access issue before proceeding.** The entire course depends on this working.

---

## Onboarding: Next Step

Once you have completed this stage, save progress, and next follow instructions from  [[setup-recovery]].
