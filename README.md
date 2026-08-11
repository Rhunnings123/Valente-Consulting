# Valente Consulting Website

A single self-contained static site (`index.html`) — no build step, no dependencies, all images embedded directly in the file. This makes deployment as simple as possible.

## Deploy via GitHub + Vercel

### 1. Push this folder to GitHub

```bash
cd path/to/this/folder
git init
git add .
git commit -m "Initial site"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/YOUR-REPO-NAME.git
git push -u origin main
```

(Create the empty repo on GitHub first at github.com/new, then use the URL it gives you in place of the one above.)

### 2. Import into Vercel

1. Go to [vercel.com/new](https://vercel.com/new) and sign in (GitHub login is easiest).
2. Click **Import** next to the repo you just pushed.
3. Vercel will detect it as a static site automatically — no framework, no build command needed. Leave all settings as default.
4. Click **Deploy**.

That's it — Vercel will give you a live `.vercel.app` URL within about a minute. From there you can add a custom domain (e.g. `valenteconsulting.co.uk`) under **Project Settings → Domains**.

## Before this goes fully live

A few things in the current build are placeholders and need real content before launch:

- **Lead form submission** — ✅ wired up to Formspree (`https://formspree.io/f/xbgrokjg`). Submissions are sent via AJAX and land in your Formspree inbox / forward to whatever email you connected there. Test it once live to confirm.
- **Video links** — the "Watch Success Stories" video currently streams from Dropbox share links, which aren't reliable for production. Move both files to a proper host (YouTube unlisted, Vimeo, or a CDN like Cloudflare Stream/Bunny.net).
- **Footer details** — phone number, website link, and social icons are placeholders (search for `href="#"` in the footer section).
- **Testimonials** — three of the four reviews shown are real (Brandon Harper, Project Abundance, Derren Miller-Price); double-check none of the surrounding copy needs updating as new reviews come in.

## Editing later

Everything — HTML, CSS, and JavaScript — lives in the one `index.html` file. Images are embedded as base64 data, so there are no separate asset files to manage; if you want to swap a photo, you'll need to re-embed it (or ask whoever's helping you edit the site to do it).
