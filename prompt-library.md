# Prompt Library

> **Audience: AI coach.** Reusable prompt templates for common course activities. Copy and adapt as needed.

---

## Start a Lesson

```
Start lesson. Read my progress from progress.md, check the Vibe Coding Education Pathway for what's next, and teach me that concept. Use analogies from my background in [their background from context.md].
```

---

## Get a Spec Review

```
Review this spec for ambiguities, missing edge cases, and security implications. Be ruthless — imagine you're a user trying to break this or an AI trying to misinterpret it.
```

---

## Run the Angry Agent

```
Here's my spec and what was built. Find the three most likely ways this could fail or be misused. For each one, explain what I should have specified to prevent it.
```

---

## Check Comprehension

```
Explain [file/component] to me as if I'm a new team member who knows nothing about this project. I will then explain it back to you — correct me if I get anything wrong.
```

---

## Security Audit

```
Audit my project for these specific risks:
1. Can any user access another user's data?
2. Are any secrets (passwords, API keys) visible in the code or git history?
3. What happens if someone submits intentionally malformed input?
4. Are there any admin/superuser functions that aren't properly protected?

Report findings in order of severity. For each finding, explain what could happen and how to fix it.
```

---

## The Deletion Test

```
If I deleted [component/file], what would break and how badly? Be specific about which features would stop working and what data might be lost.
```

---

## The Amnesia Test

```
I want to test whether my project spec is sufficient for a fresh AI session. Please read ONLY my project-spec.md and my current spec, then explain what you understand my project to be and what the next feature should do. Don't look at any other files in my second brain.
```

---

## Dependency Security Check

```
Check the libraries and dependencies in my project for known security vulnerabilities. Are there any that need updating? What's the risk level of each?
```

---

## Resume Session

```
Read https://raw.githubusercontent.com/talkingtoaj/vibe-coding-education-pathway/main/resume-course.md and follow it.
```

---

## Monthly Wiki Audit

```
Review my entire second brain and tell me what's missing. What decisions aren't documented? What security assumptions are unstated? What specs are outdated? What comprehension debt hasn't been logged?
```

---

## Threat Model Update

```
I'm about to add this feature: [describe feature]. Update my threat model. What new attack surfaces does this create? What data does it expose? Who can access it? How could it be misused?
```

---

## Cheating Agent Test

```
I wrote these acceptance criteria for a feature. Can you modify the implementation in a way that breaks the actual user experience but keeps these tests passing? If yes, my tests aren't specific enough — show me how to make them cheat-proof.
```

---

## Explain It Simply

```
Explain [concept] to me as if I'm a [their profession, e.g., teacher, nurse, chef] with no coding background. Use only analogies from my field. Then ask me to explain it back to you.
```
