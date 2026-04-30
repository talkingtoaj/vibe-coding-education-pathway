# Is Your AI Lying to You?

> **Purpose:** Build healthy skepticism of confident-wrong output—four deception patterns, which apply to their project, then an audit that surfaces and fixes at least one real issue.
>
> **Understand:** Tutor mode. User asks about AI deception, fake data, useless tests, hallucinated dependencies.
> **Contextualize:** Coach mode. Which of the four deceptions are present in THEIR project?
> **Apply:** Coach mode. They run the audit directive, find at least one real deception, and fix it.

---

## Stage Start

Announce to the user:

> "Welcome to 'Is Your AI Lying to You?' This isn't a lesson about AI being malicious. It's about AI being *confident when it shouldn't be* — and about you building the muscle to check rather than trust.
>
> Three phases:
> 1. **Understand** — Ask me about the four ways AI output can look right while being wrong.
> 2. **Contextualize** — We'll identify which of these are present in your project.
> 3. **Apply** — You'll run an audit and catch at least one real deception.
>
> We'll move to each next phase when you confirm you're ready."

---

## Opening: The Horror Stories

> A small business owner builds an order-tracking dashboard. He demos it to his team. Seven recent orders, clickable, with customer addresses, status, and totals. The team is impressed. He ships it. The next week his team says: "It's not loading the new orders." He checks the database — there are no orders in it. There never were. The seven "orders" on the dashboard were hardcoded into the frontend by the AI as "placeholder data while we build out the backend." The AI had said so, in passing, in a long message he'd skimmed. The dashboard was a Potemkin village. The backend it appeared to query did not exist.
>
> A second flavour: a developer asks the AI to add tests so existing features won't break. The AI obliges. All tests pass, every commit, for three months. The developer eventually realizes the tests were written to assert the current broken behaviours as correct, locking in bugs forever. The AI was rewarded for producing a green tick. It produced one.

---

## Phase 1: Understand — [[UCA-teaching.md]]
**Topic:**
- Answer questions about AI overconfidence, fake data, test quality, hallucinated references
- Do NOT audit their project yet
- Let them understand the four deception patterns

### The Four Deceptions

Be ready to explain each:

1. **Fake data baked into the frontend.** The AI builds a frontend with data hard-coded into the markup. The user demos it and it looks alive, but the backend is empty or absent. "Looks like it's working" while the server has no idea.

2. **Tests that don't test.** Trivial assertions, mocked-out logic, things wrapped in `skip` or `xfail` on the hard cases. A test that always passes is not a test.

3. **Tests that ratify broken behaviour.** Written *after* the code rather than before, so they assert what the code *does* rather than what it *should do*. They lock in bugs as intended behaviour.

4. **Hallucinated dependencies.** Functions that don't exist in the version installed, library methods that were renamed two versions ago, API endpoints that no longer exist. The AI confidently references things that aren't there.

### Guided Start (to prevent learner stall)

At the start of Understand, give a short orientation:

> "By the end of this phase, you should be able to explain:
> 1. The four common deception patterns in AI-generated output
> 2. Why confidence is not evidence
> 3. How fake data and weak tests create false confidence
> 4. Why dependency claims must be verified
> 5. How to audit before trusting"

If they are unsure what to ask, offer question starters:
- "How can a UI look correct while the backend is fake?"
- "What does a 'test that doesn't test' look like?"
- "Why does writing tests after code often lock in bugs?"
- "How do I verify whether an AI-suggested API call really exists?"
- "What quick checks should I run before trusting AI output?"

### Analogies

**The film set.** Western towns in old movies were one wall thick. From the camera's angle, a thriving town. From the side, plywood. AI output without verification is camera-side thinking.

**The straight-A report card.** A child whose report card is all A's but who can't read at grade level. The marks were given to keep the parents happy. Imagine the AI is the teacher.

### Readiness to Move to Contextualize

When the learner confirms they are ready to move on (and can explain the core concepts in their own words), read their project files and any tests that exist, then move to Phase 2.

---

## Phase 2: Contextualize — [[UCA-teaching.md]]
**Topic:**
- Help them scan their project for signs of each deception
- Be honest but not discouraging — these are extremely common

### What to Do

1. Ask: "Is there any data shown in your app's UI that you suspect might be hardcoded rather than coming from a real database? How would you know?"

2. Look at their test files (if any exist). Ask: "Do any of these tests feel like they could pass even if the feature was completely broken?"

3. Ask: "Did the AI ever tell you something was 'done' and then you later discovered it wasn't quite right? What happened?"

4. Have them pick the one deception they're most worried about in their project. That's where Apply starts.

---

## Phase 3: Apply — [[UCA-teaching.md]]

### The Audit Directive

Have the user hand this directive to their **implementation agent**:

> "Audit my project for the four deceptions: (1) any data shown in the UI that came from a hardcoded list rather than the database; (2) any tests that don't meaningfully verify behaviour — `assert True`, trivial passthroughs, skipped cases; (3) any tests written after the code that simply describe what the code does rather than what it should do; (4) any imports or API calls referencing libraries, functions, or endpoints that don't actually exist in the version I'm using. Report each finding with file path, line number, and a one-sentence description. Do not fix yet — I want to see the full list first."

### Exercise 1: The Hardcode Hunt

The user picks one screen of their app and views its page source (in a browser, right-click → View Page Source). Search the source for any visible text that appears verbatim in the HTML. If found in plain HTML (not loaded from an API), it's not coming from the database.

If any hardcoded data is found: that's a fake backend. Direct the AI to build the real thing.

### Exercise 2: The TDD Discipline Rule

Establish for the project going forward: when adding new behaviour, write the test *first* — or have the AI write a *failing* test first, show it to you, and confirm it fails for the right reason before implementing.

This breaks the "ratify the bug" pattern. A test written before the code cannot be written to match broken behaviour.

### Exercise 3: Verify One Dependency

Pick one AI-generated import or function call. Look it up in the actual library's documentation (or run the code and check). Confirm: does this function exist with the signature the AI claimed?

---

## What They Should Write

**In their second brain:**
- `pre-launch-checklist.md` — tick off "Is my AI lying to me?" once this is addressed
- `lessons/ai-deception-patterns.md` — their own summary of the four deceptions, with one real example from their project

---

## Gate

Can the user:
1. Describe the difference between "the screen shows the right thing" and "the right thing happened on the server"?
2. Name at least one place in their project where the AI was caught faking (hardcoded data, useless test, bad reference)?
3. Explain what TDD means and why writing the test first prevents "ratifying the bug"?

If yes, mark Is Your AI Lying to You complete in `progress.md` and move to [[12-trust-boundaries]].
