# Privacy, PII & Liability

> **Purpose:** Treat personal data as operational risk—PII map and justification, minimisation audit, privacy policy draft, and breach runbook.
>
> **Understand:** Tutor mode. User asks about PII, GDPR, data minimisation, offloading liability.
> **Contextualize:** Coach mode. Map every piece of personal data in THEIR project and ask why it's there.
> **Apply:** Coach mode. Data minimisation audit + privacy policy draft + breach runbook.

---

## Stage Start

Announce to the user:

> "Welcome to Privacy, PII & Liability — the closing lesson of the production-readiness arc. This lesson changes how you think about personal data: from 'useful information' to 'liability that lives in your house.'
>
> Three phases:
> 1. **Understand** — Ask me about PII, GDPR, data minimisation, and why the safest data is data you never collected.
> 2. **Contextualize** — We'll map every piece of personal data in your project and ask why it's there.
> 3. **Apply** — You'll run the minimisation audit, draft a privacy policy, and write a breach runbook.
>
> We'll move to each next phase when you confirm you're ready."

---

## Opening: The Horror Stories

> In late 2025, a small UK fitness app with about 4,000 users was breached. Names, emails, dates of birth, phone numbers, home addresses (collected for "delivery of free promotional t-shirts that we never actually sent"), and copies of passport photos (collected as "identity verification" though no verification ever happened) leaked publicly. The founder had no idea why he was collecting any of it; the AI had suggested the fields and he'd accepted. The Information Commissioner's Office opened an investigation. Beyond the personal humiliation: minimum fines, mandatory user notifications, a six-month forensic audit. He shut the company down rather than pay. The data was still on the internet a year later.
>
> A second case: a lifestyle app collected period-tracking data with no privacy policy and no clear data-sharing rules. After a major US legal ruling, the developers received subpoenas demanding records for individual users. They had no policy that allowed them to refuse. Every record was handed over.

---

## Phase 1: Understand — [[UCA-teaching.md]]
**Topic:**
- Answer questions about PII, GDPR (and equivalents), data minimisation, liability, third-party offloading
- Do NOT review their project yet
- Let them understand that data is a liability, not just a feature

### Key Concepts They Should Explore

- **What PII is** — personally identifiable information: name, email, phone, address, DOB, location, biometrics, government ID, financial data, health data, device fingerprints. Some are more sensitive ("radioactive") than others.
- **Data minimisation** — the principle that you should only collect data you genuinely need for the feature to work. Every extra field is a future security risk, a potential compliance obligation, and a breach-notification cost.
- **GDPR and equivalents** — if your app is reachable from the EU, UK, California, Brazil, or several other jurisdictions, local privacy law applies whether you've heard of it or not. The good news: complying with GDPR mostly means doing what you should already be doing — minimum data, clear purpose, right to delete, right to export, breach notification within 72 hours.
- **Offloading liability** — you don't have to handle passwords yourself (SSO providers do it); you don't have to handle payment cards yourself (Stripe does it); you don't have to verify identity yourself (services like Stripe Identity exist). Every category you offload is one you don't have to secure, audit, or get sued over.
- **The "just in case" trap** — the most common way apps accumulate data: "we might use this someday." AI assistants are especially prone to suggesting extra fields. Every field must earn its place.

### Guided Start (to prevent learner stall)

At the start of Understand, give a short orientation:

> "By the end of this phase, you should be able to explain:
> 1. What PII is and which categories are highly sensitive
> 2. Why data minimisation reduces risk
> 3. Why privacy obligations apply based on users, not developer intent
> 4. How offloading some data categories can reduce liability
> 5. Why every field must have a clear purpose"

If they are unsure what to ask, offer question starters:
- "What counts as PII in practice?"
- "How do I decide whether a field is required or unnecessary?"
- "What does data minimisation look like in real products?"
- "When should I offload identity or payment handling to providers?"
- "What can happen if I collect data 'just in case'?"

### Analogies

**Cleaning vs. owning:** Every item you store is something you have to clean, secure, insure, and possibly hand over. Less stuff = less work and less worry.

**The free-t-shirt sign-up:** A conference asks for your name, email, company, role, phone, and shoe size in exchange for a t-shirt. They don't need any of it. They collect because the form had fields.

**Money in the safe vs. money in the bank:** The bank takes responsibility off your hands. SSO and payment providers do the same for personal data.

### Readiness to Move to Contextualize

When the learner confirms they are ready to move on (and can explain the core concepts in their own words), read their project spec and any forms/database schemas, then move to Phase 2.

---

## Phase 2: Contextualize — [[UCA-teaching.md]]
**Topic:**
- Help them map every piece of personal data and question why it's there

### What to Do

1. Ask: "What personal information does your app currently collect or store? List it all — forms, database columns, anything."

2. For each item: "Do you genuinely *need* this for the feature to work, or is it 'just in case'?"

3. For anything in the radioactive categories (government ID, medical, financial, exact location, biometric, data about minors): "Could you offload this to a third-party provider who handles the security and compliance for you?"

4. Ask: "If all this data leaked tomorrow, what's the worst-case outcome for your users? For you?"

---

## Phase 3: Apply — [[UCA-teaching.md]]

### The Audit Directive

Have the user hand this directive to their **implementation agent**:

> "Audit every form, field, and database column in my project. For each piece of personal data, classify it: do I genuinely need it for the feature to work, or is it 'just in case'? Mark each: REQUIRED / NICE-TO-HAVE / DELETE. For everything in NICE-TO-HAVE: explain the worst case if it leaked. For anything in the radioactive categories (government ID, medical, financial, exact location, biometric, data about minors), tell me whether I could offload the responsibility to a third-party provider (Stripe, Google SSO, Auth0, etc.). Write me a plain-English privacy policy and terms-of-service draft based on what's left. Tell me which jurisdictions my app falls under and what compliance obligations come with each."

### Exercise 1: The Data Minimisation Audit

User goes field by field using the REQUIRED / NICE-TO-HAVE / DELETE framework. Produce `decisions/data-minimisation.md`: what was removed and why, what was kept and why.

### Exercise 2: The Offload Review

For every piece of radioactive PII the user must collect, find a third-party provider that handles that category. Document in `decisions/third-party-providers.md`.

### Exercise 3: The Privacy Policy Draft

The AI drafts a privacy policy and terms of service from the remaining data. The user reads them as if they were a user of the app: Are they honest? Do they describe what the app actually does? Save as `legal/privacy.md` and `legal/terms.md`. These are first drafts — if the app goes commercial, have a real lawyer review them.

### Exercise 4: The Breach Runbook

User writes `runbooks/data-breach.md`: literal steps if PII leaks. Who to notify, in what order, in what timeframe (GDPR: 72 hours from discovery). Written while calm.

---

## What They Should Write

**In their second brain:**
- `decisions/data-minimisation.md`
- `decisions/third-party-providers.md`
- `legal/privacy.md` and `legal/terms.md`
- `runbooks/data-breach.md`
- `pre-launch-checklist.md` — tick off "Privacy, PII and liability" once addressed

---

## Gate

Can the user say, for every piece of personal data their app collects, *exactly why it's being collected* and *what would happen if it leaked*? Can they describe at least one third-party provider they're using to reduce their own liability?

If yes, mark Privacy, PII & Liability complete in `progress.md`. **The production-readiness arc is complete.** Now move to [[17-deployment]].
