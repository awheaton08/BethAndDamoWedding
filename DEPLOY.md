# Deployment Guide — Beth & Damian Wedding RSVP

## What you're deploying
A single-page wedding RSVP website with:
- Guest RSVP form (name, email, attendance, meal choice, message)
- Public "Who has responded" list visible to all guests
- Password-protected admin panel to view and manage all responses
- Botanical sage green design, fully responsive for mobile and laptop

---

## Files in this folder
```
wedding-rsvp/
├── index.html     ← The entire website
└── vercel.json    ← Tells Vercel it's a static site
```

---

## BEFORE YOU DEPLOY — Change the admin password

Open `index.html` in any text editor (Notepad, VS Code, etc).

Find this line near the bottom (around line 340):
```
const PWD = 'BethDamian2025';
```
Change `BethDamian2025` to whatever password Beth or Damian want to use.
Save the file.

---

## Step 1 — Create a GitHub repository

1. Go to https://github.com and sign in to your account (awheaton08)
2. Click the **+** button (top right) → **New repository**
3. Name it: `beth-damian-wedding`
4. Set it to **Private**
5. Do NOT tick "Add a README"
6. Click **Create repository**
7. GitHub will show you a page with setup instructions — leave this open

---

## Step 2 — Push the files to GitHub

Open a terminal (Command Prompt or VS Code terminal) in the `wedding-rsvp` folder, then run:

```bash
git init
git add .
git commit -m "Initial deploy"
git branch -M main
git remote add origin https://github.com/awheaton08/beth-damian-wedding.git
git push -u origin main
```

---

## Step 3 — Deploy to Vercel

1. Go to https://vercel.com and sign in
2. Click **Add New Project**
3. Find `beth-damian-wedding` in the repository list → click **Import**
4. Vercel will auto-detect it as a static site
5. Leave all settings as default
6. Click **Deploy**
7. Wait ~30 seconds — done ✓

Your site will be live at something like:
`https://beth-damian-wedding.vercel.app`

---

## Step 4 — Custom domain (optional)

If Beth or Damian want a domain like `bethanddamian.com`:

1. Buy the domain on Namecheap, GoDaddy, or Google Domains (~£10/year)
2. In Vercel → go to your project → **Settings** → **Domains**
3. Add your domain and follow Vercel's instructions to point the DNS

---

## Giving Beth or Damian admin access

Simply send them the website URL and the admin password you set in Step 0.

To access the admin panel:
- Scroll to the very bottom of the RSVP page
- Click the subtle **Admin** text
- Enter the password
- They can see all responses, filter by attending/declined, and remove entries

---

## Updating the site later

If you need to change the date, names, password, or anything else:

1. Edit `index.html` locally
2. Run in terminal:
```bash
git add .
git commit -m "Update site"
git push
```
Vercel auto-deploys within 30 seconds. No manual steps needed.

---

## Note on data storage

Responses are stored in the browser's **localStorage** on the device of whoever is viewing the admin panel. This means:
- Data persists across browser sessions on the same device ✓
- If Beth or Damian clear their browser data, responses will be lost ✗
- Data is not visible from a different device ✗

**This is fine for a small wedding.** If you later want responses stored in a proper database (visible from any device, never lost), let me know and we can add a simple Supabase backend — same as how the Premakarini platform was structured.
