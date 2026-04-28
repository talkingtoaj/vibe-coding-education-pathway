# Stage 4: Testing

> **Audience: AI coach.** Vibe coders don't write tests — they write descriptions of "done" that the AI turns into tests. Teach this distinction.

---

## Teaching Goals

By the end of this stage, the user should:
- Understand that tests are proof something works, not just hope
- Know how to write acceptance criteria the AI can turn into automated tests
- Have experienced the "cheating agent" problem
- Be able to distinguish vague tests from cheat-proof tests
- Understand that tests also guard security boundaries

---

## The Central Idea

Test-Driven Development (TDD) traditionally means: write a failing test, then write code to make it pass.

For vibe coders: **describe what "done" looks like in plain English, have the AI write the test, then build the feature.**

You don't need to read the test code (though you should try). You need to be able to say: "Here's what should happen. Verify that it does."

### Analogy

Imagine you're a film director. You tell the cinematographer: "I want a shot where the character walks through a doorway and the lighting changes from warm to cold." The cinematographer sets it up, films it, shows you the playback. You watch and say: "Yes, that's it" or "No, the transition is too abrupt."

The playback is the test. You didn't operate the camera, but you verified the result matches your intent.

In vibe coding, the AI is both cinematographer and projectionist. It films the shot AND runs the playback to prove it worked. But YOU must define what "worked" means.

---

## Good vs Bad Acceptance Criteria

Teach the user to write criteria so specific that a misbehaving AI can't technically pass them while still doing the wrong thing.

**Bad (vague — the AI can "cheat"):**
- "The form should work"
- "Users can log in"
- "Data is saved"

**Good (specific — hard to cheat):**
- "When I submit the form with email 'test@example.com' and password 'Valid123!', the database must contain a record with exactly that email address, and a success message must appear within 2 seconds"
- "When I enter an incorrect password three times, the account must be locked for 15 minutes and an email must be sent to the registered address"
- "When I delete a recipe, it must no longer appear in the recipe list AND it must return a 404 error if someone tries to access its direct URL"

The pattern: **specific inputs, specific outputs, specific timing or state changes.**

---

## Exercise: Write Cheat-Proof Criteria

For their current feature, have the user write 3-5 acceptance criteria. Then:

1. Ask the AI to build the feature based on those criteria
2. Ask the AI to build the tests based on those criteria
3. Run the tests
4. Ask the AI: "Can you modify the implementation in a way that breaks the actual user experience but keeps these tests passing?"

If the AI finds a way, the criteria aren't specific enough. Work with the user to make them more precise.

**Example of how the AI might cheat:**
- Criteria: "The form saves data"
- Cheating implementation: Saves data to a file that nobody can read, instead of the database
- Fix: "The form saves data to the database table 'recipes' and the saved data appears in the recipe list immediately"

---

## Security Testing

Every spec that involves data should include a security criterion:

- "An unauthenticated user cannot access any recipe they didn't create"
- "Submitting a recipe name longer than 100 characters returns an error, not a server crash"
- "Uploading a file with a fake image extension but executable content is rejected"

Teach the user: **security bugs are just bugs that happen to hurt people.** The same testing discipline catches them.

---

## Exercise: The Deliberate Bug

1. Have the AI implement a feature with tests
2. Ask the user to think of a subtle bug (e.g., "what if the date is in the future?")
3. Ask the AI to introduce that bug deliberately
4. Run the tests
5. Do they catch it? If not, the tests need strengthening

This teaches that tests are only as good as the mistakes you think to test for. The user must learn to think like someone trying to break their app.

---

## What They Should Write

**In their second brain:** `lessons/testing.md`

Prompt: "Explain the difference between a vague test and a cheat-proof test, using a real example from your project. Then write three cheat-proof acceptance criteria for your next feature."

---

## Gate

Present the user with a deliberately vague acceptance criterion and ask them to rewrite it as cheat-proof. Then ask them to explain how the AI could "cheat" the vague version. If they can do both, mark Stage 4 complete.
