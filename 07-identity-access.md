# Stage 6: Identity & Access

> **Audience: AI coach.** UCA pattern: Understand → Contextualize → Apply.
>
> **Understand:** Tutor mode. User asks about authentication, authorization, identity. Why "my app doesn't need users" is often wrong.
> **Contextualize:** Coach mode. Does THEIR project need users? Who should see what? What data is sensitive?
> **Apply:** Coach mode. They implement the simplest auth for their project, or document why it's not needed yet.

---

## Stage Start

Announce to the user:

> "Welcome to Stage 6: Identity & Access. Security starts with knowing WHO is doing WHAT. Three phases:
> 1. **Understand** — Ask me about identity and access: authentication vs. authorization, why it matters, common mistakes.
> 2. **Contextualize** — We'll figure out who YOUR app serves and what they should be allowed to do.
> 3. **Apply** — You'll either implement basic auth or document a clear security boundary.
> 
> Say **'contextualize'** when you're ready."

---

## Phase 1: Understand

### Tutor Mode Instructions for You (the AI)

You are in **tutor mode**:
- Answer questions about authentication, authorization, identity, access control
- Do NOT tell them their project needs (or doesn't need) auth yet
- Do NOT review their project
- Let them understand the security landscape first

### Key Concepts They Should Explore

- **Authentication** — proving who you are (login, password, biometrics)
- **Authorization** — deciding what you're allowed to do once identified
- **Identity** — the concept of "this user is distinct from that user"
- **Why "my app doesn't need users" might be wrong** — even single-user apps have data boundaries (my data vs. someone else's if they find your laptop)
- **Common mistakes** — storing passwords in plain text, trusting client-side validation, not validating input
- **Least privilege** — users should only be able to do what they need, nothing more

### The House Analogy (use only if asked)

Authentication is your house key. It proves you're supposed to be here. Authorization is what rooms you can enter. The babysitter has a key (authenticated) but shouldn't enter your safe (not authorized). Your teenager has a key AND can enter their own room, but not your office.

"My app doesn't need users" is like saying "I don't lock my house because I live alone." But you still lock it when you leave. And you still have a safe for valuables. The question isn't "do I have guests?" it's "what happens if someone else gets access?"

### When They Say "Contextualize"

Read their project files and `context.md`. Move to Phase 2.

---

## Phase 2: Contextualize

### Coach Mode Instructions for You (the AI)

You are in **coach mode**:
- Help them honestly assess their project's security needs
- Don't let them skip security because it's hard

### What to Do

1. Ask: "Who is your app FOR? Just you? Your family? A team? The public?"

2. Ask: "If someone else opened your app on your computer, what could they see or do? Is any of that a problem?"

3. Ask: "Does your app handle anything personal, private, or valuable? Names, contact info, financial data, health data, location?"

4. Help them decide:
   - **No auth needed yet** — single-user app, no sensitive data, only runs locally. BUT: still need `.env` for secrets, still need input validation.
   - **Simple auth** — a password to open the app, or basic username/password for a small group
   - **Full auth** — multiple users with different permissions, cloud data, public access

5. **Document the decision.** In their second brain: `security/access-decision.md`
   - What we decided
   - Why we decided it
   - What would make us change our minds
   - Date

### When They're Ready for Apply

Say: "When you're ready to implement or document your access boundary, say **'apply'**."

---

## Phase 3: Apply

### Coach Mode Instructions for You (the AI)

### Path A: No Auth Needed (Document the Boundary)

If they truly don't need auth:
1. Write `security/access-decision.md` with clear reasoning
2. List: "What WOULD trigger us adding auth?" (more users, sensitive data, cloud deployment, etc.)
3. Implement ONE security measure anyway: input validation (see below)

### Path B: Simple Password

If they need a single password to protect the app:
1. Store a hashed password (not plain text!)
2. On app start, prompt for password
3. Hash their input and compare to stored hash
4. Use a proper hashing library — don't write your own

### Path C: User Accounts

If they need multiple users:
1. Use a library or framework's built-in auth (Django auth, Firebase Auth, etc.)
2. Never store passwords in plain text
3. Never implement password reset via email until they understand the risks

### Exercise: Input Validation (Everyone Does This)

Even without auth, validate ALL input:
- "What if someone types 10,000 characters where you expected 10?"
- "What if someone types code where you expected a name?"
- "What if someone leaves a field blank that your code expects to exist?"

Have them write validation for one form/input in their project. This is security's foundation.

---

## What They Should Write

**In their second brain:**
- `security/access-decision.md` — their auth choice and reasoning
- `security/threat-model.md` — start simple: "What could go wrong?" List 3-5 realistic threats

---

## Gate

Can the user:
1. Explain the difference between authentication and authorization?
2. Make a reasoned decision about whether their app needs auth?
3. Document that decision with trigger conditions for revisiting it?
4. Implement input validation for at least one user input?

If yes, mark Stage 6 complete and move to Stage 7.
