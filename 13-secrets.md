# Secrets & Credentials

> **Purpose:** Hunt down secrets and credentials in code, history, and config—contextualize to their repo, then audit, secure, and rehearse key rotation.
>
> **Understand:** Tutor mode. User asks about secrets, where they hide, how bots find them.
> **Contextualize:** Coach mode. Find every secret in THEIR project — in code, history, and anywhere else.
> **Apply:** Coach mode. Audit directive + rotation rehearsal.

---

## Stage Start

Announce to the user:

> "Welcome to Secrets & Credentials. This is the lesson about things that, if exposed, can cost you real money or destroy your project overnight.
>
> Three phases:
> 1. **Understand** — Ask me about secrets: what they are, why they get exposed, what bots do when they find one.
> 2. **Contextualize** — We'll find every secret in your project.
> 3. **Apply** — You'll audit, secure, and rehearse a rotation.
>
> We'll move to each next phase when you confirm you're ready."

---

## Opening: The Horror Stories

> A developer committed an AWS access key to a public GitHub repo by accident. He noticed within 90 seconds and force-pushed to remove it. Too late. Bots scrape every public commit on GitHub continuously, and within 60 seconds of the push, automated scanners had grabbed his key. By the time he removed the commit, his AWS account had been used to spin up 200 of the most expensive GPU instances available. The bill was $48,000 by end of day. AWS forgave most of it — but he'd permanently sold his weekend.
>
> A second case: a vibe coder pasted his OpenAI key directly into a frontend JavaScript file. He thought "no one will look at that." Within a week, his key had been harvested by a key-sniffer extension that scrapes browser-loaded JavaScript. He discovered when his monthly bill was $1,800 instead of $20.
>
> Most damning: a 2026 study found that AI-assisted commits expose secrets at *twice* the rate of human-written commits — 3.2% vs. 1.5%. The AI is biased toward "make it work now" and will paste a key inline rather than refusing and asking for env-var setup.

---

## Phase 1: Understand

### Tutor Mode Instructions for You (the AI)

Follow **Phase 1: Understand (tutor mode)** in [[UCA-teaching.md]].

**Topic guardrails for this stage:**
- Answer questions about secrets, environment variables, git history, frontend bundles
- Do NOT audit their project yet
- Let them understand the threat model

### Key Concepts They Should Explore

- **What a secret is** — API keys, database passwords, tokens, JWT signing keys, webhook secrets, encryption keys — anything that grants access to a service or system
- **Why secrets in code are dangerous** — bots scrape every public repo, every public CDN-hosted JS file, every misconfigured S3 bucket, continuously. "No one will look" is always wrong.
- **Why git history is permanent** — deleting a file doesn't delete its history. A secret committed to git is still readable in the history unless the history is explicitly rewritten — and even then, if the repo was ever public, bots already have it.
- **Why frontend secrets are especially bad** — everything in a browser-loaded JavaScript file is public. There is no "hidden" in the frontend.
- **The three rules:**
  1. Secrets never live in code. Not in source files, not in HTML, not in frontend JavaScript, not in commit history.
  2. Secrets live in environment variables — set on the deployment platform, loaded at runtime, different per environment.
  3. If a secret leaks, rotate immediately. Don't try to "delete" it — assume it's already harvested. Generate a new one and revoke the old one today.
- **Where AI hides secrets sloppily** — hardcoded defaults, comments like `# TODO: move to env`, frontend bundles, log lines, error messages, test fixtures, README examples

### Guided Start (to prevent learner stall)

At the start of Understand, give a short orientation:

> "By the end of this phase, you should be able to explain:
> 1. What counts as a secret
> 2. Why secrets in code and frontend bundles are dangerous
> 3. Why git history leaks are persistent
> 4. Why environment variables are the default pattern
> 5. Why rotation is required after exposure"

If they are unsure what to ask, offer question starters:
- "What are common places secrets accidentally appear?"
- "Why is deleting a leaked secret from a file not enough?"
- "Why is any secret in frontend JavaScript automatically public?"
- "How should environment variables be used safely?"
- "What are the exact steps when a secret leaks?"

### Analogies

**The spare key under the doormat:** Every burglar checks under doormats. Every bot checks public GitHub. There is no clever hiding place that automated scanners haven't already learned.

**The bank PIN written on the card:** Convenient! Until you lose the card.

### Readiness to Move to Contextualize

When the learner confirms they are ready to move on (and can explain the core concepts in their own words), read their project files and check git log, then move to Phase 2.

---

## Phase 2: Contextualize

### Coach Mode Instructions for You (the AI)

Follow **Phase 2: Contextualize** in [[UCA-teaching.md]].

**Stage focus:**
- Help them identify every secret in their project
- Check both current files and git history

### What to Do

1. Ask: "What external services does your project use? Any of them require a key or token?"

2. Ask: "Do any of those keys currently appear in your code files? Would you know if they did?"

3. Ask: "If someone else could read your entire git history — all the way back to your first commit — what could they access?"

4. Suggest they scan the codebase now (using the directive below) before implementing any fixes.

---

## Phase 3: Apply

### Coach Mode Instructions for You (the AI)

Follow **Phase 3: Apply** in [[UCA-teaching.md]]: the learner hands **audit directives** below to their **implementation agent**; you interpret results with them and enforce gates.

### The Audit Directive

Have the user hand this directive to their **implementation agent**:

> "Audit every file in my project for anything that looks like a secret — API keys, passwords, tokens, connection strings, JWT signing keys, encryption keys. Also check for: secrets disguised as defaults (e.g., `API_KEY = 'sk-...' if not os.environ.get`), secrets in comments, secrets in committed test fixtures, secrets in frontend JS or HTML, secrets in error messages or log lines, and secrets in git history. For each finding: the file, the line, the secret type, and whether the value still appears in any active cloud account. Then move every legitimate secret to environment variables, ensure `.env` is in `.gitignore`, and tell me which secrets need to be rotated *today* because they've been exposed."

### Exercise 1: Frontend Bundle Inspection

Have the user open their deployed site in a browser, open developer tools (F12), go to Sources/Debugger, and search the JavaScript files for anything that looks like a key (e.g., `sk-`, `Bearer `, any long alphanumeric string). The AI explains every match.

### Exercise 2: The Rotation Rehearsal

Pick one (test or real) credential. Walk through the rotation procedure:
1. Generate a new one on the provider's dashboard
2. Update the environment variable on the hosting platform
3. Redeploy
4. Verify the app still works
5. Revoke the old credential

Time it. Write it up in `runbooks/secret-rotation.md`. The goal is to be able to do this calmly under pressure — because when a real leak happens, calm is in short supply.

---

## What They Should Write

**In their second brain:**
- `security/secrets-inventory.md` — every secret, where it lives now, whether it needs rotation
- `runbooks/secret-rotation.md` — the rotation procedure, written while calm
- `pre-launch-checklist.md` — tick off "Secrets and credentials" once addressed

---

## Gate

Can the user:
1. Open their deployed frontend and confirm there are no secrets in the JavaScript bundle?
2. Confirm `.env` is in `.gitignore` and no secrets are in git history?
3. Describe the rotation process without consulting notes?

If yes, mark Secrets & Credentials complete in `progress.md` and move to [[14-cost-runaway]].
