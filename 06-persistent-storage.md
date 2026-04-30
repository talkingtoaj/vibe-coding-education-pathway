# Persistent Storage

> **Purpose:** Explain why apps must remember data between sessions, choose the simplest storage for their project and **where it will run**, persist one piece of data for real — and surface the **cloud scratch-pad** trap so file-based data is not mistaken for durable production storage.
>
> **Understand:** Tutor mode. User asks about data persistence: why variables disappear, what a database is, file vs. database tradeoffs.
> **Contextualize:** Coach mode. What data does THEIR project need to remember? What's the simplest storage that fits?
> **Apply:** Coach mode. They implement the simplest storage for one feature (usually via their **implementation agent**), with eyes open about **where the app runs**.

---

## Stage Start

Announce to the user:

> "Welcome to Persistent Storage. Every app that matters needs to remember things between sessions. We also cover a **common online-app surprise**: data saved to a file in the cloud will usually vanish later on many hosting services, because they shut down between users and throw away any file changes.
>
> Three phases:
> 1. **Understand** — Ask me about storage: why data disappears when you close the app, what options exist, how to choose — including what changes when the app lives on the internet.
> 2. **Contextualize** — We'll figure out what YOUR app needs to remember and what's the simplest way **for where it will run** (your machine vs a cloud host).
> 3. **Apply** — You'll make one piece of data actually persist between sessions (and name what would change if you moved to the cloud).
>
> We'll move to each next phase when you confirm you're ready."

---

## Phase 1: Understand — [[UCA-teaching.md]]
**Topic:**
- Answer questions about data persistence, databases, files, localStorage, etc.
- Include the **cloud scratch-pad** idea in plain words when they ask about hosting or "it worked then disappeared."
- Do NOT tell them what storage to use for their project
- Do NOT say "let's look at your project"
- Let them understand the concept space first

### Key Concepts They Should Explore

- **Why data disappears on your machine** — while the app runs, a lot of information lives in **short-term memory** (like notes on a whiteboard). When the app closes, that whiteboard is erased unless you copied the important parts somewhere durable.
- **The cloud scratch-pad gotcha (very common for vibe coders)** — Many hosts run your app inside a **disposable container** or **temporary disk**. Saving to a **file** on that server (including **SQLite**, which is still a file on disk) can look fine in testing: users sign up, data is there. Later, after idle time, a deploy, or a restart, the platform **throws away that disk** and spins up a fresh one. Your file was never "wrong" — it lived on **scratch paper** the hotel throws out between guests. **Lesson:** for an app on the internet, durable data usually belongs in a **managed database** or **managed file/object store** the host does *not* recycle with the app — not only on the app's local disk unless the platform guarantees a **persistent volume** you deliberately attached.
- **Persistent storage (plain meaning)** — data survives closing the app, restarts, and (in production) the server being replaced.
- **Files** — simplest on a **single machine you control**; risky as the *only* copy on many cloud hosts (see gotcha above).
- **Databases** — structured storage; good for complex, relational, or large data; in production, prefer **hosted** database services when the app runs in the cloud.
- **LocalStorage / cookies** — browser-only; limited space; not secure for secrets; survives browser restarts but not "use from another device" unless you sync elsewhere.
- **SQLite** — a database in a single file; zero setup; great for beginners **on a laptop or a server with a real persistent disk**; on ephemeral cloud disks, treat it like any other file — fine for learning, **not** a silent guarantee in production unless you use a persistent volume or move to hosted storage.
- **When to use what** — match storage to **where the app runs**: local dev vs cloud; files for tiny local config; SQLite for structured data when the file truly persists; hosted DB or object storage when the cloud recycles disks.

### Guided Start (to prevent learner stall)

At the start of Understand, give a short orientation:

> "By the end of this phase, you should be able to explain:
> 1. Why app data disappears without persistence
> 2. What persistent storage means
> 3. The differences between files, browser storage, and databases
> 4. Why SQLite is often a good beginner default **on your own machine**, and what changes on many cloud hosts
> 5. How to choose the simplest storage for a use case **including where the app will run**"

If they are unsure what to ask, offer question starters:
- "Why does my data disappear when I restart the app?"
- "When should I use a file instead of a database?"
- "What are the limits of localStorage and cookies?"
- "When is SQLite enough, and when is it not?"
- "I put my app in the cloud, it worked at first, but later my data was gone — what happened?"
- "How do I avoid over-engineering storage too early?"

### The Notebook Analogy (use only if asked)

Your app's memory is like working in your head. You can think about many things at once, but when you go to sleep, you forget most of it. Persistent storage is like writing in a notebook. You can close the notebook, go on holiday, come back — your notes are still there. The question is: do you need a simple notepad (file), a filing cabinet (database), or a bank vault (encrypted database with access control)?

### The Hotel Scratch Pad (use only if asked — cloud)

On many cloud hosts, the server's local disk is like the **notepad in a hotel room**: fine for tonight, but housekeeping may **clear the room** between stays. Your app might get a **new room** after idle time or an update — and the old notepad is gone. If user data only lived on that notepad, users think you "lost" their data. Fix: keep the important notebook in the **hotel safe the building manages** (hosted database or file storage), or pay for a **locker that stays yours** (a **persistent volume** attached to the app, if the platform offers it).

