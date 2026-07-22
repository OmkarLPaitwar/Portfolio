# Omkar Paitwar — Portfolio

A self-contained portfolio website that also works as an installable web app
(PWA) — visitors can add it to their home screen / desktop like a native app,
using your circuit-board logo as the app icon.

## Structure

```
.
├── index.html                    # the entire site (HTML + CSS + JS, all inline)
├── manifest.json                 # PWA manifest — app name, colors, icons
├── sw.js                         # service worker — enables offline loading + installability
├── icons/
│   ├── icon-192.png              # standard app icon
│   ├── icon-512.png              # standard app icon (large)
│   ├── icon-maskable-192.png     # Android adaptive icon (safe-zone padded)
│   ├── icon-maskable-512.png     # Android adaptive icon (large)
│   ├── apple-touch-icon.png      # iOS home screen icon
│   ├── favicon-32.png / favicon-16.png
├── vercel.json                   # tells Vercel this is a static site, no build needed
└── README.md
```

The photo and résumé PDF are still embedded directly in `index.html` as
base64 data, so the core page has zero external dependencies. The
`manifest.json`, `sw.js`, and `icons/` folder are what make it installable
as a web app — all generated from your uploaded logo.

## Deploy on Vercel (via GitHub)

1. Push this repo to GitHub (see steps below if you haven't yet).
2. Go to https://vercel.com → **Add New... → Project**.
3. Import this GitHub repo.
4. Framework Preset: leave as **Other** / static — no build command, no
   output directory needed. Click **Deploy**.
5. Vercel gives you a live URL like `your-repo-name.vercel.app`.

## Pushing this folder to GitHub for the first time

If you don't already have this in a repo:

```bash
cd portfolio-repo
git init
git add .
git commit -m "Initial portfolio site"
git branch -M main
git remote add origin https://github.com/OmkarLPaitwar/YOUR-REPO-NAME.git
git push -u origin main
```

Replace `YOUR-REPO-NAME` with whatever you name the repo on GitHub (create an
empty repo there first, with no README/gitignore, so there's no merge
conflict on first push).

## After deploying: activate the contact form

The contact form on the site posts to FormSubmit (formsubmit.co), which
forwards submissions straight to **omkarpaitwar1910@gmail.com** — no backend
needed. FormSubmit ties activation to the live URL, so:

1. Once the site is live on Vercel, open it there (not locally).
2. Submit the contact form once with any test message.
3. Check your Gmail for an email from FormSubmit asking you to
   **Activate Form** — click it. This only happens once.
4. Every submission after that lands directly in your inbox.

## Updating the site later

Since it's one static file, updates are simple:

```bash
git add index.html
git commit -m "Update content"
git push
```

Vercel auto-redeploys on every push to `main`.
