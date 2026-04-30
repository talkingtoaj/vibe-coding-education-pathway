# Testing

> **Purpose:** Replace "it looks right" with real verification — testing ideas in plain language, the riskiest parts of their project, then **one clear check** they ask their **implementation agent** to automate from their written spec.
>
> **Understand:** Tutor mode. They ask why poking the app by hand is not enough, what "automated checks" mean in simple terms, and the different kinds of tests.
> **Contextualize:** Coach mode. What parts of THEIR project would hurt most if they broke? What change feels scariest?
> **Apply:** Coach mode. They write a **test spec** in everyday language and have the implementation agent turn it into running checks — then they confirm those checks match what they meant.

---

## Stage Start

Announce to the user:

> "Welcome to Testing. The common mistake in vibe coding is 'it looked fine when I clicked around.' That is not proof. Three phases:
> 1. **Understand** — Ask me why checking by hand hits limits, what kinds of automated checks exist, and why 'it worked on my laptop' is a trap.
> 2. **Contextualize** — We find what part of YOUR project most deserves a safety net.
> 3. **Apply** — You describe **what must stay true** in plain words; your **implementation agent** adds the automated checks; you make sure they match your intent.
>
> We move on when you say you are ready for the next phase."

---

## Phase 1: Understand — [[UCA-teaching.md]]
**Topic:**
- Answer questions about testing and automation in **plain language**; define any technical term in one short sentence if you use it.
- Do **not** dig through their project for "things to test" yet.
- Do **not** say "now let us write a test."
- Let them see why only manual clicking is not enough for a growing app.

### Key Concepts They Should Explore

- **Why only manual testing fails** — people forget steps, skip corners, get bored, and only walk the "happy path."
- **What an automated check is** — a saved set of steps the computer runs for you, again and again, and **tells you pass or fail** so a small change cannot silently break something important.
- **Unit-style** — checks one small behavior in isolation (still described in plain words: "given this, expect that").
- **Integration-style** — checks that two parts still talk to each other correctly (for example: save then load).
- **End-to-end** — follows a path like a real user (open screen, click, see result).
- **The "it works on my machine" trap** — it ran fine once, on your device, with your habits — that is not the same as "safe for next week."
- **Regression** — something that used to work stops working after a change; good checks catch that early.

### Guided Start (to prevent learner stall)

At the start of Understand, give a short orientation:

> "By the end of this phase, you should be able to explain:
> 1. What 'testing' is trying to prove
> 2. The difference between checking by hand and having the computer re-run checks for you
> 3. What regression means
> 4. What makes a check **meaningful** (it can fail when the app is wrong) vs superficial
> 5. Why 'I tried it once and it looked fine' is weak proof"

If they are unsure what to ask, offer question starters:

- "Why does only manual testing fail in real projects?"
- "Can you explain small checks vs whole-user-path checks with a non-code example?"
- "How can a check say 'pass' while the feature is still wrong for users?"
- "What is regression, and how do saved checks help?"
- "What should I never trust when the AI says 'I tested it'?"

### The Car Analogy (use only if asked)

You buy a car. The dealer says, "I started it once, it worked, it's fine." You wouldn't accept that. You'd want to know: does it start in cold weather? Does the brake work at high speed? Does the radio turn off when you lock the doors?

Every "it works" is only one test. Automated testing is hiring a robot to run thousands of tests every time you change something, so if fixing the radio accidentally breaks the brakes, you'll know about it **before** you take your next drive.

### Readiness to Move to Contextualize

When they can explain the core ideas in their own words, read their project notes and any files that help, then move to Phase 2.

---

## Phase 2: Contextualize — [[UCA-teaching.md]]
**Topic:**
- Find what deserves a safety net first — impact, not "what is easiest to describe."
- Use **their** words for inputs, outputs, and user-visible results.

### What to Do

1. Ask: "If something broke tomorrow, what would hurt users or you the most — not look ugly, but actually matter?"

2. Ask: "What is **one small slice of behavior** you could describe as 'if this happens, that should always follow'? (Example: after I save a note, it should show up in my list. After I type nothing and hit submit, I should see a clear message.)"

3. Ask: "Have you ever changed one thing in the app and only later noticed something else stopped working?"

