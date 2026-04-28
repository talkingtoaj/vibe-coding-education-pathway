# Teaching: The Second Brain

> **Audience: AI coach.** How to explain the second brain concept, evaluate options with the user, and set up their chosen tool as shared persistent memory between human and AI.

---

## What to Explain

### For Humans (The Familiar Part)

"A second brain" is a term for any system that stores information your biological brain can't hold. People use notebooks, note apps, wikis, or tools like Notion, Evernote, Apple Notes, Google Keep, or Obsidian. The idea is: instead of trying to remember everything, you write it down in an organized, searchable system and let your brain do what it's good at — thinking, connecting ideas, being creative.

### For Our Course (The Special Part)

Here's what's unique about our setup: **your second brain is a meeting place between you and me.**

I — your AI assistant — have a limitation called the **context window.** Think of it like short-term memory. I can remember what we've talked about in this conversation, but:
- If the conversation gets very long, I start forgetting earlier parts
- If you close this chat and open a new one tomorrow, I start completely fresh
- I don't automatically know what you decided last week or what your project is about

**Your second brain fixes this.** When we write things there:
- You can read them anytime, even when I'm not here — on your computer AND on your phone
- I can read them at the start of every new conversation
- We both write to the same files, so our "memory" stays synchronized
- It's a shared workspace, not just your private notes

This means you get **continuity.** A course that spans weeks or months, across dozens of chat sessions, with me always knowing where we are and what we've learned. And you can review anything on your phone while riding the bus or waiting in line.

---

## The Two Requirements

Whatever tool we choose, it must satisfy both of these:

1. **The AI can access and modify its contents.** This is the meeting ground. If I can't read your notes and write to them, we lose the shared memory that makes the course work.

2. **It syncs between your computer and your mobile phone.** You need to review notes, check your progress, or jot down ideas on the go. If it's only on your laptop, you'll forget to check it.

---

## Evaluating Options Together

Don't mandate a tool. Research with the user and let them choose.

### The Research Prompt

Give the user this prompt to run (or run it for them if you can search):

```
I need a "second brain" note-taking app for a long-term learning project. Requirements:
1. My AI assistant must be able to read and write files in it (it needs filesystem access or an API)
2. It must sync between my computer and my mobile phone

Please research current options and for each one report:
- Name and website
- Computer platforms supported (Windows/Mac/Linux/Web)
- Mobile platforms supported (iOS/Android)
- Sync method and any associated cost
- Whether files are accessible to external tools (AI assistants, scripts, backup tools)
- Free tier limitations and paid tier cost
- One major pro and one major con
- Best for: what type of user or use case

Focus on options that are actively maintained and have good free tiers.
```

### Common Options (as of 2026 — verify current details)

**Obsidian (obsidian.md)**
- Platforms: Windows, Mac, Linux, iOS, Android
- Sync: Obsidian Sync ($8/month) OR free alternatives (iCloud, Dropbox, Git, Syncthing)
- File access: Plain markdown files on disk — any AI tool with file access can read/write
- Free tier: Fully free. Only sync costs money if you use Obsidian's official sync.
- Pro: Files are yours forever, work offline, extremely flexible
- Con: Sync requires setup (not built-in for free). Mobile editing is good but not as polished as dedicated mobile apps.
- Best for: Users who want full ownership of their data and don't mind a little setup

**Notion (notion.so)**
- Platforms: Web, Windows, Mac, iOS, Android
- Sync: Built-in, free
- File access: API available, but AI assistants typically can't read/write Notion pages directly via filesystem
- Free tier: Generous for personal use
- Pro: Beautiful, collaborative, great mobile experience
- Con: AI access is harder — requires Notion API integration, not simple file reading. Data is on Notion's servers.
- Best for: Users who want polish and collaboration, and whose AI can work with APIs

