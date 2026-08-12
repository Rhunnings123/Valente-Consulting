# Valente Consulting Website

A static site — `index.html` plus a small set of supporting files. As of this update, images are now
separate optimized files in the `img/` folder rather than embedded directly in the HTML, which cut the
page weight from ~1.5MB down to under 100KB for the HTML itself (images load separately, in parallel,
and get cached by the browser).

## Files in this folder

```
index.html              — the site itself
img/                     — all site images (logo, hero photo, founder photo, favicons)
og-image.jpg             — social share preview image (must stay at the repo root, not inside img/)
privacy-policy.html
terms-conditions.html
robots.txt
sitemap.xml
404.html
blog.html                — blog listing page, linked from the main nav
blog-impact-of-mentorship.html
blog-risks-of-standing-still.html
```

## Deploy via GitHub + Vercel

### 1. Push this folder to GitHub

If this is your first upload, use git:

```bash
cd path/to/this/folder
git init
git add .
git commit -m "Initial site"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/YOUR-REPO-NAME.git
git push -u origin main
```

**If you're updating an existing repo via GitHub's web upload** (the method used so far in this
project): go to your repo → "Add file" → "Upload files" → drag in the *entire* `img` folder along with
all the other files at once. GitHub's uploader preserves folder structure when you drag a folder in, so
the images will land correctly at `img/logo.png` etc. rather than loose in the repo root. Delete any old
version of these files first if they already exist, to avoid the duplicate-filename renaming issue
(`index_2.html` etc.) that came up earlier in this project.

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
- **Social share image** — `og-image.jpg` (included in this folder) needs to be uploaded to GitHub alongside `index.html`, sitting at the root of the repo. This is what shows up as the preview image when the site link is shared on LinkedIn, Facebook, WhatsApp, etc. It must live at exactly `https://valenteconsulting.co.uk/og-image.jpg` for the meta tags in `index.html` to find it.
- **Privacy Policy & Terms and Conditions** — `privacy-policy.html` and `terms-conditions.html` are included and linked from the footer. These are **starting templates, not finished legal documents** — every `[bracketed placeholder]` (company number, registered address, contact details, actual cancellation/payment terms) needs to be filled in with real information, and a solicitor should review both pages in full before launch. The Terms page in particular was deliberately rewritten from scratch to match a one-day workshop offer — don't copy in terms from any other business without checking they actually match what you're selling.

## What's now included (this update)

- **`robots.txt`** and **`sitemap.xml`** — basic SEO hygiene, tells search engines how to crawl the site and lists all 3 real pages
- **`404.html`** — a branded not-found page instead of Vercel's generic default. Upload it to the repo root; Vercel automatically serves it for broken links
- **Structured data** (JSON-LD) in `index.html` — helps search engines understand the business. Deliberately kept conservative: only real, verifiable facts (name, founder, description). No fake ratings, address, or phone number included, since those aren't confirmed yet
- **Consent checkbox** added to the application form — required, links to the Privacy Policy
- **Cookie consent banner** — appears once per visitor (remembers dismissal), since the Superchat and Formspree widgets likely set cookies

## Still outstanding (needs your input)

- **Footer contact details** — the phone number, email, and "Premium Venue" location in the footer are still placeholders. Real ones should go in before launch.
- **Analytics** — no GA4 or Meta Pixel installed yet. Set up an account and send me the tracking ID and I'll wire it in.
- **Google Search Console** — `index.html` has a commented-out verification tag ready to go. Create a free account at [search.google.com/search-console](https://search.google.com/search-console), add your domain as a property, and it'll give you a verification code — send it to me (or uncomment the tag yourself and paste the code in) and submit `sitemap.xml` once verified.
- **Cookie banner accuracy** — I added a generic banner assuming Superchat/Formspree set cookies, which is a reasonable assumption for a live chat + form tool, but worth confirming against their actual privacy documentation.
- **Footer details** — phone number, website link, and social icons are placeholders (search for `href="#"` in the footer section).
- **Testimonials** — three of the four reviews shown are real (Brandon Harper, Project Abundance, Derren Miller-Price); double-check none of the surrounding copy needs updating as new reviews come in.

## Editing later

Everything — HTML, CSS, and JavaScript — lives in the one `index.html` file. Images are embedded as base64 data, so there are no separate asset files to manage; if you want to swap a photo, you'll need to re-embed it (or ask whoever's helping you edit the site to do it).
