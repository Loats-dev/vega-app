# 🚀 How to Deploy V.E.G.A. to the Public (Beginner Guide)

This guide walks you through putting V.E.G.A. online so anyone in the world can use it.
**Total time: ~20 minutes. No coding required.**

---

## 📁 What's in this folder?

```
vega-app/
├── public/
│   └── index.html      ← The V.E.G.A. website (what users see)
├── api/
│   └── chat.js         ← Secret server that talks to Anthropic (users can't see this)
└── vercel.json         ← Tells Vercel how to set everything up
```

**Why two files?** Your Anthropic API key must NEVER be in `index.html` (anyone could steal it).
The `api/chat.js` file runs on Vercel's secure servers — your key stays hidden there.

---

## STEP 1 — Create a GitHub Account (if you don't have one)

1. Go to **https://github.com**
2. Click **Sign up** and create a free account
3. Verify your email

---

## STEP 2 — Upload Your Project to GitHub

1. Go to **https://github.com/new** to create a new repository
2. Name it `vega-app`
3. Leave everything else as default, click **Create repository**
4. On the next page, click **uploading an existing file**
5. Upload ALL files maintaining the folder structure:
   - Upload `vercel.json` to the root
   - Create a folder called `api` → upload `chat.js` inside it
   - Create a folder called `public` → upload `index.html` inside it
6. Click **Commit changes**

> 💡 Tip: If file uploading feels confusing, use GitHub Desktop (https://desktop.github.com) — it lets you drag and drop your whole `vega-app` folder.

---

## STEP 3 — Create a Vercel Account

1. Go to **https://vercel.com**
2. Click **Sign Up**
3. Choose **Continue with GitHub** (this links them together — very important!)
4. Authorize Vercel to access your GitHub

---

## STEP 4 — Deploy V.E.G.A. on Vercel

1. Once logged into Vercel, click **Add New → Project**
2. Find your `vega-app` repository in the list and click **Import**
3. Leave all settings as they are — Vercel detects everything automatically
4. Click **Deploy**
5. Wait ~1 minute while Vercel builds your site
6. 🎉 You'll see a green "Congratulations!" screen with a live URL like:
   `https://vega-app-yourusername.vercel.app`

**But wait — it won't work yet!** You still need to add your secret API key.

---

## STEP 5 — Add Your Anthropic API Key (The Most Important Step!)

This is how V.E.G.A. gets permission to use Claude AI — and it stays 100% secret.

1. Go to **https://console.anthropic.com**
2. Sign in (or create a free account)
3. Click **API Keys** in the left sidebar
4. Click **Create Key**, name it `VEGA Production`, copy the key (starts with `sk-ant-...`)
   ⚠️ Save it somewhere safe — you can only see it once!

Now add it to Vercel:

1. In your Vercel project dashboard, click **Settings** (top menu)
2. Click **Environment Variables** (left sidebar)
3. Fill in:
   - **Name:** `ANTHROPIC_API_KEY`
   - **Value:** paste your key (`sk-ant-...`)
4. Make sure **Production**, **Preview**, and **Development** are all checked
5. Click **Save**

6. Go back to your project → click **Deployments** → click the three dots on your latest deployment → click **Redeploy**

---

## STEP 6 — Visit Your Live V.E.G.A.!

Go to your Vercel URL (e.g. `https://vega-app-yourusername.vercel.app`) and V.E.G.A. should be fully working!

Share this link with anyone — it's public! 🌍

---

## STEP 7 (Optional) — Get a Custom Domain

Want `www.myvega.com` instead of the long Vercel URL?

1. Buy a domain at **https://namecheap.com** or **https://domains.google**
2. In Vercel → Settings → **Domains** → Add your domain
3. Follow Vercel's simple instructions to point your domain to Vercel
4. Done — usually takes 10–30 minutes to go live

---

## 💰 Cost Breakdown

| Service | Cost |
|---|---|
| Vercel hosting | **FREE** (up to 100GB bandwidth/month) |
| GitHub | **FREE** |
| Custom domain | ~$10–15/year (optional) |
| Anthropic API | **Pay per use** — roughly $0.003 per conversation |

> 💡 Anthropic gives new accounts some free credits to start. For light usage, costs are very low.

---

## 🔒 Is It Secure?

Yes! Here's why:
- Your API key is stored in Vercel's encrypted environment — no one can see it
- Users talk to `/api/chat` on your server — they never touch Anthropic directly
- Vercel automatically handles HTTPS (the padlock in the browser)

---

## ❓ Common Problems

**"Function not found" error** → Make sure `api/chat.js` is in a folder called exactly `api`

**"Invalid API key" error** → Double-check you copied the full key and redeployed after adding it

**Page loads but chat doesn't work** → Open browser DevTools (F12) → Console tab and share the error message

---

## 🆘 Need Help?

- Vercel docs: https://vercel.com/docs
- Anthropic console: https://console.anthropic.com
- GitHub help: https://docs.github.com
