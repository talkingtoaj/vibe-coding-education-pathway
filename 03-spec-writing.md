# Stage 2: Spec Writing

> **Audience: AI coach.** This is the core skill of the entire course. Everything else builds on this.

---

## Teaching Goals

By the end of this stage, the user should:
- Understand that vague descriptions create vague (and often wrong) results
- Know the six parts of a good spec
- Have written a spec for their project's first feature
- Have experienced the "angry agent" review
- Understand that specs have security implications
- Be able to write a spec an AI cannot misinterpret

---

## The Central Idea

Traditional coding: you write instructions the computer follows.
Vibe coding: you describe *what you want*, the AI figures out *how to build it*.

**The problem:** The AI cannot read your mind. If your description is vague, it guesses. Its guesses are often wrong — sometimes subtly wrong (the button is on the left instead of the right), sometimes disastrously wrong (it exposes private data to everyone).

**A spec is a clear, complete description of what you want BEFORE any code is written.**

Think of it like ordering at a restaurant. "I'd like a sandwich" gets you something. "I'd like a toasted sourdough sandwich with roasted chicken, lettuce, tomato, and mustard, no mayo, cut diagonally" gets you exactly what you want. The chef (AI) still does the cooking — but they don't have to guess.

---

## The Seven Parts of a Good Spec

Teach these as a checklist. Every spec should have all seven.

### 1. The User Story
Format: "As a [type of user], I want to [action] so that [benefit]"

Example: "As a recipe app user, I want to save a new recipe so that I can find it later."

This forces clarity about WHO wants this and WHY.

### 2. What It Does
3-5 sentences in plain English. No technical terms.

Example: "When I click the 'Add Recipe' button, a form appears where I can type the recipe name, ingredients, and instructions. When I click 'Save,' the recipe is stored and I see a confirmation message."

### 3. Context and Limitations
What's the bigger picture? What constraints or realities should the AI know about before it picks an approach?

This section is incredibly helpful because the AI often has to choose between multiple valid technical approaches. Without context, it guesses — and its guess may not fit your reality.

Example:
- "This app is for my family of four. It will never have more than 10 users."
- "I need this to work offline because my internet is unreliable."
- "I'm on Windows and want to stay on Windows — no Linux solutions."
- "I don't want to pay for any services right now. Free tiers only."
- "This feature is just a prototype — it can be ugly, but it must work by Friday."

Teach the user: when the AI picks an approach that feels wrong, the missing piece was probably here.

### 4. What Data Goes In
Forms, files, user input — be specific about fields and types.

Example:
- Recipe name (text, required, max 100 characters)
- Ingredients (text, required)
- Instructions (text, required)
- Photo (image file, optional, max 5MB)

### 5. What Data Comes Out
Pages, emails, saved records, displayed information.

Example: "The saved recipe appears in my recipe list. The list shows the recipe name and a thumbnail photo. Clicking the recipe name opens the full recipe."

### 6. Acceptance Criteria
Specific, testable checks that describe "done." Include at least one **happy path** (everything goes right) and at least one **unhappy path** (something goes wrong and the app handles it gracefully).

The happy path confirms the feature works. The unhappy path confirms it fails safely.

**Happy path example:**
- "When I submit the form with all required fields filled, I see 'Recipe saved!' within 2 seconds"

**Unhappy path examples:**
- "When I submit the form without a recipe name, I see an error message 'Recipe name is required' and the recipe is NOT saved"
- "When I submit a photo larger than 5MB, I see an error message 'Photo must be smaller than 5MB'"

Teach the user: unhappy paths are where security often lives. The AI is less likely to build protection for scenarios you didn't explicitly describe.

### 7. What Could Go Wrong?
Brainstorm at least 2 ways this feature could break, be misused, or behave unexpectedly. This is where security often lives, and it's a great place to involve the AI.

**If you're not sure, ask the AI:** "What are the most likely ways this feature could go wrong or be misused?" Then pick the ones that matter for your situation and add them here.

Example:
- "What if two people submit recipes at the exact same time?"
- "What if someone tries to submit a recipe with a name that's 10,000 characters long?"
- "What if someone uploads a file that's not a photo at all, but disguised as one?"
- "What if someone tries to save a recipe while their internet is down?"

---

## Exercise: Write Their First Spec

Have the user write a spec for their project's simplest feature. If they don't have a feature yet, use: "Display a welcome message on the home page."

Guide them through all seven parts. Push them to be specific. "It should work" is not acceptance criteria. "When I click X, Y happens within Z seconds" is.

Save the spec to their vault as `project-spec.md` or a feature-specific file.

---

## The Angry Agent Exercise

After the AI implements the spec, run this counter-prompt with the user:

```
Here's my spec and what was built. Find the three most likely ways this could fail or confuse a user. For each one, explain what I should have specified to prevent it. Be ruthless — imagine you're a user who wants to break this.
```

This is critical. The user must see that even a "good" spec has gaps.

Save the angry agent's response to their vault: `security/angry-agent-[feature-name].md`

Over time, they'll see patterns in what they consistently forget. Those patterns are their personal curriculum.

---

## Security Note: Specs Are Security Boundaries

Every spec that involves data must specify WHO can see it. If the user doesn't specify access control, the AI might build something with no protection.

**Bad spec:** "Users can view recipes."
**Good spec:** "Any visitor can view public recipes. Only the recipe owner can edit or delete their own recipes. Admin users can view all recipes including private ones."

Teach the user: when a spec involves data, always ask "who can see this? who can change this?"

---

## What They Should Write

**In their vault:** `lessons/spec-writing.md`

Prompt: "Explain why a vague spec is dangerous, using a non-coding example (like ordering food, giving directions, or planning an event). Then list the seven parts of a spec in your own words, with one example from your actual project."

---

## Gate

Give the user a deliberately vague spec and ask them to improve it. Example:

> "The app should let users save notes."

They should rewrite it with all seven parts, including at least one security-relevant "what could go wrong?"

If they can do this, mark Stage 2 complete and move to Stage 3.