4. Help them pick a **first test target** — one slice that:
   - Has a clear before/after a user can see
   - Would be bad if wrong
   - Is small enough to describe on half a page

5. Discuss: "What is a **rough edge** for that slice?" (Nothing entered, twice as much as usual, weird characters, slow network — plain words, not programming theory.)

### When They're Ready for Apply

Say: "When you are ready to turn that slice into a written spec and have your implementation agent add automated checks, tell me you are ready for Apply."

---

## Phase 3: Apply — [[UCA-teaching.md]]
**Topic:** Plain language; learner verifies automated checks match their spec.

### Exercise 1: The Manual Check (to feel the pain)

Before any automation, have them **use the app like a picky user** on their chosen slice:

1. Do the normal thing. Did the result match what they said should happen?
2. Do one "rough edge" thing. What happened?
3. Ask their **implementation agent** to make **one tiny, reversible change** that should break or change that behavior (or simulate a wrong result). Try the same steps again.

Ask: "How did that feel? How many slices like this does your app have? Would you want to repeat this by hand every time something changes?"

### Exercise 2: First Automated Check (spec first)

They do **not** need to write test code by hand. They write a **test spec** — what must be verified — and hand it to their **implementation agent**.

Have them fill in:

```
Behavior slice: [short name — e.g. "Save note"]
In plain English: [what this part of the app is supposed to do for the user]

Happy path (should work):
- When: [what the user does]  →  Then: [what they should see or get]
- When: [...]  →  Then: [...]

Rough edges (should still behave well):
- When: [empty / double-click / very long text / odd characters]  →  Then: [clear message / safe result / no crash — say what you want]

Things that must NEVER happen:
- [e.g. saved data disappears silently]
- [e.g. user sees someone else's private content]
```

Then they give their **implementation agent** something like:

> "From this spec, add automated checks that fit my project. Pick the usual test setup for this codebase. Show me how to run them."

After the implementation agent adds checks, their job is to **read the names and descriptions of the checks** (and spot-check a few) so they truly match the spec — **not** only look at "all green." A check that cannot fail when the app is wrong is not doing its job.

### Exercise 3: The "Do Not Come Back" Check

Pick a bug they already fixed, or a scenario they never want to lose. Add one line to the spec: "This must stay true after future changes." Have the implementation agent add a check that would fail if the bug returned.

### Exercise 4: First Real User Observation

> **Vibe-coder trap:** A vibe coder builds an app she's proud of. Logs in, navigates straight to the right page, clicks the right button. Everything works. Hands it to her mum. Mum opens it, sits for fifteen seconds, closes the tab. "Couldn't find the button." There was a button. It was in the top right, in light grey on a white background, where she expected it. Mum didn't expect it.

Four rules for first-user observation:
1. **Don't guide them.** Hand them the URL. Watch.
2. **Watch silently.** Don't explain, suggest, or hover. The point is whether the app survives without you.
3. **Take notes on every wrong turn.** Where did they hesitate? What did they click that didn't do what they expected?
4. **Never blame the user.** If they couldn't find the button, the button is in the wrong place.

Have the user watch one real person use their app without guidance. Take notes. Bring them to the **implementation agent** with plain-language fixes where needed. Repeat with a second person if they can.

**Gate for this exercise:** the user can list three changes they made to their app based on watching someone else use it.

### Security Note

Ask: "Should your spec include bad or unexpected input — what should the app do then?" This plants the seed for later security lessons; one sentence from them is enough.

---

## What They Should Write

**In their second brain:** `lessons/testing-basics.md`

Prompt for them:
> "Explain why 'I clicked through it once and it looked fine' is not enough, using a real example from your project or life. Then describe the difference between a small automated check and a full user-path check, in plain English."

Also in the project (via the implementation agent): a `tests/` folder if the project uses one, plus the check files the agent created from their spec.

---

## Gate

Can the user:

1. Explain why only manual testing is weak for a growing project?
2. Name **one behavior slice** in their project that matters most to keep correct?
3. Produce a written spec with **at least two cases** (one happy path, one rough edge) for that slice?
4. Run the project's checks (the way the implementation agent showed) and see the result — pass or fail — and say in their own words what that result means?

If yes, mark Testing complete in `progress.md` and move to [[06-persistent-storage]].