### Readiness to Move to Contextualize

When the learner confirms they are ready to move on (and can explain the core concepts in their own words), read their `context.md`, `project-spec.md`, and current code, then move to Phase 2.

---

## Phase 2: Contextualize — [[UCA-teaching.md]]
**Topic:**
- Help them figure out what data their project needs to persist
- Guide them to the SIMPLEST solution that fits their constraints

### What to Do

1. Ask: "What does your app need to remember between sessions? List everything — even if it seems obvious."

2. For each item, ask:
   - "How much of this data is there?" (10 items vs. 10,000)
   - "Does it relate to other data?" (users have posts; posts have comments = relational)
   - "Does it need to be secure?" (passwords, personal info = encrypted storage)
   - "Does it need to work on multiple devices?" (phone + laptop = cloud sync needed)

3. **Where will this app mainly run?** Only on their laptop → files/SQLite on disk are simpler. On a **cloud host** (Railway, Fly, Render, Heroku-style, Cloud Run, many VPS setups with containers) → ask explicitly: "Is user data only written to the server's **local** disk?" If yes, warn about the **scratch-pad** risk and steer toward **hosted database**, **object/file storage**, or a **persistent volume** the platform documents — not "it worked yesterday" as proof.

4. Help them choose the simplest storage **for that target**:
   - **JSON file** — if it's config, settings, or small lists
   - **SQLite** — if it's structured data with relationships
   - **LocalStorage** — if it's a browser-only app with tiny data needs
   - **Cloud database** (e.g., Firebase) — only if multi-device sync is required AND they understand the complexity. Test this bar: if they can't write a spec for what gets synced and what happens during conflicts (using the Spec Writing stage), they don't yet understand the complexity.

5. **Default recommendation (local dev):** Start with SQLite or a JSON file. You can always upgrade later. "Simple and working" beats "scalable and broken."

6. **If they already deployed and "lost" data:** Name the likely cause first (ephemeral disk / new container / no volume) in plain language — *then* pick a durable option. Shame-free; this is extremely common.

7. Ask: "What's the SINGLE most important piece of data to persist first?" Don't let them store everything at once. One feature at a time.

### When They're Ready for Apply

Say: "When you're ready to make data actually persist, tell me you're ready for the Apply phase."

---

## Phase 3: Apply — [[UCA-teaching.md]]

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
Where will this app run? [e.g., only my laptop / on Cloud Platform X / other — name it]
If it runs on the internet: where will this data live **after** the host replaces the server or clears idle space? [e.g., hosted Postgres, SQLite on an attached persistent volume, S3-style object storage — or "not sure yet" so the AI can propose]
What happens if the file/database is missing or corrupted? [expected behaviour]
What data should NEVER be stored here? [e.g., passwords, API keys]
```

Once complete, hand it to their **implementation agent** with something like: *"Implement persistent storage for this data using the simplest solution that fits my project **and where it runs**. Tell me what you chose and why. If I am on a cloud host with a disposable local disk, call that out and fix it before I lose user data."*

Verification steps (the user does these, not the AI):
1. Close the app completely
2. Reopen it — is the data still there?
3. **If the app is already on a cloud host (or they use a staging deploy):** trigger a **new deploy** or wait through an idle period if their host is known to sleep instances — then check again. If data disappears, treat that as confirmation of the scratch-pad problem; have the implementation agent move durable data to **hosted** storage or a **documented persistent volume**, not only a path inside the container.
4. If something still fails, describe the symptom to the **implementation agent** and ask it to investigate — they do not need to open raw storage files themselves.

### Security Note

If they're storing anything sensitive (even just a user's name or preferences):
- Ask: "Who can see this file if they get access to your computer **or** if someone gained access to the cloud account?"
- Direct the **implementation agent**: "Never store passwords or API keys in plain text files anywhere in this project."
- If they need user accounts later, they'll need encryption and proper authentication (covered in the Identity & Access lesson).

### Vibe-coder trap: "It worked in the cloud, then everyone was gone"

> They deployed. Users signed up. Two weeks later, after quiet hours or a redeploy, **every account looked new**. Nothing "crashed" — the host simply gave them a **fresh scratch pad**. All user rows lived on **local disk inside a disposable container**. SQLite was "fine" until the disk was not.

If this already happened to them: normalize it, fix forward with **durable** storage for production, and add one line to `lessons/storage-choices.md` about what went wrong in plain words.

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
> "List every type of data your app needs to remember. For each, write one sentence about why you chose your storage method (or why you're not sure yet). If the app runs on the internet, add one sentence: where that data lives **after** the server is replaced. Be honest about what you don't know."

---

## Gate

Can the user:
1. Explain why variables don't persist between app restarts?
2. Name at least two storage options and when each makes sense — **including** why "a file on the server" is not automatically safe on many cloud hosts?
3. Implement storage for one data type in their project (via their **implementation agent**)?
4. Verify that data survives closing and reopening the app **on their current setup**?
5. (If the app runs or will run on the internet) Say in plain words **where** user data will survive after an idle period or redeploy — or honestly say "I don't know yet" and name what they will ask their implementation agent to fix next?

If yes, mark Persistent Storage complete in `progress.md` and move to [[07-identity-access]].
