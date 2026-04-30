# Deployment

> **Purpose:** Get the app off the laptop—deployment concepts and constraints for their situation, then either a written deployment plan or a real deploy if they are ready.
>
> **Understand:** Tutor mode. User asks about deployment: why local isn't enough, what options exist, environment variables, HTTPS.
> **Contextualize:** Coach mode. Where does THEIR app need to live? What are their constraints?
> **Apply:** Coach mode. They document a deployment plan OR deploy if the project is ready.

---

## Stage Start

Announce to the user:

> "Welcome to Deployment. Your app works on your laptop. Now it needs to work for other people, on other devices, all the time. Three phases:
> 1. **Understand** — Ask me about deployment: why it's different from 'it works here,' what options exist, what 'production' means.
> 2. **Contextualize** — We'll figure out where YOUR app should live and what that means for your setup.
> 3. **Apply** — You'll either write a deployment plan or actually deploy if you're ready.
>
> We'll move to each next phase when you confirm you're ready."

---

## Phase 1: Understand — [[UCA-teaching.md]]
**Topic:**
- Answer questions about deployment, hosting, environment variables, HTTPS, production
- Do NOT tell them where to deploy their project
- Do NOT review their project for deployment readiness
- Let them understand the concept space

### Key Concepts They Should Explore

- **Why local isn't production** — your laptop isn't always on, doesn't have a public address, isn't secured for strangers
- **What deployment means** — moving code from your machine to a server that's always on and publicly reachable
- **Environment variables** — secrets and config that change between local and production
- **Why HTTPS matters** — encrypts data in transit; required for most modern features
- **Shared hosting vs. VPS vs. PaaS vs. serverless** — tradeoffs in control, cost, complexity
- **The "works on my machine" problem** — differences between development and production environments

### Guided Start (to prevent learner stall)

At the start of Understand, give a short orientation:

> "By the end of this phase, you should be able to explain:
> 1. Why local success is not deployment readiness
> 2. What deployment means operationally
> 3. Why environment variables and HTTPS are non-negotiable
> 4. The tradeoffs between common hosting options
> 5. How to think about deployment constraints"

If they are unsure what to ask, offer question starters:
- "What changes when an app moves from local to production?"
- "How do I compare PaaS, VPS, and serverless choices?"
- "Why must secrets be environment variables before deployment?"
- "What risks does missing HTTPS create?"
- "How do I pick a deployment target for my actual constraints?"

### The Theater Analogy (use only if asked)

Right now, their app is like a play performed in their living room for an audience of one. Deployment is building a theater, putting up a marquee, and selling tickets. The play is the same — but now anyone can attend. And the theater has different rules: fire exits, seat capacity, ushers, ticket takers. Your living room play didn't need those. Production does.

### Readiness to Move to Contextualize

When the learner confirms they are ready to move on (and can explain the core concepts in their own words), read their `context.md`, `project-spec.md`, and current project status, then move to Phase 2.

---

## Phase 2: Contextualize — [[UCA-teaching.md]]
**Topic:**
- Help them choose the right deployment path for their project and constraints
- Don't push them to deploy before they're ready

### What to Do

1. Ask: "Who needs to use this app? Just you? Your family? A team? The general public?"

2. Ask: "What's your budget for hosting? $0? A few dollars a month? Budget isn't shameful — it's a constraint like any other."

3. Ask: "Do you need this to be available 24/7, or only when you turn it on?"

4. Check `decisions/` in their second brain for any prior hosting decision from the hosting-options research. If they already chose a platform, pick up from that decision — don't re-decide. Help them execute.

   If no prior decision exists, help them choose:

   **$0 / Minimal / Personal use:**
   - GitHub Pages (static sites only)
   - Netlify / Vercel free tier (static + some dynamic)
   - Run locally + expose via tunnel (ngrok, or Cloudflare Tunnel for free zero-config option) for demos

   **Small cost / Small audience:**
   - Shared hosting (if PHP/WordPress style)
   - VPS like DigitalOcean, Hetzner (full control, more setup)
   - Platform-as-a-Service: Render, Railway, Fly.io (note: Railway offers credits; Render has a free tier)

   **Full control / Learning infrastructure:**
   - VPS + domain + SSL certificate
   - Docker containers
   - CI/CD pipelines

5. **Security discussion:**
   - "If this is public, who can access it?"
   - "Do you have any secrets in your code that need to be environment variables?"
   - "Is HTTPS required?" (Yes, for anything with user data or login)

6. **Document the decision:** `deployment/plan.md`
   - Where we're deploying
   - Why this choice
   - What's needed before we can deploy
   - Open security questions

### When They're Ready for Apply

Say: "When you're ready to make a deployment plan or actually deploy, tell me you're ready for the Apply phase."

---

## Phase 3: Apply — [[UCA-teaching.md]]

### Exercise 1: Environment Variables

Before ANY deployment, have the user hand this directive to their **implementation agent**:

> "Audit my codebase for any secrets — API keys, passwords, tokens, connection strings. For each one, move it to a `.env` file and load it from the environment instead. Confirm `.env` is in `.gitignore`. Show me what you changed and tell me which environment variables I need to set on my hosting platform."

Then have the user manually search the codebase for any obviously-looking key strings (e.g., `sk-`, `password =`, `API_KEY =`) to verify the audit was complete. Document: "In production, these variables are set on the hosting platform's settings panel, never in the code."

### Exercise 2: The Deployment Plan

Have them write `deployment/plan.md`:
```
# Deployment Plan for [Project Name]

## Target Platform
[Where and why]

## Prerequisites
- [ ] All secrets in environment variables
- [ ] .env in .gitignore
- [ ] HTTPS configured
- [ ] [Any other requirements]

## Steps
1. [Step 1]
2. [Step 2]
3. [Step 3]

## Rollback Plan
If deployment fails: [how to revert]

## Security Checklist
- [ ] No secrets in code
- [ ] HTTPS enabled
- [ ] Input validation working
- [ ] Auth configured (if needed)
```

### Exercise 3: Deploy (If Ready)

If their project is truly ready:
1. Guide them through their chosen platform's deployment process
2. Test the deployed app — does it work the same as locally?
3. Check: HTTPS? Secrets loading? Database connecting?

If NOT ready:
1. The deployment plan IS the apply exercise
2. Set a future date to revisit: "When [condition], we'll execute this plan"

---

## What They Should Write

**In their second brain:**
- `deployment/plan.md` — their deployment plan
- `deployment/security-checklist.md` — pre-deployment security review
- `lessons/deployment-concepts.md` — their explanation of why deployment matters

---

## Gate

Can the user:
1. Explain why "it works on my laptop" isn't enough for a real app?
2. Choose a deployment approach that fits their project's needs and constraints?
3. Identify all secrets in their codebase and move them to environment variables?
4. Write a deployment plan with prerequisites, steps, and rollback?
5. Explain why HTTPS is non-negotiable for anything with user data?

If yes, mark Deployment complete in `progress.md` and move to [[18-maintenance]].
