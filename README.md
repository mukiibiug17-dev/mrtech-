# MR Tech Solutions: Website with AI Assistant

A website with a live AI chat assistant that answers visitors' questions about cybersecurity, digital forensics and camera and network installation. The AI runs on your server through the Claude API, so your API key is never exposed to visitors.

## What is inside

```
server.js         the server: serves the website and answers chat questions
package.json      list of packages
.env.example      copy to .env and add your API key (for running on your own computer)
.gitignore        keeps your secret .env file out of GitHub
public/
  index.html      the website (services, photo slider, profile, chat, contact form)
  images/         logo, photos and slides
```

## 1. Get your API key (needed for the AI)

1. Go to https://console.anthropic.com and create an account.
2. Add a small amount of credit under Billing. API use is billed separately from the Claude app.
3. Set a monthly spending limit in the Console so you never get a surprise bill.
4. Open API Keys, click Create Key, and copy it. Keep it private.

## 2. Test on your computer (optional)

1. Install Node.js (LTS) from https://nodejs.org
2. In the project folder run: `npm install`
3. Copy `.env.example` to `.env` and paste your key after `ANTHROPIC_API_KEY=`
4. Run: `npm start` and open http://localhost:3000

## 3. Put it online (Render example)

1. Create a free account at https://github.com and make a new repository. Upload all the project files and folders (do not upload `.env` or `node_modules`).
2. Create a free account at https://render.com. Choose New, then Web Service, and connect your GitHub repository.
3. Use these settings: Build command `npm install`, Start command `npm start`.
4. Under Environment Variables add `ANTHROPIC_API_KEY` with your key. Optional: `DAILY_LIMIT` (default 500 AI answers per day).
5. Deploy. Render gives you a public link. Open it and test the chat.
6. Later you can connect your own domain name in the host's settings.

Railway and similar hosts work the same way: build `npm install`, start `npm start`, add the environment variable. Free plans may put the site to sleep when nobody visits, so the first load can be slow.

## Settings you can change

- **Business details and texts:** `public/index.html`.
- **What the AI knows and how it behaves:** `SYSTEM_PROMPT` in `server.js` (services, contact details, rules).
- **Contact form delivery:** at the top of the script in `index.html`, paste a Formspree form URL into `CONTACT_ENDPOINT` so messages arrive in your inbox. If left empty, the form opens the visitor's email app, and the WhatsApp button always works.
- **Cost protection:** each visitor can ask 20 questions per 10 minutes, and the whole site is capped at `DAILY_LIMIT` answers per day.

## Safety notes

- Never share or upload your real `.env` file. If your key leaks, delete it in the Console and create a new one.
- The assistant is set to give defensive advice only and to refuse requests to attack systems.
- Tell visitors not to type passwords or PINs into the chat (the page already says so).
