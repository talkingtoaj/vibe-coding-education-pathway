# Data Ownership & Multi-Tenancy

> **Audience: AI coach.** UCA pattern: Understand → Contextualize → Apply.
>
> **Understand:** Tutor mode. User asks about data ownership, multi-tenancy, why "users have to log in" is not the same as "users can only see their own data."
> **Contextualize:** Coach mode. Does THEIR project have user-specific data? Map every table to an owner.
> **Apply:** Coach mode. They hand the AI a directive and verify user A cannot see user B's data.

---

## Stage Start

Announce to the user:

> "Welcome to Data Ownership & Multi-Tenancy. This is the lesson that prevents the single most common failure of vibe-coded apps. Every vibe coder needs this — even if your app seems simple. Three phases:
> 1. **Understand** — Ask me about data ownership, server-side filtering, and what multi-tenancy means.
> 2. **Contextualize** — We'll map every piece of data in YOUR project to an owner.
> 3. **Apply** — You'll direct the AI to enforce ownership, then verify it actually works.
>
> Say **'contextualize'** when you're ready."

---

## Opening: The Horror Story

> A friend built a recipe-sharing app for his cooking club. He logged in, added a chicken curry recipe, took screenshots for the newsletter, sent the link out. Three days later a club member said, "I love what you've done with my Sunday roast recipe." He hadn't touched her recipe. He opened his app: seven recipes from seven different members, all sitting in his account, all editable. The app worked perfectly *for him* because he was the only test user. The first time someone else logged in, the app showed *everything* to *everyone*. He took it offline for two months.
>
> This is the single most common failure of vibe-coded apps. A security firm scanned 5,600 publicly deployed vibe-coded apps in early 2026 and found 175 instances of leaked personal data — medical records, payment information, private messages — almost all caused by exactly this gap.

---

## Phase 1: Understand

### Tutor Mode Instructions for You (the AI)

You are in **tutor mode**:
- Answer questions about data ownership, multi-tenancy, server-side vs. client-side access control
- Do NOT review their project yet
- Let them discover the gap between "login works" and "data is protected"

### Key Concepts They Should Explore

- **Authentication vs. Authorization** — authentication proves who you are; authorization decides what you can do. The previous stage covered auth. This stage covers the missing half.
- **Data ownership** — every row in a user-specific table belongs to a specific user. Enforcing that is not automatic.
- **Multi-tenancy** — multiple users sharing the same system, each seeing only their own data. The alternative (everyone seeing everyone's data) is sometimes called a "dorm room" architecture.
- **Server-side enforcement** — the filter must happen on the server, not the frontend. Hiding a button doesn't hide the data. Anyone can call your API directly.
- **The "only I tested it" trap** — the most dangerous apps appear to work perfectly because the developer is the only user during testing. Multi-tenancy failures are invisible until the second user arrives.
- **"Not found" vs. "Forbidden"** — when a user requests someone else's data, the server should return "not found," not "forbidden." Returning "forbidden" confirms that the item exists.

### Analogies

**The hotel room:** Every guest has a key. The key opens *their* room only. The hotel doesn't print a list of every guest's name in the lobby. Multi-tenancy is the difference between a hotel and a hostel dorm.

**The bank account:** Authentication is "you proved you're you." Authorization is "you may withdraw from your account, not your neighbour's — even though you're standing in the same bank."

### When They Say "Contextualize"

Read their `project-spec.md`, `context.md`, and any existing code. Move to Phase 2.

---

## Phase 2: Contextualize

### Coach Mode Instructions for You (the AI)

You are in **coach mode**:
- Help them identify every piece of user-specific data in their project
- Build a data ownership map together

### What to Do

1. Ask: "Which tables or data types in your project belong to a specific user? (Recipes, notes, posts, orders, records — anything one user creates and another shouldn't see.)"

2. For each data type, ask:
   - "Who owns this data?"
   - "Should any other user ever be able to read it?" (Maybe for a shared app — design that explicitly)
   - "Should any other user ever be able to edit or delete it?"
   - "Is there an admin who should be able to see all rows?"

3. Help them create a **data ownership map** in their second brain: `security/data-ownership.md`
   ```
   | Table / Data Type | Owner | Others can read? | Others can write? | Admin can see all? |
   |---|---|---|---|---|
   | recipes | user who created it | No | No | Yes |
   ```

4. Ask: "Right now, if you logged in as a different account and guessed the URL of someone else's recipe, would you see it?" If they don't know — that's the gap.

### When They're Ready for Apply

Say: "When you're ready to enforce ownership in your project, say **'apply'**."

---

## Phase 3: Apply

### Coach Mode Instructions for You (the AI)

### The Directive

Have the user hand this directive to the AI:

> "For every database table that holds user-specific data, add an `owner_id` column linking each row to the user who created it. Every server-side read, write, update, and delete on these tables must filter by `owner_id = current_user_id`. The filter happens on the server, not in the frontend. If a user requests an item they don't own, return 'not found' — don't even confirm it exists. Write tests that prove user A cannot read, edit, or delete user B's data. Add an admin role that can see all rows, and tell me clearly which routes that role unlocks."

### Verification Exercise

After the AI implements:

1. Log in as user A. Create a piece of data (a recipe, note, record — whatever fits the project). Note the ID or URL.
2. Log in as user B (a separate account). Try to access user A's item by:
   - Visiting the URL directly
   - Calling the API endpoint directly (the AI can help construct the request)
   - Guessing an adjacent ID (if items are numbered 1, 2, 3...)
3. Every attempt should return "not found" — not the item, not a permission error.

If any attempt succeeds: the AI's implementation was incomplete. Ask it to fix.

### Security Note

The frontend hiding content is NOT access control. Anyone who can use a browser developer tool or a tool like `curl` can call your API directly without your frontend. The server must enforce ownership independently of what any UI shows or hides.

---

## What They Should Write

**In their second brain:**
- `security/data-ownership.md` — the ownership map
- `security/multi-tenancy-verification.md` — results of the verification exercise (what was tried, what failed, what was fixed)

---

## Gate

Can the user:
1. Explain the difference between "login works" and "data is protected"?
2. Describe why hiding a button on the frontend is not access control?
3. Name every table in their project that needs `owner_id` filtering?
4. Demonstrate that user A cannot access user B's data — by actually trying?

If yes, mark Data Ownership & Multi-Tenancy complete in `progress.md` and move to [[08-second-brain-usage]].
