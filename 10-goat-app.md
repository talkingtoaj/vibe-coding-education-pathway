# The Pre-Launch Checklist

> **Purpose:** Orient the learner before the production arc—walk the pre-launch checklist, set stakes, and give narrative glue for the seven technical lessons that follow (framing, not deep implementation).

---

## Stage Start

Announce to the user:

> "Welcome to the Pre-Launch Checklist — or, as I like to call it, 'I think I have the GOAT app.'
>
> By now you've built something. Maybe you've shown it to a friend. Maybe you've thought: *this is great — I'm ready to put it on the internet so other people can use it.* You might even be right. This is exciting.
>
> Hold on just a moment. Before you press the share button, there's a checklist. Most of these things you've never had to think about — because while your app lived only on your laptop, none of them mattered. The moment your app is reachable from the internet, all of them matter.
>
> We're going to walk through the checklist now, briefly. Then over the coming lessons we'll cover each item properly, with the depth it deserves.
>
> The good news: you don't have to become a security engineer or a sysadmin. You just have to know enough about each item to direct your AI competently, and to recognise when the AI has done a poor job. That's still a lot. Take a breath."

### Guided Start (to prevent learner stall)

Right after the opening, give a short orientation:

> "By the end of this lesson, you should be able to:
> 1. Name the pre-launch checklist areas that protect real users
> 2. Identify which checklist items are highest risk for your project
> 3. Explain why laptop-success is not production-readiness
> 4. Create and start using `pre-launch-checklist.md` as your operating document"

If they are unsure how to begin, offer question starters:
- "Which checklist item feels most urgent for your app right now?"
- "Which checklist item feels least clear, and why?"
- "What is one concrete failure that could happen if we skip this checklist?"
- "Which item do you already believe is covered, and what evidence do you have?"

**For the course coach:** Later lessons assume the learner keeps a separate **implementation agent** for audits and code (see `UCA-teaching.md`). This stage is framing only.

---

## The Checklist

Walk through this together. For each item, ask the user to reflect honestly: "Have you addressed this? Yes, no, or unsure?"

```
☐ 1. Is my AI lying to me?
     Are the things my app appears to do, actually happening? Or is some of it
     theatre — fake data baked into the frontend, tests that don't test, a
     frontend that lies about what the backend is doing?

☐ 2. Trust boundaries.
     Anything from outside my app — typed by users, sent to my API, uploaded
     as a file — is suspect until proven otherwise. Have I told my AI to
     treat input as hostile?

☐ 3. Secrets and credentials.
     API keys, passwords, tokens. Are any of them in my code? In my git
     history? Anywhere a stranger could find?

☐ 4. Cost protection.
     If my app got popular tomorrow, what's the maximum I could lose in a day?
     If someone with bad intentions hammered it, can they drain my budget?

☐ 5. Observability.
     When something goes wrong in production, can I see what happened? Can I
     diagnose without watching over a user's shoulder?

☐ 6. Privacy, PII, and liability.
     Am I collecting data I don't need? If it leaks, what's my exposure?
     Do I have a privacy policy? Do I need one?

☐ 7. Backups.
     If my database vanished tomorrow, how much data would I lose? How
     quickly could I be back? Have I actually tested a restore?

☐ 8. Multi-tenancy.
     Already covered. Can user A see user B's data? (Confirmed: no.)
```

---

## Horror Stories for This Moment

Choose the story most relevant to their project type and share it to give stakes:

**If they're building a social or sharing app:**
> In January 2026, an AI-assisted social network called Moltbook launched. Within three days, security researchers exposed its production database: 1.5 million API tokens, 35,000 emails, every private message between users. The cause was a single missing access check. The company folded within a week.

**If they're building something with paid APIs or services:**
> A solo developer launched a hobby AI image generator on a Saturday. Free to use, no auth, "just for fun." A meme account on Twitter posted a link. By Sunday morning, the app had served 200,000 image requests. The OpenAI bill was $11,800. The hosting bill was another $2,400. He had no spend cap on either service. He discovered Monday morning.

**If they're handling any personal information:**
> A small UK fitness app with 4,000 users was breached. The founder had no idea why he was collecting some of the data — the AI had suggested the fields and he'd accepted. Names, emails, dates of birth, phone numbers, home addresses, copies of passport photos. The UK data regulator opened an investigation. He shut the company down rather than pay.

---

## Phase 3: Apply

### Create the Pre-Launch Checklist File

Have the user save this checklist to their second brain as `pre-launch-checklist.md`. They'll return to it after each of the next seven lessons and tick items off as they're properly addressed.

The checklist file is the *spine* of the production-readiness arc — a document they own and update as they work through the lessons.

---

## Gate

Can the user:
1. Name three specific risks from the checklist they hadn't fully considered before this lesson?
2. Identify which items on the checklist their project most urgently needs?
3. Explain, in their own words, why an app that "works on their laptop" might not be safe to share?

If yes, move to [[11-is-your-ai-lying]].
