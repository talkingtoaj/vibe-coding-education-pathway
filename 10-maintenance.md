# Stage 9: Maintenance & Growth

> **Audience: AI coach.** The user is now a steward, not just a builder. Teach sustainable practices.

---

## Teaching Goals

By the end of this stage, the user should:
- Understand that software is never "done"
- Be conducting regular comprehension audits
- Be updating their threat model with every new feature
- Have created an onboarding document for future maintainers
- Understand that maintenance is where most projects die — and how to prevent that

---

## The Mindset Shift

Deployment is not the finish line. It's the starting line of a much longer race.

After deployment, the user is responsible for:
- Keeping the app running
- Fixing bugs users report
- Adding features users request
- Updating dependencies (libraries the app relies on)
- Monitoring for security issues
- Paying hosting costs (if applicable)

**Analogy:** Building a house is exciting. Plumbing, wiring, painting, furniture. But once you move in, the real work begins: fixing leaks, replacing appliances, cleaning gutters, patching the roof. The house doesn't maintain itself. Neither does software.

---

## Ongoing Practices

### Monthly Comprehension Audits

Pick one major component. Ask: "If I delete this, what breaks?" If the answer is "I don't know," study it until they do.

This is the Deletion Test from the programmer pathway, adapted for vibe coders.

Save findings to `comprehension-log.md`.

---

### Security Reviews

Every new feature = new attack surface. Before adding any feature, ask:
- "How could someone misuse this?"
- "What new data does this expose?"
- "Who can access this, and who shouldn't?"

Document in `security/threat-model.md`.

---

### Dependency Updates

The app relies on other people's code (libraries, frameworks, packages). These get security patches.

Monthly: ask the AI to check for security updates. Ask: "Are there any known vulnerabilities in the libraries we're using?"

This is like checking for recalls on your car. Boring but critical.

---

### The "Explain to a Stranger" Test

Monthly: can the user explain their entire app — every feature, every data flow, every security boundary — to someone who's never seen it? If not, their comprehension debt is growing.

---

## Exercise: The New Developer Simulation

Pretend the user is handing their project to someone else. Have them create `onboarding.md` — everything a new person would need to know to take over.

Include:
- What the app does and who it's for
- Tech stack and why
- How to set up the development environment
- How to deploy
- Where secrets live (environment variables, not in code)
- Known security considerations
- Where the comprehension debt lives (what's fragile or poorly understood)

If there are parts the user can't explain, those are their study priorities.

---

## Exercise: The Feature Graveyard

Create `graveyard.md`. Every time the user considers a feature but decides not to build it, write why. This prevents the AI from repeatedly suggesting things they've already rejected.

Example:
- "User profiles with photos — rejected: adds storage complexity and moderation risk for MVP"
- "Real-time chat — rejected: requires WebSockets, too complex for current team size"

---

## The Sustainability Checklist

Every month, review together:

- [ ] Can I explain every major component without looking at the code?
- [ ] Is my threat model up to date?
- [ ] Are my dependencies patched?
- [ ] Is my project brief current?
- [ ] Is my second brain organized and useful?
- [ ] Am I still excited about this project?

**The last one matters.** If the user isn't excited, the project will rot. Either rekindle the excitement or sunset the project gracefully.

---

## What They Should Write

**In their second brain:**
- `onboarding.md` — the handover document
- `graveyard.md` — rejected features and why
- `lessons/maintenance.md` — summary of ongoing practices

---

## Gate

There is no formal gate for Stage 9. The user is now a vibe coder.

But before declaring them "complete," verify:
1. They have an up-to-date project brief
2. They have a threat model that's been updated within the last month
3. They can explain their app to a stranger
4. They have a comprehension log with at least 10 entries
5. They know how to update dependencies

If all are true, mark Stage 9 complete in their progress file. Celebrate. They've come a long way.

**Remind them:** this isn't the end. It's the beginning of maintaining something real. The course is over, but the learning never stops.
