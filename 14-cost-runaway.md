# Cost Runaway & Abuse Protection

> **Purpose:** Deliver a short (~45 minute) pre-launch briefing on spend runaway and abuse—caps, rate limits, bot risk—with practical exercises (not a phased UCA lesson).

---

## Stage Start

Announce to the user:

> "Welcome to Cost Runaway & Abuse Protection. This is the shortest lesson in the production-readiness arc but possibly the one with the most immediate financial stakes. Let's talk about what happens when your app becomes too popular, or when someone tries to use it as a weapon against your wallet."

### Guided Start (to prevent learner stall)

At the start of the lesson, give a short orientation:

> "By the end of this lesson, you should be able to:
> 1. Explain hard caps, rate limits, and quotas
> 2. Estimate your one-day maximum financial exposure
> 3. Define limits for expensive endpoints
> 4. Set alert thresholds and document a shutdown plan"

If they are unsure how to begin, offer question starters:
- "What is the difference between a spend cap and a rate limit?"
- "Which endpoint in your app could become most expensive under abuse?"
- "What one-day loss would be unacceptable for your budget?"
- "What would you disable first if you hit a 100% spend alert?"

---

## Opening: The Horror Stories

> A solo developer launched a hobby AI image generator on a Saturday. Free to use, no auth, "just for fun." A meme account on Twitter posted a link. By Sunday morning the app had served 200,000 image requests. The OpenAI bill was $11,800. The host's bandwidth bill was another $2,400. He had no spend cap on either service. He discovered Monday morning. He didn't sleep that night.
>
> Another variant: a small SaaS app with a "send invitation email" button. Free tier, no rate limit. A bored teenager wrote a script that hit the button 800,000 times in an hour. The email provider charged for every send. The owner discovered when the email provider's fraud team called.
>
> Free tiers, in particular, are honeypots for abuse. Anything that costs *you* money but is free for the user invites bot abuse the moment a search engine or a Twitter post finds it.

---

## The Gap

The user thinks "I'm a small project, no one's going to attack me." Bots don't care if you're small. They scrape and abuse every public endpoint they find, indiscriminately.

---

## The Mastery: Three Layers of Cost Protection

Teach these three layers and why all three are needed:

1. **Hard spend caps.** On every paid provider — LLM API, hosting, database, email, SMS. These are dashboard settings on the provider, not code. They are the non-negotiable outer fence. When reached, the service stops (or alerts you). You can't spend past them.

2. **Rate limiting.** Per-IP, per-user, per-endpoint. Prevents one client from dominating. Throttles out 99% of casual abuse.

3. **Quotas.** Per-user limits on expensive operations ("5 image generations per day for free users"). So legitimate users get a fair share without a single user draining the bucket.

**Analogy:** The hard cap is the seatbelt. The rate limiter is the speed governor. The quota is the lane discipline. They're independent — each stops a different kind of accident.

---

## Phase 3: Apply

### Exercise 1: The Provider Tour

Have the user open each paid provider's dashboard and set a hard spend cap. The AI can tell them what a sensible cap is (default: 2× expected monthly cost, with email alerts at 50%, 80%, and 100%).

For each provider: where is the spend cap setting? Is there an alert email configured?

Document: `decisions/spend-caps.md` — every provider, the cap set, the alert threshold.

### The Directive

Have the user hand this directive to their **implementation agent**:

> "List every paid external service my app uses. For each, tell me: what's the unit of cost (per request, per token, per GB, per email), what's a sensible per-user-per-hour limit for my expected use, and how do I configure a hard spend cap on the provider's dashboard. Add per-IP and per-user rate limits to every endpoint that calls a paid service. Add per-user quotas to any operation that costs more than half a cent. Set up email alerts that fire when I'm at 50%, 80%, and 100% of any spend cap. Tell me: if I got the 100% alert right now, what's the fastest way to take the affected feature offline?"

### Exercise 2: The Abuse Simulation

The AI writes a small script (or pseudocode the user reads) that simulates hitting one endpoint 1,000 times in 10 seconds. The user confirms the rate limiter blocks it.

### Exercise 3: The Quota Policy Doc

Have the user write `policies/quotas.md`: per-user limits per feature, with reasoning. This document becomes the spec the AI implements against when rate limits are added.

---

## What They Should Write

**In their second brain:**
- `decisions/spend-caps.md` — every provider, cap, alert threshold
- `policies/quotas.md` — per-feature user limits
- `pre-launch-checklist.md` — tick off "Cost protection" once addressed

---

## Gate

The user can answer: *"If my app went viral overnight, what's the maximum I could lose in one day?"* — with an actual number, not "I don't know." And they can show, on a provider dashboard, the specific cap that enforces it.

If yes, mark Cost Runaway & Abuse Protection complete in `progress.md` and move to [[15-observability]].
