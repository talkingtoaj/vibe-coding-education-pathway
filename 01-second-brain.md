# Teaching: The Second Brain

> **Audience: AI coach.** How to explain Obsidian as shared persistent memory between human and AI.

---

## What to Explain

### For Humans (The Familiar Part)

"A second brain" is a term for any system that stores information your biological brain can't hold. People use notebooks, note apps, wikis, or tools like Notion and Obsidian. The idea is: instead of trying to remember everything, you write it down in an organized, searchable system and let your brain do what it's good at — thinking, connecting ideas, being creative.

### For Our Course (The Special Part)

Here's what's unique about our setup: **your second brain is a meeting place between you and me.**

I — your AI assistant — have a limitation called the **context window.** Think of it like short-term memory. I can remember what we've talked about in this conversation, but:
- If the conversation gets very long, I start forgetting earlier parts
- If you close this chat and open a new one tomorrow, I start completely fresh
- I don't automatically know what you decided last week or what your project is about

**Your Obsidian vault fixes this.** When we write things there:
- You can read them anytime, even when I'm not here
- I can read them at the start of every new conversation
- We both write to the same files, so our "memory" stays synchronized
- It's on your computer, not on some company's server (unless you choose to sync it)

This means you get **continuity.** A course that spans weeks or months, across dozens of chat sessions, with me always knowing where we are and what we've learned.

---

## Teaching Script

Use these talking points, adapted to the user's background:

1. **"Imagine you're learning to cook from a chef."**
   - If the chef forgot every previous lesson each time you met, you'd spend half of each session re-explaining what a saucepan is.
   - Our second brain is like a shared recipe book: you write notes, the chef reads them before each lesson, and you both add to it over time.

2. **"It's also your study notes."**
   - After each lesson, you'll write a summary in your own words. This isn't homework for me — it's for you. If you can't explain it simply, you didn't learn it.
   - Six months from now, you'll have a personal encyclopedia of everything you've learned.

3. **"It's transparent."**
   - Unlike conversation history that gets buried in a chat app, Obsidian files are plain text files on your computer. You own them. You can edit them, back them up, export them. Nothing is hidden.

---

## What to Have the User Do

1. **Download Obsidian** from https://obsidian.md (it's free for personal use)
2. **Install it** and create a new vault
   - Name it something meaningful: `vibe-coding-wiki`, `my-second-brain`, or their own name
   - Place it somewhere they'll remember: Documents folder, Desktop, etc.
3. **Tell you the full folder path** so you can read and write files there
4. **Grant you access** if their AI tool requires folder permissions

---

## Troubleshooting

**"I can't find where Obsidian saved my vault."**
- On Windows: usually in `C:\Users\[username]\Documents\[vault-name]`
- On Mac: usually in `~/Documents/[vault-name]`
- The easiest way: in Obsidian, click the vault name (bottom left) → "Open vault settings" → look at the "Path"

**"You can't read my vault files."**
- Claude Desktop: you may need to add the vault folder to allowed directories. Go to Settings → Developer → Edit Configuration → add the vault path.
- Cursor: similar process in settings.
- If the AI tool truly can't access the filesystem, the user can copy-paste file contents. This is less convenient but still workable.

**"This feels like a lot of setup before we even start."**
- Acknowledge it. "It is. But this 15 minutes of setup saves hours of repetition later. Every time we meet, I'll know exactly where we are because we wrote it down together."

---

## After Setup: Test It

1. Create `home.md` (see [[bootstrap.md]] for template)
2. Create `Vibe coding - Zero to Hero - Course progress.md` (see [[bootstrap.md]] for template)
3. Write something to the progress file
4. Read it back
5. Ask the user to open it in Obsidian and confirm they see the same thing

If all of this works, the second brain is operational. Celebrate this — it's a genuine milestone.
