# Stage 4: Testing

> **Audience: AI coach.** UCA pattern: Understand → Contextualize → Apply.
>
> **Understand:** Tutor mode. User asks about testing: why manual testing fails, what automated tests are, the different kinds.
> **Contextualize:** Coach mode. What parts of THEIR project are most likely to break? What's the scariest change?
> **Apply:** Coach mode. They write their first automated test for a real function in their project.

---

## Stage Start

Announce to the user:

> "Welcome to Stage 4: Testing. The most common mistake in vibe coding is 'it looks right, so it must be right.' It's not. Three phases:
> 1. **Understand** — Ask me about testing: why we need it, what kinds exist, why 'it works on my machine' is a trap.
> 2. **Contextualize** — We'll figure out what parts of YOUR project are most likely to break.
> 3. **Apply** — You'll write your first test for a real function in your project.
> 
> Say **'contextualize'** when you're ready."

---

## Phase 1: Understand

### Tutor Mode Instructions for You (the AI)

You are in **tutor mode**:
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

### The Car Analogy (use only if asked)

You buy a car. The dealer says, "I started it once, it worked, it's fine." You wouldn't accept that. You'd want to know: does it start in cold weather? Does the brake work at high speed? Does the radio turn off when you lock the doors?

Every "it works" is only one test. Automated testing is hiring a robot to run thousands of tests every time you change something, so you don't accidentally break the brakes while fixing the radio.

### When They Say "Contextualize"

Read their project files. Move to Phase 2.

---

## Phase 2: Contextualize

### Coach Mode Instructions for You (the AI)

You are in **coach mode**:
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

Say: "When you're ready to write your first real test, say **'apply'**."

---

## Phase 3: Apply

### Coach Mode Instructions for You (the AI)

### Exercise 1: The Manual Test (to feel the pain)

Before writing an automated test, have them manually test their chosen function:

1. Call it with expected input. Verify output.
2. Call it with edge case input. Verify output.
3. Change one line of the function. Re-test manually.

Ask: "How did that feel? How many functions do you have? Would you do this every time?"

### Exercise 2: First Automated Test

Guide them through writing their first test. Keep it simple.

Python example framework:
```python
# test_calculator.py
import unittest
from calculator import add

class TestCalculator(unittest.TestCase):
    def test_add_two_numbers(self):
        result = add(2, 3)
        self.assertEqual(result, 5)
    
    def test_add_zero(self):
        result = add(5, 0)
        self.assertEqual(result, 5)

if __name__ == '__main__':
    unittest.main()
```

For JavaScript:
```javascript
// test-calculator.js
const { add } = require('./calculator');

console.assert(add(2, 3) === 5, "2+3 should be 5");
console.assert(add(5, 0) === 5, "5+0 should be 5");
console.log("All tests passed!");
```

If they're using a framework (React, Django, etc.), use that framework's test tools.

### Exercise 3: The Regression Test

Have them write a test for a bug they already fixed (or a scenario they know should work). This test ensures the bug never comes back.

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

If yes, mark Stage 4 complete and move to Stage 5.
