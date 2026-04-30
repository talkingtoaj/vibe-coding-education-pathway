# Vibe Coding — Zero to Hero

> A free, self-paced course for non-coders who want to ship software by directing AI.

This isn't watching tutorials. It's learning by doing, with your real project as the curriculum.

Every stage follows the **UCA pattern**: **Understand** → **Contextualize** → **Apply** (see `UCA-teaching.md` in the repo for the full model).
- **Understand:** You ask questions until the concept is clear (**course coach** in tutor mode)
- **Contextualize:** We connect it to your actual project (coach mode)
- **Apply:** You drive the work hands-on — usually by **directing a separate implementation AI** to change code while you review, decide, and capture notes (coach mode for learning; builder AI for typing code)


---

## What is Vibe Coding?

Vibe coding means building software by describing what you want in plain English and having an AI assistant write the actual code. You don't learn Python, JavaScript, or any programming language. You learn how to **think clearly about problems**, **describe them precisely**, and **catch when the machine misunderstands you.**

Think of it like directing a film. You don't operate the camera — but you absolutely must know what shot you need and whether the footage is right.

## What You'll Learn

**Foundations:**
- **Git & safety** — never lose work, always be able to undo
- **Specification-driven development** — write clear descriptions before any code exists
- **Comprehension debt** — notice fuzzy spots in how your app behaves; shrink them with plain stories and simple diagrams, not by reading every line of code
- **Testing** — prove things work, even when you didn't write the code
- **Persistent storage** — where data lives and why it matters
- **Identity & access** — authentication, authorization, and why they're different
- **Data ownership & multi-tenancy** — so user A cannot see or edit user B's data
- **Your second brain** — a shared memory system between you and your AI
- **AI skills** — teach your AI reusable superpowers: brainstorming, reflection, pattern drift prevention

**Production readiness:**
- **The pre-launch checklist** — eight things that only matter once real people use your app
- **Is your AI lying to you?** — hardcoded data, useless tests, hallucinated dependencies
- **Trust boundaries** — why every input must be validated, sanitized, and authorized
- **Secrets & credentials** — why bots harvest exposed API keys within 60 seconds
- **Cost runaway & abuse protection** — hard caps, rate limits, quotas
- **Observability** — logs, error tracking, and the "tell me what happened" workflow
- **Privacy, PII & liability** — data you don't collect can't leak

**Closing:**
- **Deployment** — getting your app in front of the world
- **Sustainable maintenance** — keeping your project healthy over time, and knowing when to stop

## What You Need

1. **An AI coding assistant** — we recommend [Claude Desktop](https://claude.ai/download) (free tier). It runs on your own computer, works offline, and handles long conversations well. Cursor, GitHub Copilot, or similar tools are fine too.

2. **A computer** — Windows, Mac, or Linux. 

3. **Curiosity** — and a real problem or project you want to solve.

That's it. No coding knowledge required.

## How to Start

Copy and paste this exact prompt into an AI assistant of your choosing:

```
I want to begin the Vibe Coding Education Pathway for non-coders.

Course repo:
https://github.com/talkingtoaj/vibe-coding-education-pathway

Start here:
https://github.com/talkingtoaj/vibe-coding-education-pathway/blob/main/bootstrap.md

Raw file:
https://raw.githubusercontent.com/talkingtoaj/vibe-coding-education-pathway/main/bootstrap.md

Please start with bootstrap.md and follow it exactly. If you cannot open the raw URL directly, use the GitHub repo link or web search for "talkingtoaj vibe-coding-education-pathway bootstrap.md".

Walk me through the course step by step. Do not skip the file persistence check.
```

### What Happens Next

The AI will guide you through this sequence:

1. **Can we save files?** — The AI tests whether it can write files on your system. If not, it'll guide you to install a local AI assistant (like Claude Desktop) that can. This is essential — the entire course depends on a shared memory system.

2. **Second brain setup** — You pick a note-taking app (we'll explore options together), set it up as a shared workspace between you and the AI, and the AI populates it with your course progress tracker, project notes, and lesson summaries.

3. **Recovery setup** — Now that your second brain exists, the AI sets up a way for you to resume instantly after any interruption: a persistent system instruction, a custom command, or a Desktop paste-file — all pointing to a single resume script.

4. **Interview** — The AI asks about your background, goals, and available time, then helps you pick a real project to build. Your answers are saved directly to your second brain.

5. **Begin learning** — You start with Git (your "save game" system) and progress through each stage at your own pace.

The AI will read the course material and guide you through everything.

---

## About This Course

This course is entirely free and self-paced. There's no timeline, no homework deadlines, and no grades. You progress when you're ready. You will typically use **two different AI setups**: a **course coach** that follows `AGENTS.md` + `UCA-teaching.md` (teaching, pacing, safety), and an **implementation agent** in another chat or profile that you point at your repo to write code from your specs. Same course material; two roles so “don’t do my homework for me” and “AI writes the code” stay in balance.

All course content is open source. If you find a bug, have a suggestion, or want to contribute an improvement, contributions are welcome.

**Built on:** Specification Driven Development, Comprehension Debt, and the philosophy that in the age of AI, coding is a management skill — not a craft skill.
