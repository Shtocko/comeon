# PactPal - Setup Guide

This guide walks you through getting PactPal live. No coding knowledge needed — just follow each step.

---

## What you'll need (all free)

- A **Supabase** account → supabase.com
- A **Vercel** account → vercel.com
- A **GitHub** account → github.com
- **Node.js** installed on your computer → nodejs.org (download the "LTS" version)

---

## Step 1 - Set up Supabase (your database)

1. Go to **supabase.com** and sign up / log in
2. Click **"New project"**
3. Give it a name: `pactpal`
4. Choose a strong database password (save it somewhere)
5. Choose a region close to you
6. Click **"Create new project"** and wait ~2 minutes

### Run the database schema

1. In your Supabase project, click **"SQL Editor"** in the left sidebar
2. Click **"New query"**
3. Open the file `supabase/schema.sql` from this folder
4. Copy ALL the text in that file
5. Paste it into the SQL Editor
6. Click **"Run"** (the green button)
7. You should see "Success. No rows returned"

### Get your API keys

1. In Supabase, click **"Project Settings"** (gear icon, bottom left)
2. Click **"API"**
3. Copy these two values (you'll need them in Step 3):
   - **Project URL** (looks like: `https://xxxxxxxxxxxx.supabase.co`)
   - **anon public** key (a long string starting with `eyJ...`)

---

## Step 2 - Put the code on GitHub

1. Go to **github.com** and sign up / log in
2. Click the **"+"** button (top right) → **"New repository"**
3. Name it `pactpal`, leave everything else default, click **"Create repository"**

Now push the code:

1. Open **Terminal** (Mac: search "Terminal" in Spotlight, Windows: search "Command Prompt")
2. Type these commands one by one, pressing Enter after each:

```
cd path/to/pactpal
```
(Replace `path/to/pactpal` with the actual folder location of this app on your computer)

```
npm install
git init
git add .
git commit -m "initial commit"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/pactpal.git
git push -u origin main
```
(Replace `YOUR_USERNAME` with your GitHub username)

---

## Step 3 - Deploy on Vercel

1. Go to **vercel.com** and sign up with your GitHub account
2. Click **"Add New Project"**
3. Find `pactpal` in the list and click **"Import"**
4. Before clicking Deploy, click **"Environment Variables"** and add:

| Name | Value |
|------|-------|
| `NEXT_PUBLIC_SUPABASE_URL` | Your Supabase Project URL from Step 1 |
| `NEXT_PUBLIC_SUPABASE_ANON_KEY` | Your Supabase anon key from Step 1 |

5. Click **"Deploy"**
6. Wait ~2 minutes. Vercel will give you a URL like `pactpal.vercel.app`

That's your app! Open it on your phone.

---

## Step 4 - First use

1. Open your Vercel URL on your phone
2. Register a new account (you're a Member)
3. Go to **Promises** and add your daily commitments
4. Go to **Pals** and generate an invite link
5. Send the link to your pal
6. They open it, register, and they're connected to you automatically

---

## How to use it daily

**Every morning:**
- Open the app
- Tap "Morning check-in" - read your promises, tap "I commit to these today"

**Every evening:**
- Open the app
- Tap "Evening check-in" - check each promise done/not done, add notes

**Your pal:**
- Opens the app, taps "Pal View"
- Sees your check-ins, signs off, leaves comments

---

## Updating the app later

If we add new features, just run:
```
git add .
git commit -m "update"
git push
```
Vercel will redeploy automatically.

---

## Supabase email confirmation (important)

By default Supabase requires email confirmation on signup. To turn this off for a private app:
1. In Supabase → **Authentication** → **Providers** → **Email**
2. Turn off **"Confirm email"**
3. Save

This lets your friends register without email verification friction.
