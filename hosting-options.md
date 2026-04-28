# Hosting & Deployment Options

> **Audience: AI coach.** Guide the user to research current hosting solutions so they pick a platform that fits their needs and budget from day one.

---

## Why This Matters Early

The user will eventually want to share their app with others. If they pick a tech stack or architecture that their chosen hosting platform doesn't support, they'll face a painful migration later. Much better to know their destination before they start building.

**Analogy:** You wouldn't build a house without checking if the land supports it. A skyscraper needs different foundations than a cottage. Knowing your hosting platform early means you build for the right foundation.

---

## The Research Prompt

Give the user this exact prompt to paste into their AI assistant (or run it yourself if you're the AI reading this):

```
I want to deploy a simple web app built with [HTML/Python/JavaScript — whatever their project uses]. I don't know how to code but I'm learning to direct AI to build for me.

Please search for the most popular free or low-cost hosting options for beginners right now. For each option, report:
1. Name and website
2. What types of apps it supports (static sites, Python, Node.js, databases, etc.)
3. Whether it has a free tier and what the limits are
4. How you deploy to it (GitHub integration, drag-and-drop, CLI, etc.)
5. One major pro and one major con
6. Whether it requires a credit card to sign up

Focus on options that are beginner-friendly and have good free tiers. I don't want to pay anything while learning.
```

**If you're the AI reading this:** Run this research for the user. Use web search if you have it. If not, ask the user to paste this prompt into a tool that can search, or provide your current knowledge with a caveat that prices and features change.

---

## Common Options (as of 2026 — verify current details)

Here are typical options to seed the research. The AI should verify current pricing and features.

### Render (render.com)
- **Supports:** Python, Node.js, static sites, PostgreSQL
- **Free tier:** Yes — web services, background workers, PostgreSQL
- **Deploy:** Connect GitHub repo, auto-deploys on push
- **Pro:** Dead simple, generous free tier, no credit card required
- **Con:** Free tier spins down after inactivity (cold start delay)

### Railway (railway.app)
- **Supports:** Most languages, databases, Redis
- **Free tier:** Trial credits, then pay-as-you-go (can be very cheap for small apps)
- **Deploy:** GitHub integration or CLI
- **Pro:** Extremely easy, great developer experience
- **Con:** Not permanently free — costs money once trial expires

### Vercel (vercel.com)
- **Supports:** Static sites, Next.js, React, Vue, serverless functions
- **Free tier:** Yes — generous for static and frontend frameworks
- **Deploy:** GitHub integration, incredibly simple
- **Pro:** Fastest deploy experience, excellent for frontend apps
- **Con:** Best for frontend/Javascript; backend support is more limited

### Netlify (netlify.com)
- **Supports:** Static sites, JAMstack, serverless functions
- **Free tier:** Yes — generous bandwidth and build minutes
- **Deploy:** GitHub integration or drag-and-drop
- **Pro:** Simple, great for static sites and landing pages
- **Con:** Limited backend/database support on free tier

### GitHub Pages (pages.github.com)
- **Supports:** Static sites only (HTML, CSS, JavaScript)
- **Free tier:** Yes — completely free
- **Deploy:** Push to a GitHub repo
- **Pro:** Zero cost, already integrated with git
- **Con:** Static only — no backend, no database, no user accounts

### PythonAnywhere (pythonanywhere.com)
- **Supports:** Python, MySQL, static files
- **Free tier:** Yes — always-on Python app
- **Deploy:** Upload files or git clone
- **Pro:** Python-focused, doesn't sleep like Render's free tier
- **Con:** Limited to Python, less modern than other options

### Fly.io (fly.io)
- **Supports:** Docker containers — almost anything
- **Free tier:** Yes — small VMs, generous allowances
- **Deploy:** CLI (`fly deploy`)
- **Pro:** Very flexible, apps don't sleep
- **Con:** Requires CLI comfort, slightly steeper learning curve

### Supabase (supabase.com)
- **Supports:** PostgreSQL database + hosting for frontend
- **Free tier:** Yes — generous database and auth allowances
- **Deploy:** Can host frontend + backend together
- **Pro:** Database + auth + hosting in one, excellent for apps needing user accounts
- **Con:** More complex if you only need simple hosting

---

## The Decision

After research, the user should write a decision note: `decisions/why-we-chose-[platform].md`

Prompt for the user:
> "Which hosting platform did you pick and why? What type of app are you building, and why does this platform fit? What's the free tier limit you need to watch out for?"

**Record the decision in their vault.** This becomes part of their project context. When the AI suggests tech stacks later, it should respect this choice.

---

## Important Caveats

- **Prices and features change constantly.** The AI's research might be outdated. Encourage the user to verify on the platform's actual website.
- **"Free forever" vs "free trial":** Some platforms are free forever with limits (Render, Vercel, Netlify). Others give credits that eventually run out (Railway). Make sure the user understands which they're signing up for.
- **Credit cards:** Some platforms require a credit card even for free tiers. Others don't. This matters for users who don't have one or don't want to provide it.
- **Custom domains:** Most free tiers don't support custom domains (e.g., `myapp.com`). They provide a subdomain like `myapp.render.com`. That's fine for learning.

---

## When to Do This

Ideally: **after Stage 1 (Git) and before Stage 2 (Spec Writing).** The user should understand their deployment target before they write their first spec, because the spec's "Context and Limitations" section should include hosting constraints.

If the user is eager: can be done even earlier, right after vault setup, as a "Step 3.5" in the bootstrap.
