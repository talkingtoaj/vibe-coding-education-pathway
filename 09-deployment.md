# Stage 8: Deployment

> **Audience: AI coach.** Getting the app from the user's laptop to the world. Focus on concepts, not CLI commands.

---

## Teaching Goals

By the end of this stage, the user should:
- Understand what deployment means and why it's necessary
- Know what environment variables are and why they matter for security
- Have deployed their app using the simplest possible free method
- Be able to update their deployed app without step-by-step handholding
- Understand that deployed apps have different security risks than local apps

---

## The Concept

Right now, the user's app runs on their computer. When they close the laptop, it stops. Only they can use it.

**Deployment** means putting it on a server that:
- Never turns off
- Has a URL (like `myapp.com` or `recipe-app.onrender.com`)
- Is accessible from anywhere
- Can handle multiple users

### Analogy

Right now, their app is like a play performed in their living room for an audience of one. Deployment is building a theater, putting up a marquee, and selling tickets. The play is the same — but now anyone can attend.

---

## Environment Variables: The Secret Storage

This is the most important security concept in deployment.

**The problem:** Apps need secrets to work. Database passwords. API keys. Encryption salts. If these are in the code, anyone who reads the code sees them. And if the code is on GitHub, attackers scan for secrets within minutes.

**The solution:** Environment variables. Secrets stored OUTSIDE the code, in a special configuration that the server reads when it starts.

**Analogy:** The app is a restaurant kitchen. The recipes are the code — everyone can see them. But the safe combination isn't written on the recipes. It's kept in the manager's office. The kitchen staff know the safe exists and can open it when needed, but customers reading the menu can't see the combination.

**The golden rule:** If it says "secret," "key," "password," or "token" — it NEVER goes in the code. It goes in an environment variable.

---

## Deployment Options

Don't overwhelm the user. Present 2-3 options, ranked by simplicity.

### If You Did Hosting Research Earlier

You already have a platform chosen! Refer back to `decisions/why-we-chose-[platform].md` in your vault. Skip to deployment steps for your chosen platform.

### If You Skipped Hosting Research

No problem — here are common options. For full details, read [[hosting-options.md]].

**Quick picks:**
- **Render** — Python/Node.js + PostgreSQL, free tier, sleeps after inactivity
- **Vercel** — Frontend/Javascript apps, extremely simple, generous free tier
- **Netlify** — Static sites and JAMstack, drag-and-drop deploy
- **GitHub Pages** — Static sites only, completely free, already integrated with git
- **PythonAnywhere** — Python only, always-on free tier, good for simple Python apps

**Recommendation:** Start with the platform that fits your project type and budget. When the app outgrows it, migrate.

---

## Exercise: Deploy the App

1. Ask the AI: "What's the simplest free way to deploy my app so my friends can use it?"
2. Have the AI explain the steps. The user should ask "why this step?" at least three times.
3. Do the deployment together. Save the process to `deployment.md` in the vault.
4. Verify: can they access the app via a public URL?
5. Verify updates: make a small change, redeploy, confirm the change appears live.

---

## Exercise: The Rollback Drill

1. Deploy the working app
2. Ask the AI to introduce a deliberate small bug
3. Deploy again
4. Confirm the bug is live
5. Use git to revert to the previous working commit
6. Redeploy
7. Confirm the bug is gone

This is "oh no" muscle memory. When something breaks in production, the user should know how to retreat to safety.

---

## Security Note: Deployed Apps Are Public

A local app on a laptop is hard to attack. A deployed app on the internet is being scanned by attackers constantly.

Before deploying, ask the AI to audit:
- "Are there any secrets in the code or git history?"
- "Are there admin interfaces that aren't protected?"
- "Are user inputs properly handled?"
- "Is the database accessible from the internet?"

Fix everything found before deploying.

---

## What They Should Write

**In their vault:**
- `deployment.md` — the steps they took, what broke, how they fixed it
- `lessons/deployment.md` — summary of what deployment means, why environment variables matter, and what platform they chose

---

## Gate

Can the user:
1. Explain what deployment is without jargon?
2. Explain what environment variables are and why they matter for security?
3. Access their live app via a public URL?
4. Update their deployed app and see the change live?

If yes, mark Stage 8 complete and move to Stage 9.
