# Study Buddy — SQL Module

> Your personal AI study companion for the SCTP Data Science & AI bootcamp (SQL module).

Study Buddy reviews your assignments (without giving away answers), explains concepts when you're stuck, and nudges you toward deeper understanding.

**What you'll need:**
- A Google account (for [Gemini](https://gemini.google.com))
- Two files from this repo: [`study-skills.md`](study-skills.md) and [`course-content.md`](course-content.md)

`study-skills.md` is a **skill file** — it follows the [Agent Skills](https://agentskills.io) format, an open standard for giving AI agents new capabilities. It defines *how* Study Buddy behaves. `course-content.md` is the reference material — it provides *what* Study Buddy knows. Together, they turn a general-purpose AI into your personal study partner.

Setup takes about 5 minutes.

---

## Setup — Gemini (Free)

### Step 1 — Open Gemini

Go to **[gemini.google.com](https://gemini.google.com)** and sign in with your Google account.

<!-- [SCREENSHOT: Gemini homepage with message input at the bottom] -->

### Step 2 — Start a new chat

Click **"New chat"** (top left). Make sure the chat is empty.

<!-- [SCREENSHOT: "New chat" button highlighted] -->

### Step 3 — Paste the skill file

Open [`study-skills.md`](study-skills.md) on GitHub. Click **"Copy raw file"** (top right of the file view).

Paste it into Gemini's message box. **Don't send yet.**

<!-- [SCREENSHOT: GitHub "Copy raw file" button on study-skills.md] -->

### Step 4 — Paste the course content

Open [`course-content.md`](course-content.md) on GitHub. Click **"Copy raw file"** again.

Go back to Gemini and paste below the skill file — in the **same message**. Now send it.

<!-- [SCREENSHOT: Gemini message input showing both files pasted] -->

### Step 5 — Test it

Gemini will respond. Reply with:

> `Hey Study Buddy, what lessons can you help me with?`

It should mention lessons 1.2 through 1.5. If it does, you're good to go.

<!-- [SCREENSHOT: Study Buddy confirming it's ready] -->

---

## Optional: Attach files instead of pasting

If your version of Gemini supports **file attachments** (look for a 📎 or "+" icon near the message box), you can skip the copy-paste steps:

1. **Download both files** from this repo — click each file, then click **"Download raw file"** (↓ icon, top right):
   - [`study-skills.md`](study-skills.md)
   - [`course-content.md`](course-content.md)
2. **Start a new chat** on [gemini.google.com](https://gemini.google.com)
3. **Attach both files** using the 📎 icon
4. **Type this and send:**

> `You are Study Buddy. Read the attached study-skills.md for your instructions and course-content.md for your reference material. Follow the rules in the skill file exactly. Say hi and tell me what lessons you can help with.`

5. Study Buddy should introduce itself and list the lessons it covers. If it does, you're set.

> When you start a new chat, attach both files again — Gemini doesn't carry attachments across chats.

<!-- [SCREENSHOT: Gemini with two attached .md files and the starter prompt] -->

---

## Using Study Buddy

**To get a concept explained:**

> *Explain the difference between 2NF and 3NF — I don't get it.*

> *What's the difference between WHERE and HAVING?*

**To get feedback on your work:**

> *Review my FoodFast schema:* [paste your DBML]

> *Check my Question 3 for Lesson 1.4:* [paste your SQL]

**If you're stuck:**

> *I'm stuck on the junction table for Lesson 1.2 — can you help me think through it?*

---

## Tips

**Start a new chat for each lesson.** When you move to a new lesson, start a fresh chat and re-paste or re-attach both files.

**Study Buddy won't give you the answers.** It helps you understand concepts and points at what's wrong — but it won't write your solution.

**If it seems confused,** start a fresh chat. Long conversations drift.

---

## Optional: Gemini Gems (Gemini Advanced only)

If you have Gemini Advanced, you can create a **Gem** so you don't re-paste every time.

1. Go to [gemini.google.com/gems](https://gemini.google.com/gems) → **Create new Gem**
2. Name it **Study Buddy**
3. In the **Instructions** field, paste [`study-skills.md`](study-skills.md) then [`course-content.md`](course-content.md) below it
4. Save → open the Gem and chat

> If you don't see Gems, use the paste method above.

---

## Something not working?

| Problem | Fix |
|---|---|
| Message too long | Let your instructor know |
| Study Buddy forgot the rules | Start a new chat and set up again |
| Something seems wrong | Tell your instructor — your feedback helps |

---

## About

Study Buddy is a pilot project for the SCTP DS/AI bootcamp at NTU. We're testing whether a personal AI study companion helps learners between class sessions. Your feedback — good or bad — shapes what comes next.

---

## What you just built

You gave an AI agent two things: a **skill file** (how to behave) and **reference material** (what to know). That's the [Agent Skills](https://agentskills.io) pattern — an open standard for extending AI capabilities.

The skill file (`study-skills.md`) is generic — it works with any module's content, not just SQL. The reference material (`course-content.md`) is what makes it specific. Swap the reference file and you have a study buddy for a completely different subject.

This is how AI agents are configured in practice: instructions separate from knowledge, loaded on demand. As a data professional, this is a pattern you'll use again.

> **Try it yourself:** think about a process you know well from your current or previous job. Could you write a skill file and a reference document that would let an AI agent help someone with that process? That's all a skill is.

---

*SCTP DS/AI — SQL Module Pilot, v1 · April 2026*
