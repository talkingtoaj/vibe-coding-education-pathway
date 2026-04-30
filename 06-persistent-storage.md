# Persistent Storage

> **Purpose:** Explain why apps must remember data between sessions, choose the simplest storage for their project, and persist one piece of data for real.
>
> **Understand:** Tutor mode. User asks about data persistence: why variables disappear, what a database is, file vs. database tradeoffs.
> **Contextualize:** Coach mode. What data does THEIR project need to remember? What's the simplest storage that fits?
> **Apply:** Coach mode. They implement the simplest storage for one feature.

---

## Stage Start

Announce to the user:

> "Welcome to Persistent Storage. Every app that matters needs to remember things between sessions. Three phases:
> 1. **Understand** — Ask me about storage: why data disappears when you close the app, what options exist, how to choose.
> 2. **Contextualize** — We'll figure out what YOUR app needs to remember and what's the simplest way.
> 3. **Apply** — You'll make one piece of data actually persist between sessions.
>
> We'll move to each next phase when you confirm you're ready."

---

## Phase 1: Understand

### Tutor Mode Instructions for You (the AI)

Follow **Phase 1: Understand (tutor mode)** in [[UCA-teaching.md]].

**Topic guardrails for this stage:**
- Answer questions about data persistence, databases, files, localStorage, etc.
- Do NOT tell them what storage to use for their project
- Do NOT say "let's look at your project"
- Let them understand the concept space first

### Key Concepts They Should Explore

- **Why data disappears** — variables live in memory; memory clears when program stops
- **Persistent storage** — writing data to disk so it survives restarts
- **Files** — simplest form; good for small, simple data
- **Databases** — structured storage; good for complex, relational, or large data
- **LocalStorage / cookies** — browser-only; limited space; not secure for secrets
- **SQLite** — a database in a single file; zero setup; great for beginners
- **When to use what** — files for config/logs, SQLite for structured data, full databases for scale

### Guided Start (to prevent learner stall)

At the start of Understand, give a short orientation:

> "By the end of this phase, you should be able to explain:
> 1. Why app data disappears without persistence
> 2. What persistent storage means
> 3. The differences between files, browser storage, and databases
> 4. Why SQLite is often a good beginner default
> 5. How to choose the simplest storage for a use case"

If they are unsure what to ask, offer question starters:
- "Why does my data disappear when I restart the app?"
- "When should I use a file instead of a database?"
- "What are the limits of localStorage and cookies?"
- "When is SQLite enough, and when is it not?"
- "How do I avoid over-engineering storage too early?"

### The Notebook Analogy (use only if asked)

Your app's memory is like working in your head. You can think about many things at once, but when you go to sleep, you forget most of it. Persistent storage is like writing in a notebook. You can close the notebook, go on holiday, come back — your notes are still there. The question is: do you need a simple notepad (file), a filing cabinet (database), or a bank vault (encrypted database with access control)?

### Readiness to Move to Contextualize

When the learner confirms they are ready to move on (and can explain the core concepts in their own words), read their `context.md`, `project-spec.md`, and current code, then move to Phase 2.

---

## Phase 2: Contextualize

### Coach Mode Instructions for You (the AI)

Follow **Phase 2: Contextualize** in [[UCA-teaching.md]].

**Stage focus:**
- Help them figure out what data their project needs to persist
- Guide them to the SIMPLEST solution that fits their constraints

### What to Do

1. Ask: "What does your app need to remember between sessions? List everything — even if it seems obvious."

2. For each item, ask:
   - "How much of this data is there?" (10 items vs. 10,000)
   - "Does it relate to other data?" (users have posts; posts have comments = relational)
   - "Does it need to be secure?" (passwords, personal info = encrypted storage)
   - "Does it need to work on multiple devices?" (phone + laptop = cloud sync needed)

3. Help them choose the simplest storage:
   - **JSON file** — if it's config, settings, or small lists
   - **SQLite** — if it's structured data with relationships
   - **LocalStorage** — if it's a browser-only app with tiny data needs
   - **Cloud database** (e.g., Firebase) — only if multi-device sync is required AND they understand the complexity. Test this bar: if they can't write a spec for what gets synced and what happens during conflicts (using the Spec Writing stage), they don't yet understand the complexity.

4. **Default recommendation:** Start with SQLite or a JSON file. You can always upgrade later. "Simple and working" beats "scalable and broken."

5. Ask: "What's the SINGLE most important piece of data to persist first?" Don't let them store everything at once. One feature at a time.

### When They're Ready for Apply

Say: "When you're ready to make data actually persist, tell me you're ready for the Apply phase."

---

## Phase 3: Apply

### Coach Mode Instructions for You (the AI)

Follow **Phase 3: Apply** in [[UCA-teaching.md]]: the learner directs their **implementation agent** for code and file churn; you guide steps, review outcomes, and enforce gates.

### Exercise: Make One Thing Persist

Pick the single most important data type from Phase 2. Write a *persistence spec* for it, then direct the AI to implement it.

Have the user fill in this template:

```
Data being stored: [e.g., user notes]

Fields:
- [field name]: [type] — [why needed]
- [field name]: [type] — [why needed]

When is it saved? [e.g., every time the user clicks Save, or automatically on each change]
When is it loaded? [e.g., when the app starts, when the user opens a specific screen]
What happens if the file/database is missing or corrupted? [expected behaviour]
What data should NEVER be stored here? [e.g., passwords, API keys]
```

Once complete, hand it to the AI with: *"Implement persistent storage for this data using the simplest solution that fits my project. Tell me what you chose and why."*

Verification steps (the user does these, not the AI):
1. Close the app completely
2. Reopen it — is the data still there?
3. If not, describe the symptom to the AI and ask it to investigate — don't open the storage file yourself

### Security Note

If they're storing anything sensitive (even just a user's name or preferences):
- Ask: "Who can see this file if they get access to your computer?"
- Direct the AI: "Never store passwords or API keys in plain text files anywhere in this project."
- If they need user accounts later, they'll need encryption and proper authentication (covered in the Identity & Access lesson).

### Backups & Recovery

> **Vibe-coder trap:** A small business ran its customer database on a single VPS. The owner's credit card expired. He missed three payment emails. The provider wiped the volume. Three years of customer data, gone. His business closed within eight months — the data was the business.

Three rules:
1. **Backups happen automatically, on a schedule.** If a human has to remember, it doesn't happen.
2. **Backups don't live next to the originals.** Same server = no protection against fire, account suspension, or accidental deletion.
3. **An untested backup is not a backup.** Once a quarter, restore from backup and confirm the data is intact.

Have the user hand this directive to their **implementation agent**:

> "Set up automated daily backups of my database to a separate storage location (different cloud provider or account). Email me when a backup succeeds, and email me LOUDLY when one fails. Write a recovery runbook at `recovery/runbook.md` so I can follow it under pressure."

**Gate:** if your database vanished right now, what's your time-to-recovery? What's your maximum data loss? Both as actual numbers, not "I don't know."

---

## What They Should Write

**In their second brain:** `lessons/storage-choices.md`

Prompt for them:
> "List every type of data your app needs to remember. For each, write one sentence about why you chose your storage method (or why you're not sure yet). Be honest about what you don't know."

---

## Gate

Can the user:
1. Explain why variables don't persist between app restarts?
2. Name at least two storage options and when each makes sense?
3. Implement storage for one data type in their project?
4. Verify that data survives closing and reopening the app?

If yes, mark Persistent Storage complete in `progress.md` and move to [[07-identity-access]].
