# JTKiaz Writing Studio — GitHub setup (about 15 minutes, once)

You make **two** repositories:

| Repo | Visibility | What's in it |
|---|---|---|
| `writing-studio` | Public | Just the app (`index.html`). Free GitHub Pages needs public. |
| `writing-studio-data` | **PRIVATE** | Your books, progress, badges. The app writes here by itself. |

Your writing never goes in the public repo.

---

## Step 0 — Before anything else: make a safety copy of what you have now
Open your **old** Writing Studio file → **All-Time** tab → **Full backup (.json)**. Then for each book tab: **Book JSON** tab → **Download .json**. Keep these files.

## Step 1 — The app repo (public)
1. github.com → **New repository** → name `writing-studio` → **Public** → Create.
2. **Add file → Upload files** → drag in **all five files**: `index.html`, `manifest.webmanifest`, `sw.js`, `icon-192.png`, `icon-512.png` → Commit.
   (The last four are what make phone install and offline use work. Updating later = upload the new `index.html` over the old one.)
3. **Settings → Pages** → Source: *Deploy from a branch* → Branch `main`, folder `/ (root)` → Save.
4. After a minute your app is live at `https://YOUR-USERNAME.github.io/writing-studio/`

## Step 2 — The data repo (private)
1. **New repository** → name `writing-studio-data` → **Private** → tick **Add a README file** → Create.
   (The README matters: it creates the `main` branch.)

## Step 3 — Make an access token (the app's key to the private repo)
1. GitHub → your picture → **Settings → Developer settings → Personal access tokens → Fine-grained tokens → Generate new token**.
2. Name: `writing-studio`. Expiration: the longest offered (put a reminder in your calendar).
3. **Repository access → Only select repositories →** `writing-studio-data`.
4. **Permissions → Repository permissions → Contents → Read and write.**
5. Generate, then **copy the token now** (starts `github_pat_…`). You can't see it again.

## Step 4 — Bring your existing work in (this order matters)
Your old work lives in this browser's storage for the **file on your computer**; the website is a different address and can't see it. So first:
1. On the computer + browser you always used, **double-click the new `index.html`** (open it from your files, not from the website).
2. Open **☁ GitHub sync on this device**: enter your GitHub username, `writing-studio-data`, `main`, and the token → **Save & test connection**. (It refuses if the repo is public.)
3. Sign in: **JTKias** / your password. It finds your earlier chapters, progress and badges and uploads them. Wait for the top bar to say **☁ Synced**.
4. Check the data repo: you should see `data/jtkias.json` and `profiles.json`.

If it doesn't find your old work, sign in anyway, then **⚙ Settings → Backup file → Restore from backup…** and choose the backup from Step 0.

## Step 5 — Every other device (phone, laptop…)
1. Open your website address.
2. **☁ GitHub sync on this device** → username, repo, token → Save & test.
3. Sign in. Your books, progress and badges appear.
Tip: edit `index.html` on GitHub (pencil icon) and fill in `CONFIG` near the top with your username so new devices only need the token.

---

## How it protects your work
- Saves on the device as you type, in two places (browser storage + a second backup store).
- Uploads to your private repo a few seconds after you stop typing, and at least every 30 seconds while typing, and when you leave the tab.
- Every upload is a GitHub commit, so there is a full history. A daily snapshot goes in `backups/`.
- **Wipe guard:** if a device suddenly holds far less text than GitHub, syncing pauses and asks you, instead of overwriting.
- **Two versions?** If two devices edited separately you get a dialog; **Merge** keeps the longer version of every chapter and the best stats. Safety copies go in `conflicts/`.
- One tab per profile: a second tab pauses itself so the two can't overwrite each other.
- Offline is fine: it saves locally and uploads when you're back.

## Good to know
- **The password is a convenience lock, not real security.** The page's code is public, and a 6-digit password can be guessed. What actually keeps your writing private is the **private data repo + token**. Anyone opening your site sees only a login box and no work.
- The token is stored in each device's browser. Lost a device? GitHub → Settings → Developer settings → revoke it, make a new one.
- Expired token → the app says "Sync problem / token rejected". Make a new token and paste it in **⚙ Settings → GitHub sync**.
- Use **⚙ → Switch profile / log out** on shared computers.
- New profile (⚙ → Profiles) = its own empty book, progress and badges, stored as `data/<name>.json`.
- Username/password change (⚙) is also synced, so other devices pick it up at next sign-in.

## Install on your phone (home-screen app, works offline)
Open your website address on the phone, then ⚙ Settings → **Install on your phone or computer** shows the exact step for your device (iPhone: Safari → Share → Add to Home Screen; Android: Chrome ⋮ → Install app). Offline it opens from the saved copy, you keep writing, and it uploads when you're back online.

## New buttons
- **◧ (top-left, or Ctrl+\\)**: hide/show the left panel. Remembered. On a phone it swaps between the panel and your writing.
- **📄 (top bar) or "Export to .txt"** in the Chapters panel: whole book, this chapter, or chosen chapters. Plain text or with formatting marks, optional poems.
- **⚙ Settings**: password, profiles, GitHub, full backup/restore.
- **🎯 Focus mode (Ctrl+Shift+F)**: hides everything except your words. Pick a timer (15/25/45/60/custom, or count-up), dim dark screen, typewriter scrolling, optional full screen. A chime and message when time's up. Esc exits.
- **⌖ Typewriter scrolling** (next to the quote button): the line you're typing stays in the middle of the screen.
- **🔎 Find & Replace**: this chapter, whole book, or all book tabs; match case, whole word, include poems/titles. Click a result to jump to it. **Undo last replace** is in the same window.
- **🕘 Versions**: browse earlier saves (on this device, or every autosave on GitHub), read any chapter, then restore one chapter or the whole book. Your current work is saved as a safety copy first. Restoring leaves your progress and badges alone unless you tick the box.
- **Chapter target**: under the editor, set words per chapter with a progress bar; "Apply to all chapters" copies it everywhere. The chapter list shows `340/1500w ✓`.
- **Word Check tab**: word cloud, overused words, crutch words (very, really, just, suddenly…), repeated phrases, sentence rhythm, for this chapter or the whole book. Click any word to find it.
