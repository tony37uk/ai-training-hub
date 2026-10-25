# 🤖 AI Training Hub

A friendly, single-page hub of AI tools, learning resources, how-to guides and training videos. Built with plain HTML, CSS and JavaScript, hosted free on GitHub Pages.

Sister site to [Tony's AI & Cloud Training Hub](https://github.com/tony37uk/training-hub). This one focuses on AI.

🌐 **Live site:** https://tony37uk.github.io/ai-training-hub/

---

## 📋 What's Inside

| Section | What you'll find |
|---|---|
| 🤖 **AI Resources** | ChatGPT, Claude, Copilot, Gemini, Perplexity, DeepSeek, Qwen, Grok and Meta AI |
| 🔗 **Training Links** | Anthropic Academy, OpenAI Academy, Google Gemini and Hugging Face (each with its own resource page), plus agent and multi-agent courses and articles |
| 📖 **How-To Guides** | GitHub Pages, writing better prompts, Claude Code, AI agents, multi-agent systems and swarms, building a swarm with Claude Code subagents, choosing an agent framework, OpenClaw and vibe coding |
| 🎬 **Training Videos** | Intro to AI for IT pros, AI-assisted coding, LLMs, Ollama, OpenClaw, plus an interactive Power BI for Beginners walkthrough |
| 💬 **Feedback** | A form for visitors to suggest resources or report broken links |

**Features:** search, category filters (AI, Claude, Prompts, AI Coding, Agents), a "mark as complete" progress tracker saved in your browser, and a mobile-friendly layout.

---

## 🗂️ Project Structure

```
ai-training-hub/
├── index.html                    # Main page: layout, styles, search, filters, feedback form
├── data.json                     # All the cards shown on the main page
├── guide-*.html                  # How-to guides
├── resources-*.html              # Resource pages for each training provider
├── powerbi-beginner.html         # Interactive Power BI walkthrough (opens in a popup)
├── feedback-submissions.html     # Admin page for reading feedback (sign-in required)
├── supabase/security.sql         # Database security rules for the feedback table
├── CLAUDE.md                     # Rules Claude Code follows when editing this repo
└── README.md
```

---

## 🚀 Running Locally

The main page loads its cards from `data.json`, which browsers block when you just double-click `index.html`. Run a tiny local web server instead:

```bash
git clone https://github.com/tony37uk/ai-training-hub.git
cd ai-training-hub
python3 -m http.server 8000
```

Then open http://localhost:8000 in your browser. (In VS Code, the Live Server extension does the same job.)

---

## ✏️ Adding Content

All cards on the main page live in **`data.json`**, so no HTML editing is needed. Find the right section and add a card to its `cards` list.

**A link, guide or resource:**

```json
{
  "tag": "AI",
  "tagClass": "tag-blue",
  "title": "Resource Title",
  "description": "One sentence on what this covers.",
  "url": "https://example.com",
  "linkLabel": "Visit →"
}
```

- For a guide in this repo, set `url` to the file name, e.g. `"guide-my-topic.html"`, and `linkLabel` to `"Read guide →"`.
- To link a training provider to its own resource page, add `"subPageUrl": "resources-name.html"`.

**A video:**

```json
{
  "thumb": "🤖",
  "thumbBg": "#ffe0ec",
  "tag": "AI Basics",
  "tagClass": "tag-pink",
  "title": "Video Title",
  "description": "What the video covers and roughly how long it is.",
  "url": "https://www.youtube.com/watch?v=VIDEO_ID",
  "linkLabel": "Watch →"
}
```

**Tag colours:** `tag-blue`, `tag-orange`, `tag-pink`, `tag-green`, `tag-purple`.

Use `https://` links only. Search and the category filters pick up new cards automatically.

---

## 💬 Feedback & Admin

The feedback form saves submissions to a [Supabase](https://supabase.com) database. The `feedback` table is **shared with the Training Hub**, so submissions from both sites appear in one place.

- **Visitors** can only *add* feedback. They can't read, edit or delete anything.
- **The admin** signs in on `feedback-submissions.html` to read feedback, mark it as actioned, delete it or export it to CSV.

The rules are in `supabase/security.sql`. If you set up your own copy, create an admin user in Supabase (Authentication → Users), then run that file in the SQL Editor after replacing `YOUR_ADMIN_EMAIL`. Keep the placeholder in the repo so your email isn't published.

> The key in the page source is Supabase's *publishable* key, which is meant to be public. Never commit the `service_role` key or any password.

---

## 🌍 Deploying

The site deploys automatically from the `main` branch via GitHub Pages. To set it up on a fork: **Settings → Pages → Deploy from a branch → `main` / root → Save**. It's live a minute or two after each push.

---

## 🔧 Built With

- Plain **HTML**, **CSS** and **JavaScript**: no frameworks or build step
- [Google Fonts](https://fonts.google.com): Nunito and Poppins
- [Supabase](https://supabase.com) for the feedback database
- **GitHub Pages** for hosting
- Built with **Claude** and **Claude Code** as a vibe coding training exercise

---

## 🤝 Contributing

Suggestions are welcome. Use the feedback form on the site, or open a GitHub Issue.

If you edit the repo with Claude Code, it reads `CLAUDE.md` automatically and follows the security rules there.

---

*Learning by doing.* 🎓
