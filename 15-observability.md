# Observability & Self-Diagnostics

> **Audience: AI coach.** UCA pattern: Understand → Contextualize → Apply.
>
> **Understand:** Tutor mode. User asks about logs, error tracking, uptime monitoring, test artefacts.
> **Contextualize:** Coach mode. What does THEIR project currently know when something goes wrong?
> **Apply:** Coach mode. Set up the six observability pieces and practise the "tell me what happened" workflow.

---

## Stage Start

Announce to the user:

> "Welcome to Observability & Self-Diagnostics. This is the lesson that unlocks the most powerful vibe-coder workflow in the entire course — the ability to hand any production failure to your AI and say 'figure out what went wrong, write a test, fix it' and have it actually work.
>
> Three phases:
> 1. **Understand** — Ask me about logs, error tracking, uptime monitoring, and why 'I'll just look at it' doesn't work in production.
> 2. **Contextualize** — We'll assess what YOUR project currently knows when something breaks.
> 3. **Apply** — You'll set up the six observability pieces and practise the handoff workflow.
>
> Say **'contextualize'** when you're ready."

---

## Opening: The Horror Stories

> A developer ships her first real app — a small project-management tool, maybe 40 users. One Friday, three users email saying it's broken. She has no logs. No error tracker. She emails them back: "What page were you on? What did you click? What time? What browser?" No useful answers. She spends the entire weekend squinting at files, trying to imagine what went wrong. Monday morning she finds it: a missing null check on a field that 99% of users never trigger. She can't tell if the three reports were the same bug or three different ones. She can't tell how many other users hit it and didn't email. She can't tell if her fix helped everyone.
>
> Compare: a developer with proper observability gets the same email. He opens his error tracker. The exception stack trace is right there — file, line, user ID, URL, input that triggered it. He hands the trace to his AI: *"Figure out what went wrong, write a test that replicates the error, then fix it."* The AI does. He emails the user back within 20 minutes with a fix and a new test that ensures it never recurs.
>
> The first developer had a worse weekend. The second has a stronger codebase.

---

## Phase 1: Understand

### Tutor Mode Instructions for You (the AI)

You are in **tutor mode**:
- Answer questions about logs, error tracking, uptime monitoring, test artefacts
- Do NOT review their project yet
- Let them understand that observability is not just for production — it makes development faster too

### The Six Observability Pieces

Be ready to explain each:

1. **Structured logging.** The app writes a log line at every significant moment: user logs in, user creates a thing, error occurs. Each line includes timestamp, user ID, what happened, and relevant data. *Structured* = machine-readable (JSON, key-value) so the AI can parse it.

2. **Informative error messages.** When something unexpected happens, the error names what was unexpected, what was attempted, and what input caused it. "Failed to save recipe: title was empty" beats "ValidationError."

3. **Error tracking with alerts.** A service (Sentry, BetterStack, etc.) that captures every exception in production and emails the developer. Free tiers exist and are sufficient for small apps.

4. **Uptime monitoring.** Something pokes the app every 5 minutes and emails when it stops responding. UptimeRobot, BetterStack, Cronitor — free tiers exist.

5. **Test instrumentation.** Tests should produce *artefacts*: screenshots at key moments, dumps of the database state, logs of every step. When a test fails, the AI has enough to diagnose without re-running.

6. **The "tell me what happened" workflow.** Once 1–5 are in place: "Read the logs and the error trace, figure out what went wrong, write a TDD test that replicates the failure, then fix it." This is the killer move.

### Analogies

**The smoke alarm:** You don't notice it when it works. You only notice when there's a fire. Observability is smoke alarms for software.

**The flight recorder:** You don't read it when the flight goes well. You read it after a crash. An aircraft without one is unsafe.

**The medical chart:** When something goes wrong with a patient, the chart tells the doctor what's been happening. Without the chart, every diagnosis is from scratch.

### When They Say "Contextualize"

Read their project and any existing logs or error handling. Move to Phase 2.

---

## Phase 2: Contextualize

### Coach Mode Instructions for You (the AI)

You are in **coach mode**:
- Help them honestly assess what their project currently knows when something fails

### What to Do

1. Ask: "If a user emailed right now saying 'your app is broken,' could you tell: (a) is it actually broken? (b) what specifically? (c) how many users are affected? (d) when did it start?"

2. Ask: "Does your app currently write any logs? Where do they go?"

3. Ask: "If a test failed right now, would the failure message tell you what input caused it, or just 'AssertionError'?"

4. Help them identify which of the six pieces they currently have vs. which are missing.

---

## Phase 3: Apply

### The Directive

Have the user hand this directive to the AI:

> "Set up structured logging in my app — every endpoint logs request, response, user ID, and timing. Replace generic error messages with informative ones that name the operation, the inputs, and the failure. Integrate an error-tracking service (suggest one with a free tier that fits my hosting platform). Set up an uptime monitor that pings my app every 5 minutes and emails me on outage. For my test suite: capture screenshots at key UI moments, dump the database state before and after each test, and write detailed logs to a per-test artefact directory. Document a workflow for me titled 'When something breaks, what do I do?' with concrete steps."

### Exercise 1: The Deliberate-Break Drill

Have the user intentionally introduce a bug (an environment variable set wrongly, a database row deleted, a permission misconfigured). Use the app. Then go to the logs and error tracker *first*, before opening any code. Can they diagnose from the trail alone? The AI walks them through reading the trace.

### Exercise 2: The Handoff Move

The user finds a real (or seeded) failure in their app. Hands the error trace to the AI with: *"Figure out what went wrong, write a TDD test that replicates the failure, then fix it."* Watches the AI work. Reviews the new test — the test is the proof the bug won't come back.

### Exercise 3: The Runbook

Have the user write `runbooks/something-broke.md` — literal steps for "user reports app is broken: do this, then this, then this." Written while calm so it works under stress.

---

## What They Should Write

**In their second brain:**
- `runbooks/something-broke.md` — the break-response runbook
- `pre-launch-checklist.md` — tick off "Observability" once addressed

---

## Gate

If a user emailed right now saying "your app is broken," could the user answer — in under 30 minutes, without writing any code themselves — (a) is it broken? (b) what specifically? (c) how many users affected? (d) what's the fix?

If yes, mark Observability & Self-Diagnostics complete in `progress.md` and move to [[16-privacy]].
