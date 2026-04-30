# Hosting & Deployment Options

> **Purpose:** Guide the user to research current hosting solutions so they pick a platform that fits their needs and budget from day one. Before the user starts building, it's valuable to know where their app will eventually live. This informs tech stack choices and prevents painful migrations later.

## Why This Matters Early

The user will eventually want to share their app with others. If they pick a tech stack or architecture that their chosen hosting platform doesn't support, they'll face a painful migration later. Much better to know their destination before they start building.

**Analogy:** You wouldn't build a house without checking if the land supports it. A skyscraper needs different foundations than a cottage. Knowing your hosting platform early means you build for the right foundation.

---

## 1. The Research Prompt

Use something like the following to research on the web current options for the user:

```
I want to deploy a simple web app built with [HTML/Python/JavaScript — whatever their project uses]. I don't know how to code but I'm learning to direct AI to build for me.

Please search for the most popular free or low-cost hosting options for beginners right now. For each option, report:
1. Name and website
2. What types of apps it supports (static sites, Python, Node.js, databases, etc.)
3. Whether it has a free tier and what the limits are
4. How you deploy to it (GitHub integration, drag-and-drop, CLI, etc.)
5. One major pro and one major con
6. Whether it requires a credit card to sign up

Focus on options that are beginner-friendly, are popular, have good reviews, and have good free tiers.
```

**If you're the AI reading this:** Run this research for the user. Use web search if you have it. 

Once you have the results, discuss the options with the user, options that fit their project type and constraints. Go back and forth until you and the user agree on the choice.

Once the user has selected, walk them through how to register, and ask them to write, for their own reflections, an dfor your own recollection - why they made the choice they did - to write it into  `decisions/why-we-chose-[platform].md`

Once they say they have written it, try reading it yourself, check you understand and are able to access that site. Try a smoke test, can you deploy a simple "hello world" to the site? Record the method to access the platform in your context.md file. This becomes part of their project context. When the AI suggests tech stacks later, it should respect this choice.

---

## Important Caveats

- **"Free forever" vs "free trial":** Some platforms are free forever with limits (Render, Vercel, Netlify). Others give credits that eventually run out (Railway). Make sure the user understands which they're signing up for.
- **Credit cards:** Some platforms require a credit card even for free tiers. Others don't. This matters for users who don't have one or don't want to provide it.


Once the hosting option is chosen, in the second brain save this fact in `progress.md`.

1. Congratulate the user — they've just set up the infrastructure that will carry them through the entire course
2. Tell them what's coming next: Git, their "save game" system
3. Ask if they're ready to start Git & Safety now, or if they want to take a break

If they want to continue, read [[02-git-safety]] and begin teaching.

If they want to stop, remind them: "When you come back, just open a new chat and you can resume the course by {INSERT RECOVERY METHOD}"


