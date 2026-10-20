# Deploying your portfolio

The `site/` folder is the whole website: `index.html` and `Shubhram_Priyadarshan_CV.pdf`. There is no build step.

## Option 0: Render (static site)
Render deploys from a Git repository, not from a zip, so push the extracted files first.
1. Extract the zip. Create a new GitHub (or GitLab) repository and push the extracted files to its root:
   ```
   git init && git add . && git commit -m "Portfolio"
   git branch -M main
   git remote add origin https://github.com/shbzstrkr1999/portfolio.git
   git push -u origin main
   ```
2. In Render, click New > Static Site and connect that repository.
3. Settings: Branch `main`, Build Command empty (or `echo done`), Publish Directory `.`
4. Click Create Static Site. Render gives you a URL like `https://portfolio-xxxx.onrender.com`. Every push to `main` redeploys it.

## Option 1: GitHub Pages (free, fits your GitHub profile)
1. Create a repository named `shbzstrkr1999.github.io` (public).
2. Put `index.html` and the PDF in the repository root and push:
   ```
   git init && git add . && git commit -m "Portfolio"
   git branch -M main
   git remote add origin https://github.com/shbzstrkr1999/shbzstrkr1999.github.io.git
   git push -u origin main
   ```
3. Repository Settings > Pages > Source: "Deploy from a branch", branch `main`, folder `/ (root)`.
4. The site goes live at https://shbzstrkr1999.github.io within a few minutes.

## Option 2: Netlify (drag and drop)
1. Go to app.netlify.com/drop.
2. Drag the `site/` folder onto the page. You get a URL straight away; rename it under Site settings.

## Option 3: Vercel
1. Install the CLI: `npm i -g vercel`.
2. From inside `site/`, run `vercel --prod` and accept the defaults (framework: Other, no build command).

## Make the contact form send mail
Without setup, the form opens the visitor's email app. To receive messages directly:
1. Create a free form at formspree.io and copy its endpoint URL.
2. In `index.html`, set `var FORM_ENDPOINT = 'https://formspree.io/f/xxxxxxxx';`.

## Before you publish
- The LectAI "View code" button points to your GitHub profile. Replace it with the repository URL once that repo is public.
- Tailwind loads from its CDN, which is fine for a personal site. For a faster build later, compile Tailwind with its CLI.
- To update your CV, replace the PDF with the same filename.
