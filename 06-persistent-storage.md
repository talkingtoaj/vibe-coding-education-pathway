# Stage 5: Persistent Storage

> **Audience: AI coach.** The user needs to understand storage options well enough to say "yes, that fits" or "no, that's wrong for us." They don't need to implement the storage themselves.

---

## Teaching Goals

By the end of this stage, the user should:
- Know the three main storage options and their tradeoffs
- Understand when each is appropriate
- Be able to explain why their current project uses its current storage
- Know when they would need to migrate to something more robust
- Understand the security implications of each choice

---

## The Options

Present these as a progression, not competitors. Most projects start simple and grow.

### Option 1: JSON File (e.g., `data.json`)

**What it is:** A single text file on the computer where the app stores data in a structured format.

**Good for:**
- Prototypes and experiments
- Single-user apps
- Tiny datasets (under 1,000 records)
- Learning and testing

**Bad for:**
- Multiple users (everyone reads and writes the same file)
- Searching or sorting large amounts of data
- Relationships between data ("show me all recipes that use tomatoes")

**Security:** Anyone who can read your server files can read everything. No built-in access control, encryption, or user separation.

**Analogy:** A single notebook where you write everything. Fine for personal journaling. Chaos if ten people try to write in it at once.

---

### Option 2: SQLite File (e.g., `database.sqlite`)

**What it is:** A database engine stored in a single file. More structured and powerful than JSON.

**Good for:**
- Small to medium apps
- Structured data with relationships
- Searching, filtering, sorting
- Multiple tables that connect to each other

**Bad for:**
- Multiple servers accessing the same database simultaneously
- Very large datasets (millions of records)
- High-traffic apps

**Security:** Same file-access risks as JSON, but at least has basic concepts of users, permissions, and data integrity. Still on the local filesystem.

**Analogy:** A well-organized filing cabinet with labeled folders, cross-references, and an index. One person can use it beautifully. Ten people in different buildings can't share the same cabinet.

---

### Option 3: Cloud-Hosted Database (e.g., PostgreSQL on Supabase, Neon, Railway)

**What it is:** A professional database running on someone else's server, accessible over the internet.

**Good for:**
- Multi-user apps
- Apps that need to scale
- Team projects
- Production applications

**Bad for:**
- Simple prototypes (overkill)
- Tight budgets (usually costs money, though many have free tiers)
- Situations where you can't trust a third party with your data

**Security:** Built-in user management, encryption, backups, access logging. But you're trusting a third-party company. If they have a breach, your data is exposed.

**Analogy:** A bank safety deposit box. Professional security, accessible from anywhere, but you pay for it and you trust the bank.

---

### Option 4: In-Memory / No Persistence

**What it is:** Data stored only in the computer's RAM. When the app restarts, everything is gone.

**Good for:** Nothing that matters.

**Bad for:** Everything real.

**Analogy:** Writing notes on a whiteboard and erasing them every time you leave the room.

---

## Exercise: The Migration Scenario

Ask the user: "Pretend your app went viral and now has 10,000 active users. What breaks with your current storage? What would we migrate to?"

Have the AI explain the migration path. The user doesn't need to DO it — they need to know the path EXISTS and what it would involve.

**Key insight:** Choosing a storage option isn't about picking the "best" one. It's about picking the one that fits your current reality while knowing what comes next.

---

## Security Note: Data Location = Risk Location

Teach the user: **where your data lives determines who can steal it.**

- JSON file on your laptop? Only someone with your laptop can steal it.
- SQLite on a shared server? Anyone with server access can read it.
- Cloud database? The cloud provider's security team, plus anyone who breaches them.

For every piece of data their app stores, ask: "If someone unauthorized accessed this storage, what would they see? How bad would that be?"

---

## What They Should Write

**In their second brain:** `decisions/why-we-use-[storage-type].md`

Prompt: "Which storage does my project currently use? Why did we choose it? Under what conditions would we need to change? What data do we store, and what would happen if someone unauthorized accessed it?"

**Also:** `lessons/persistent-storage.md` — summary of the three options in their own words.

---

## Gate

Can the user:
1. Name the three storage options and one pro/con for each?
2. Explain why their project uses its current storage?
3. Describe what would trigger a migration to something more robust?
4. Identify what data their app stores and what the risk is if exposed?

If yes, mark Stage 5 complete and move to Stage 6.
