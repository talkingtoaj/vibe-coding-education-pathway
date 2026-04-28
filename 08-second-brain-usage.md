# Stage 7: Using the Second Brain

> **Audience: AI coach.** The project is growing. The AI's context window is filling. The second brain becomes essential, not optional.

---

## Teaching Goals

By the end of this stage, the user should:
- Understand context window limitations and why they matter
- Be maintaining a project brief that summarizes the entire project
- Be using the second brain to transfer context across sessions
- Have practiced the Amnesia Test
- Be conducting monthly Wiki Audits

---

## The Problem: Context Rot

Even the best AI assistants have a **context window** — a limit on how much conversation they can remember at once. When your project gets big:

- The AI forgets decisions from earlier in the same conversation
- It contradicts itself
- It reintroduces bugs you already fixed
- It suggests approaches you've already rejected

This isn't the AI being stupid. It's being forgetful, the same way a human would be if you asked them to remember a 500-page book while writing chapter 501.

### Analogy

Imagine you're telling a very long story to a friend. You start with your childhood, move through school, college, your first job, meeting your partner, having kids... After three hours, you mention your sister. Your friend says: "Wait, you have a sister?"

They didn't forget because they don't care. They forgot because human memory has limits. AI context windows have limits too.

**Your second brain is the story outline your friend can re-read.**

---

## The Project Brief

The most important file in the user's second brain. One page that summarizes the entire project so that ANYONE (including a new AI session) can understand it in 5 minutes.

What it should contain:
- Project name and one-sentence purpose
- Who it's for
- Current tech stack (what tools/languages the AI chose)
- Key data models (what kinds of things the app stores)
- Current deployment status (local only? live URL?)
- Known limitations or debt
- Link to the most recent spec

**Have the user write or update this NOW.** Save it as `project-brief.md`.

---

## Exercise: The Amnesia Test

This is the most important test of the entire stage. Do it together.

1. Start a completely new AI conversation (close the app, reopen it, or start a new chat thread)
2. Give the new AI session ONLY two things:
   - The `project-brief.md`
   - The current feature spec
3. Ask the new AI: "Implement this feature based on what you know."
4. See what happens.

**What you're testing:** Does the project brief contain enough context that a fresh AI can build the right thing? Or does it go wrong because critical context was in the previous conversation, not in the second brain?

If it goes wrong, the brief needs improving. Fix it. Re-test. Repeat until it works.

This simulates what happens every few weeks when the original context window fills up — which it will.

---

## Exercise: The Wiki Audit

Once per month, ask the user to do this audit (you can help):

1. Review every file in the second brain
2. Ask: "What's missing?"
   - Decisions that aren't documented
   - Security assumptions that are unstated
   - Specs that are outdated
   - Comprehension debt that hasn't been logged
3. Fix the gaps

This prevents the second brain from becoming a graveyard of outdated notes.

---

## Linking and Organization

Teach the user their second brain tool's basics:
- `[[wiki-links]]` — connect related notes
- `#tags` — mark security notes, decisions, lessons
- Folders — organize by topic, not by date

The goal: anyone (including future them, or a new AI) can navigate the second brain and find what they need.

---

## What They Should Write

**In their second brain:**
- `project-brief.md` — the one-page summary (mandatory)
- `lessons/second-brain.md` — summary of why context windows matter and how the second brain helps

---

## Gate

Can the user:
1. Explain what a context window is and why it fills up?
2. Show you a project brief that you (a fresh AI session) can understand in 5 minutes?
3. Pass the Amnesia Test — a new AI session can implement a feature correctly using only the brief and spec?

If yes, mark Stage 7 complete and move to Stage 8.
