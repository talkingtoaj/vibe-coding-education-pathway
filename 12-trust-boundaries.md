# Trust Boundaries

> **Purpose:** Teach trust boundaries for everything that enters the app—injection and XSS concepts, mapping their input surfaces, then audit plus self-attack drill.
>
> **Understand:** Tutor mode. User asks about injection attacks, XSS, input validation, sanitization, authorization.
> **Contextualize:** Coach mode. Map every input entry point in THEIR project.
> **Apply:** Coach mode. They hand the AI an audit directive, then run the attack drill.

---

## Stage Start

Announce to the user:

> "Welcome to Trust Boundaries — the first of two advanced security lessons. This one is about what happens to data that comes *into* your app from the outside world.
>
> Three phases:
> 1. **Understand** — Ask me about injection, XSS, file uploads, and why "the user probably won't do that" is not security.
> 2. **Contextualize** — We'll map every place data enters YOUR app.
> 3. **Apply** — You'll direct the AI to audit and fix your input handling, then try to break it yourself.
>
> We'll move to each next phase when you confirm you're ready."

---

## Opening: The Horror Story

> In 1998 a security researcher popularised the joke about a student named `Robert'); DROP TABLE Students;--`. He's not real, but the attack is. A school's grade-tracking app had a "student name" field. A student typed that exact string. The app concatenated it directly into a SQL query. The query dropped the entire students table. Six months of grades, gone.
>
> Twenty-eight years later, AI models trained on pre-2010 code patterns still generate string-concatenated SQL by default. In one 2026 audit, 86% of AI-generated code samples were vulnerable to cross-site scripting, and 88% to log injection.
>
> A more recent variant: an indie app accepted profile pictures. The AI implemented "upload an image" by saving any file with an image-looking extension to the server. A user uploaded `evil.php.jpg`. The webserver, configured to execute PHP files, ran it. The user now had a remote shell on the server.

---

## Phase 1: Understand — [[UCA-teaching.md]]
**Topic:**
- Answer questions about injection, XSS, file upload vulnerabilities, IDOR, input validation
- Do NOT review their project yet
- Let them understand why every input is suspect

### Key Concepts They Should Explore

- **Why every input is suspect** — the user's mental model is "what the form expected." The actual input is "anything an attacker can send to the same endpoint, in any encoding, of any size, with any filename, with any content."
- **SQL injection** — inserting SQL fragments into text fields to manipulate database queries. Prevented by parameterized queries — never build SQL by string concatenation.
- **Cross-site scripting (XSS)** — inserting HTML/JavaScript into text fields so it executes in another user's browser. Prevented by HTML-escaping output.
- **File upload abuse** — uploading executable files disguised as images or documents.
- **IDOR (Insecure Direct Object Reference)** — accessing someone else's resource by guessing its ID in a URL. Prevented by combining multi-tenancy filtering with input validation (already covered).
- **The three jobs:** Every input must pass through all three in order:
  1. **Validate** — does this match what I expected? (type, length, allowed values, charset, file size, file format)
  2. **Sanitize** — strip or escape anything that could be interpreted as code
  3. **Authorize** — even if valid and clean, is *this user* allowed to do *this thing* with *this data*?

### Guided Start (to prevent learner stall)

At the start of Understand, give a short orientation:

> "By the end of this phase, you should be able to explain:
> 1. Why all incoming input is untrusted
> 2. The basic idea of SQL injection and XSS
> 3. Why upload handling is a security boundary
> 4. The validate → sanitize → authorize sequence
> 5. Why frontend checks alone do not secure an app"

If they are unsure what to ask, offer question starters:
- "Why is all input considered hostile by default?"
- "What's a simple explanation of SQL injection and XSS?"
- "Why can file uploads be dangerous even when file extensions look safe?"
- "How are validate, sanitize, and authorize different?"
- "Why isn't frontend-only validation sufficient?"

### Analogies

**Airport security:** Even ticketed passengers walk through scanners. The ticket (authentication) doesn't get you out of screening (validation, sanitization).

**The bouncer:** Three jobs — check the ID (validation), check the guest list (authorization), pat down for weapons (sanitization). A bouncer doing only one is not security.

### Readiness to Move to Contextualize

When the learner confirms they are ready to move on (and can explain the core concepts in their own words), read their project files and move to Phase 2.

---

## Phase 2: Contextualize — [[UCA-teaching.md]]
**Topic:**
- Help them list every place data enters their app
- Connect each input to the three jobs it needs to pass

### What to Do

1. Ask: "Where does data come INTO your app? Think broadly — forms, URL parameters, file uploads, API calls, cookies, anything the user can type or send."

2. For each entry point, ask:
   - "What do you validate for this input currently?"
   - "What would happen if someone typed 10,000 characters here?"
   - "What would happen if someone typed HTML or JavaScript?"
   - "What would happen if someone uploaded a file with a deceptive extension?"

3. Help them build an **input inventory** in `security/input-inventory.md`:
   ```
   | Entry Point | Validates? | Sanitizes? | Authorizes? | Risk level |
   |---|---|---|---|---|
   | name field | length only | no | no | medium |
   | file upload | extension only | no | no | HIGH |
   ```

4. Ask: "Which of these looks scariest to you?"

---

## Phase 3: Apply — [[UCA-teaching.md]]

### The Audit Directive

Have the user hand this directive to their **implementation agent**:

> "List every place data enters my app from outside: forms, URL/query parameters, file uploads, headers, cookies, third-party webhooks, OAuth callbacks. For each, tell me three things: what validation is in place, what sanitization is in place, what authorization check is in place. Then play attacker: assume someone wants to break each input. What can they do? Specifically check for: SQL injection, cross-site scripting, file-upload exploits, mass assignment, path traversal. Use parameterized queries everywhere — never construct SQL by string concatenation. Report findings ordered by severity."

### Exercise 1: The Attack Drill

For ONE form in their project, the user systematically tries:
- A very long string (10,000 characters)
- HTML tags: `<b>bold</b>`
- A script tag: `<script>alert('xss')</script>`
- SQL fragment: `' OR '1'='1`
- Empty input where something is expected
- A `.php` or `.exe` file renamed to `.jpg` (for file uploads)

For each: what does the app do? The AI fixes each failure as it's discovered.

### Exercise 2: The IDOR Hunt

Log in as account A. Copy a URL or API endpoint that contains a numeric ID. Log in as account B. Paste the URL. If you see A's data — that's an IDOR failure. Direct the AI to add both server-side ownership filtering (from the multi-tenancy lesson) and input validation.

### Security Note

Inputs aren't only forms. Data read back from the database was written by someone at some point — that someone might have been malicious. Treat database content as untrusted when displaying it in HTML.

---

## What They Should Write

**In their second brain:**
- `security/input-inventory.md` — their input map with validation status
- `pre-launch-checklist.md` — tick off "Trust boundaries" once addressed

---

## Gate

Can the user:
1. Name three categories of attack their app was vulnerable to before this lesson?
2. Describe what "parameterised query" means without mentioning syntax?
3. Describe the three jobs every input must pass through?

If yes, mark Trust Boundaries complete in `progress.md` and move to [[13-secrets]].