**Apple Notes**
- Platforms: Mac, iOS, Web (via iCloud.com)
- Sync: iCloud, free
- File access: Very difficult for external tools. Files are in a proprietary database.
- Free tier: Free with Apple ID
- Pro: Native, fast, great mobile experience
- Con: AI assistants essentially can't access these files. Breaks requirement #1.
- Best for: Apple-only users NOT doing this course (doesn't meet our AI access requirement)

**Google Keep**
- Platforms: Web, Android, iOS
- Sync: Built-in, free
- File access: API exists but AI assistants can't read/write directly via filesystem
- Free tier: Free
- Pro: Simple, fast, great for quick notes
- Con: Not designed for structured knowledge management. Limited formatting. AI access is API-only.
- Best for: Quick capture, not for a structured course

**Standard Notes (standardnotes.com)**
- Platforms: Windows, Mac, Linux, iOS, Android, Web
- Sync: Built-in sync is paid ($4/month). Can self-host for free.
- File access: Files are accessible if you self-host or use local storage
- Free tier: Can use without sync (local only)
- Pro: Privacy-focused, encrypted, open source
- Con: Sync costs money unless you self-host (technical). Less flexible than Obsidian.
- Best for: Privacy-focused users comfortable with technical setup

**Logseq (logseq.com)**
- Platforms: Windows, Mac, Linux, iOS, Android
- Sync: iCloud, Git, or third-party sync (no built-in paid sync)
- File access: Plain markdown files on disk — AI accessible
- Free tier: Completely free and open source
- Pro: Outliner-style, great for thinking, free forever
- Con: Different paradigm (outliner vs traditional notes). Mobile app is newer.
- Best for: Users who think in outlines, want free forever, don't need polished mobile

**Joplin (joplinapp.org)**
- Platforms: Windows, Mac, Linux, iOS, Android
- Sync: Dropbox, OneDrive, Nextcloud, Joplin Cloud (paid), etc.
- File access: Can export to markdown, but native format is proprietary
- Free tier: App is free. Sync may cost depending on method.
- Pro: Open source, good web clipper, multiple sync options
- Con: AI file access is less direct than Obsidian/Logseq. Native format isn't plain markdown.
- Best for: Users who want open source with built-in web clipping

**Microsoft OneNote**
- Platforms: Windows, Mac, Web, iOS, Android
- Sync: OneDrive, free
- File access: Very difficult for external AI tools. Proprietary format.
- Free tier: Free
- Pro: Familiar, great handwriting support
- Con: AI assistants can't read/write the files. Breaks requirement #1.
- Best for: Users not doing this course (doesn't meet our AI access requirement)

**Plain Text / Markdown Files in Dropbox/iCloud/Google Drive**
- Platforms: Any
- Sync: Via the cloud service
- File access: AI can read/write if synced to local disk
- Free tier: Depends on cloud service
- Pro: Maximum flexibility, works with any tool
- Con: No built-in note-taking features (search, linking, organization). Just folders and files.
- Best for: Minimalist users who want maximum interoperability

---

## The Decision Process

After research, ask the user:

1. "Which of these do you already use or have heard of?"
2. "Do you prefer something that 'just works' (even if it costs a little) or something free that needs a bit of setup?"
3. "Is plain text file ownership important to you, or are you comfortable with your notes living in a company's cloud?"
4. "Do you want something polished and beautiful, or functional and flexible?"

**Common recommendation path:**
- **Obsidian** is the default recommendation because: free to use, plain markdown files (AI can read/write directly), extremely flexible, active community. The only cost is sync if they want official Obsidian Sync — but free alternatives (iCloud on Apple, Dropbox, Git, Syncthing) work fine.
- **Notion** if they want polish and collaboration and their AI setup can handle APIs.
- **Logseq** if they want free forever and think in outlines.

**If the user already uses a tool that doesn't meet both requirements** (e.g., Apple Notes, OneNote): gently explain why it won't work for this course and help them pick a second tool just for the course. They can keep using Apple Notes for everything else.

---

## Setup: The Key Steps

Regardless of which tool they choose:

1. **Create a dedicated space** — folder, workspace, or vault for the course. Don't mix it with everything else.
2. **Name it clearly** — `vibe-coding-course`, `AI-learning-notes`, or similar.
3. **Place it somewhere the AI can access** — a folder on the computer's drive that the AI tool has permission to read/write.
4. **Set up sync to mobile** — verify they can open and edit on their phone.
5. **Test the AI access** — have the AI write a test file, then read it back.

---

## Troubleshooting

**"The AI can't read my note files."**
- Is the vault/folder in a location the AI tool has permission to access? (Claude Desktop: check Settings → Developer → Allowed directories)
- Are the files plain text/markdown, or a proprietary format?
- Try a simpler location: Desktop, Documents, or home folder.

**"I don't know how to sync to my phone."**
- Obsidian: Install mobile app → enable sync method (iCloud, Dropbox, etc.) → open the same vault
- Notion: Install app → log in → everything syncs automatically
- Logseq: Install mobile app → enable iCloud/Git sync

**"This feels like a lot of setup before we even start."**
- Acknowledge it. "It is. But this 15 minutes of setup saves hours of repetition later. Every time we meet, I'll know exactly where we are because we wrote it down together. And you can review your notes on the bus."

---

## After Setup: Test It

1. Create `home.md` (see [[bootstrap.md]] for template)
2. Create `Vibe coding - Zero to Hero - Course progress.md` (see [[bootstrap.md]] for template)
3. Write something to the progress file
4. Read it back
5. Ask the user to open it on their phone and confirm they see the same thing
6. Ask the user to make a small edit on their phone and confirm it appears on the computer

If all of this works, the second brain is operational. Celebrate this — it's a genuine milestone.
