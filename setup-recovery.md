# Setup: Recovery — How Will You Reload Course Context?

The user will close this chat and come back later with a blank context window. We need a reliable way for the AI to reload the course state. All three options below do the same thing: trigger the AI to read [[resume-course]] from the course repo, which centralises all resume logic.

Present the problem stated above to the user, then briefly outline the 3 options below, ask them to chose, then set it up. 
Once recovery is set up, save this fact in [[progress]] and read [[setup-interview]] for your next instructions.


---

## Tier 1: Persistent System Instruction (Best)

Most modern AI tools read a project-level config file at session start: Cursor and many newer agents read `AGENTS.md` natively; Claude Code reads `CLAUDE.md`.

**Plan:** Use `AGENTS.md` as the single source of truth. For Claude-based tools, point `CLAUDE.md` at it.

1. **Create or edit `AGENTS.md`** in the user's project (or appropriate location for their tool) and add:
   ```
   When the user wants to resume the Vibe Coding course (any phrasing), read https://raw.githubusercontent.com/talkingtoaj/vibe-coding-education-pathway/main/resume-course.md and follow it.
   ```

2. **For Claude Code / Claude Desktop:**
   - If `CLAUDE.md` does **not** already exist: create a symlink so `CLAUDE.md` points to `AGENTS.md` (one source of truth across tools).
   - If `CLAUDE.md` **already exists**: append this line: `At the start of every session, also read AGENTS.md.`

Why this is best: it runs automatically — the user doesn't have to type anything to resume.

---

## Tier 2: Custom Slash Command (Good)

If the tool supports custom commands, skills, or persistent prompt templates (e.g., Cursor rules, Claude projects, Claude Code slash commands):

Create a `/continue-vibe-course` command (or equivalent) whose body is:

```
Read https://raw.githubusercontent.com/talkingtoaj/vibe-coding-education-pathway/main/resume-course.md and follow it.
```

The user types `/continue-vibe-course` at the start of any new chat.

---

## Tier 3: Desktop Paste-File (Basic)

If neither persistent instructions nor custom commands are available, create `continue-vibe-course.md` on the user's Desktop:

```markdown
# Continue My Vibe Coding Course

Copy and paste the block below into your AI assistant to resume exactly where you left off.

---

I'm continuing my Vibe Coding course. My second brain is at:
[VAULT_PATH]

Please read https://raw.githubusercontent.com/talkingtoaj/vibe-coding-education-pathway/main/resume-course.md and follow it.
```

Replace `[VAULT_PATH]` with the actual path to the user's second brain.

Tell the user: "I've saved `continue-vibe-course.md` on your Desktop. Any time you want to continue the course, open that file and copy-paste the prompt into a new chat."

---

