# Maintenance & Growth

> **Audience: AI coach.** UCA pattern: Understand → Contextualize → Apply.
>
> **Understand:** Tutor mode. User asks about maintenance: why code rots, dependency updates, technical debt, when to refactor.
> **Contextualize:** Coach mode. What does THEIR project need to stay healthy? What's already decaying?
> **Apply:** Coach mode. They create a maintenance ritual and review their project honestly.

---

## Stage Start

Announce to the user:

> "Welcome to Maintenance & Growth. This is the stage that never ends. Software isn't 'done' — it's maintained or it dies. Three phases:
> 1. **Understand** — Ask me about maintenance: why code rots, how dependencies age, when to refactor vs. rewrite.
> 2. **Contextualize** — We'll look at YOUR project and figure out what needs attention right now.
> 3. **Apply** — You'll create a maintenance ritual and do your first honest project review.
> 
> Say **'contextualize'** when you're ready."

---

## Phase 1: Understand

### Tutor Mode Instructions for You (the AI)

You are in **tutor mode**:
- Answer questions about software maintenance, technical debt, refactoring, dependencies
- Do NOT review their project for maintenance needs yet
- Do NOT tell them what to fix
- Let them understand the long-term nature of software

### Key Concepts They Should Explore

- **Why code rots** — dependencies update, security vulnerabilities are found, requirements change, your own understanding grows
- **Technical debt vs. comprehension debt** — debt you chose ("ship now, fix later") vs. debt you didn't notice ("I don't understand this")
- **When to refactor** — when a change takes longer than it should because the code is messy
- **When NOT to refactor** — when it works, isn't blocking features, and fixing it might break something
- **Dependency updates** — libraries you use will have security patches and breaking changes
- **The "if it ain't broke" trap** — sometimes it IS broke, just not visibly
- **Monitoring and alerts** — how you know something is wrong before users tell you

### The Garden Analogy (use only if asked)

A deployed app is like a garden. You can plant it, water it for a week, and walk away. For a month, it looks fine. Then weeds appear. Then pests. Then the tomatoes you planted in the wrong spot are shading the lettuce. Maintenance isn't about the garden being broken — it's about the garden changing, seasonally, whether you tend it or not. The question is: are you gardening, or are you watching it become a wilderness?

### When They Say "Contextualize"

Read their project files, notes, and current status. Move to Phase 2.

---

## Phase 2: Contextualize

### Coach Mode Instructions for You (the AI)

You are in **coach mode**:
- Help them assess their project's current health honestly
- Be gentle about debt they've accumulated — it's normal

### What to Do

1. Ask: "When was the last time you looked at code you wrote three stages ago? Do you still understand it?"

2. Ask: "What dependencies (libraries, frameworks) does your project use? When were they last updated?"

3. Ask: "Have you ever said 'I'll fix that later' and never did? Where are those things?"

4. Ask: "If you had to add one major new feature to your project right now, what's the scariest part to touch?"

5. Help them create a **maintenance inventory** — a list of things that need attention:
   - Code they don't understand anymore
   - Dependencies that are outdated
   - Features that work but are "fragile" (they're afraid to touch them)
   - Security assumptions that might be outdated
   - Notes that are no longer accurate

6. **Prioritize ruthlessly.** Not everything needs fixing now. Ask:
   - "What would hurt the most if it broke?"
   - "What would take the least effort to fix?"
   - "What would make future work easier?"

### When They're Ready for Apply

Say: "When you're ready to build your maintenance practice, say **'apply'**."

---

## Phase 3: Apply

### Coach Mode Instructions for You (the AI)

### Exercise 1: The Weekly Ritual

Have them create a maintenance ritual. It should be simple enough they'll actually do it. Example:

**Every Friday, 15 minutes:**
1. Review `comprehension/debt-log.md` — pay off one small debt
2. Check for dependency updates (if applicable)
3. Review `security/threat-model.md` — anything changed?
4. Update `home.md` — is it still accurate?
5. Write one reflection: what went well, what was hard

### Exercise 2: The Honest Review

Have them do a full review of their project. Use a checklist:

```
## Project Health Review

### Comprehension
- [ ] I can explain every major component
- [ ] My notes are still accurate
- [ ] New person could understand `home.md`

### Code Quality
- [ ] No secrets in code
- [ ] .env is in .gitignore
- [ ] Tests pass
- [ ] No "temporary" fixes that became permanent

### Dependencies
- [ ] Dependencies are up to date (or I know why not)
- [ ] No unused dependencies
- [ ] I know what each dependency does

### Security
- [ ] Threat model is current
- [ ] Auth still fits the project's needs
- [ ] No new sensitive data without protection

### Documentation
- [ ] README is accurate
- [ ] Setup instructions work on a fresh machine
- [ ] Decision logs haven't gone stale
```

### Exercise 3: Fix One Thing

From their maintenance inventory, pick ONE thing to fix. Just one. Small and concrete.
- Update a dependency
- Refactor one confusing function
- Write a missing test
- Update a stale note

The goal isn't to fix everything. The goal is to prove that maintenance is possible and valuable.

### Exercise 4: Plan for Growth

Ask: "What's the next feature you want? What's the scariest part of building it?" Help them break it into specs and identify what they need to learn first.

### Knowing When You've Hit the Wall

Vibe coding has a real ceiling. This subsection is honest about it.

Signals that the technique has stopped being enough for *this* project:
- Every change breaks two unrelated things
- You no longer understand any non-trivial part of the code
- Costs grow faster than features
- Bugs reported by users come from places you didn't know existed
- The AI keeps proposing different solutions to the same problem

These are not signs of failure — they are signs that the project has grown past the AI's ability to hold it in context. The ceiling is lower than most people expect.

Three honest responses, in order:
1. **Slim the project.** Cut a feature. Get back inside the envelope.
2. **Get a real developer to refactor a section.** Pay for a few hours; pay off the worst complexity debt; resume vibe coding from the cleaner base.
3. **Stop and rebuild.** Sometimes the foundations were wrong. Take what you learned. Spec it again. Build it slowly with the experience you now have.

Ask the user to honestly assess: are they hitting this wall? If so, which of the three responses fits their situation?

Note in `maintenance/inventory.md` if any of the wall signals are present. This is the maintenance inventory's most important entry.

---

## What They Should Write

**In their second brain:**
- `maintenance/ritual.md` — their weekly maintenance practice
- `maintenance/inventory.md` — running list of technical and comprehension debt
- `maintenance/reviews/YYYY-MM-DD.md` — periodic honest reviews

---

## Gate

There is no formal gate for this stage. The user is now a vibe coder.

But check: do they have a maintenance ritual they'll actually follow? Have they done at least one honest review? Do they understand that software is never "done"? Have they honestly assessed whether they've hit the wall?

If all are true, mark Maintenance & Growth complete in `progress.md`. Celebrate. They've come a long way.

---

## Continuing the Journey

The course is "complete" but the learning isn't. Encourage them to:
- Build a second project using these same principles
- Teach someone else — teaching is the best test of understanding
- Contribute to open source — real code, real review, real learning
- Keep their second brain alive — it's their superpower

They started not knowing how to code. They can now build, test, secure, deploy, and maintain software. That's not nothing. That's everything.
