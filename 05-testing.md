# Testing

> **Purpose:** Replace "it looks right" with real verification—testing concepts, the riskiest parts of their project, then one automated test on real code.
>
> **Understand:** Tutor mode. User asks about testing: why manual testing fails, what automated tests are, the different kinds.
> **Contextualize:** Coach mode. What parts of THEIR project are most likely to break? What's the scariest change?
> **Apply:** Coach mode. They write their first automated test for a real function in their project.

---

## Stage Start

Announce to the user:

> "Welcome to Testing. The most common mistake in vibe coding is 'it looks right, so it must be right.' It's not. Three phases:
> 1. **Understand** — Ask me about testing: why we need it, what kinds exist, why 'it works on my machine' is a trap.
> 2. **Contextualize** — We'll figure out what parts of YOUR project are most likely to break.
> 3. **Apply** — You'll write your first test for a real function in your project.
>
> We'll move to each next phase when you confirm you're ready."

---

## Phase 1: Understand

### Tutor Mode Instructions for You (the AI)

Follow **Phase 1: Understand (tutor mode)** in [[UCA-teaching.md]].

**Topic guardrails for this stage:**
- Answer questions about testing, types of tests, test automation
- Do NOT review their project for testable functions yet
- Do NOT say "now let's write a test"
- Let them discover why manual testing is insufficient

### Key Concepts They Should Explore

- **Why manual testing fails** — humans forget edge cases, skip steps, get bored
- **What an automated test is** — code that runs other code and checks the result
- **Unit test** — tests one small piece in isolation
- **Integration test** — tests pieces working together
- **End-to-end test** — tests the whole flow as a user would experience it
- **The "it works on my machine" trap** — code works for you today on your laptop with your data
- **Regression** — something that used to work stops working after a change

### Guided Start (to prevent learner stall)

At the start of Understand, give a short orientation:

> "By the end of this phase, you should be able to explain:
> 1. Why manual testing is not enough
> 2. The difference between unit, integration, and end-to-end tests
> 3. What regression means
> 4. What makes a useful automated test
> 5. Why 'it works on my machine' is not proof"

If they are unsure what to ask, offer question starters:
- "Why does manual testing fail in real projects?"
- "Can you explain unit vs integration vs end-to-end with simple examples?"
- "What makes a test meaningful instead of superficial?"
- "What is regression, and how do tests catch it?"
- "How can a test pass while the feature is still broken?"

### The Car Analogy (use only if asked)

You buy a car. The dealer says, "I started it once, it worked, it's fine." You wouldn't accept that. You'd want to know: does it start in cold weather? Does the brake work at high speed? Does the radio turn off when you lock the doors?

Every "it works" is only one test. Automated testing is hiring a robot to run thousands of tests every time you change something, so you don't accidentally break the brakes while fixing the radio.

### Readiness to Move to Contextualize

When the learner confirms they are ready to move on (and can explain the core concepts in their own words), read their project files and move to Phase 2.

---

## Phase 2: Contextualize

### Coach Mode Instructions for You (the AI)

Follow **Phase 2: Contextualize** in [[UCA-teaching.md]].

**Stage focus:**
- Help them identify what parts of their project most need testing
- Connect to their actual work

### What to Do

1. Ask: "What part of your project, if it broke, would hurt the most? Not 'look bad' — actually cause problems?"

2. Ask: "What's the simplest function in your project that does something important? Something where you could say 'if I give it X, it should always give me Y'?"

3. Ask: "Have you ever made a change to your project, thought it was fine, and then later discovered something else broke?"

4. Help them identify their **first test candidate** — ideally a function that:
   - Has clear inputs and outputs
   - Is important if wrong
   - Is small enough to understand

5. Discuss: "What's an edge case for this function?" (Empty input, very large input, wrong type of input, special characters, etc.)

### When They're Ready for Apply

Say: "When you're ready to write your first real test, tell me you're ready for the Apply phase."

---

## Phase 3: Apply

### Coach Mode Instructions for You (the AI)

Follow **Phase 3: Apply** in [[UCA-teaching.md]]: the learner directs their **implementation agent** for code and file churn; you guide steps, review outcomes, and enforce gates.

### Exercise 1: The Manual Test (to feel the pain)

Before writing an automated test, have them manually test their chosen function:

1. Call it with expected input. Verify output.
2. Call it with edge case input. Verify output.
3. Change one line of the function. Re-test manually.

Ask: "How did that feel? How many functions do you have? Would you do this every time?"

### Exercise 2: First Automated Test

Rather than writing the test code yourself, you will *spec the tests* and direct the AI to implement them. The AI picks the framework; your job is to define what must be verified.

Have the user fill in a test specification for their chosen function:

```
Function: [name]
Purpose: [what it does in plain English]

Happy path:
- Input: [example]  →  Expected output: [example]
- Input: [example]  →  Expected output: [example]

Edge cases:
- Input: [empty / zero / very large / wrong type]  →  Expected: [error / graceful result]
- Input: [boundary value]  →  Expected: [explain]

Things that should NEVER happen:
- [e.g., it should never return null when given valid input]
- [e.g., it should never mutate the input]
```

Once they've written the spec, have them hand it to the AI with: *"Implement tests for this function using whatever test framework fits my project. Write failing tests first, then confirm they pass after implementation."*

After the implementation agent implements, the user's job is to *read* the tests and verify they actually exercise what the spec described — not just that they pass. A test that always passes is not a test.

### Exercise 3: The Regression Test

Have them write a test for a bug they already fixed (or a scenario they know should work). This test ensures the bug never comes back.

### Exercise 4: First Real User Observation

> **Vibe-coder trap:** A vibe coder builds an app she's proud of. Logs in, navigates straight to the right page, clicks the right button. Everything works. Hands it to her mum. Mum opens it, sits for fifteen seconds, closes the tab. "Couldn't find the button." There was a button. It was in the top right, in light grey on a white background, where she expected it. Mum didn't expect it.

Four rules for first-user observation:
1. **Don't guide them.** Hand them the URL. Watch.
2. **Watch silently.** Don't explain, suggest, or hover. The point is whether the app survives without you.
3. **Take notes on every wrong turn.** Where did they hesitate? What did they click that didn't do what they expected?
4. **Never blame the user.** If they couldn't find the button, the button is in the wrong place.

Have the user watch one real person use their app without guidance. Take notes. Bring them to the AI and decide which problems are app problems. Apply changes. Repeat with a second person.

**Gate for this exercise:** the user can list three changes they made to their app based on watching someone else use it.

### Security Note

Ask: "Should your tests include cases for bad input? What happens if someone passes the wrong thing?" This is the seed of security testing.

---

## What They Should Write

**In their second brain:** `lessons/testing-basics.md`

Prompt for them:
> "Explain why 'I tested it manually and it worked' is not enough, using a real example from your project or life. Then describe the difference between a unit test and an end-to-end test in plain English."

Also:
- `tests/` folder in their project (if it doesn't exist)
- Their actual test files

---

## Gate

Can the user:
1. Explain why manual testing is insufficient for a growing project?
2. Identify the most important function in their project to test?
3. Write at least two test cases (one happy path, one edge case) for that function?
4. Run their tests and see them pass?

If yes, mark Testing complete in `progress.md` and move to [[06-persistent-storage]].
