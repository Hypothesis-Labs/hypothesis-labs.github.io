# Deploy Hypothesis Labs — Go Live Today

## What you have
```
hypothesis-labs-site/
├── index.html                        ← landing page
├── style.css                         ← shared styles (don't delete)
├── favicon.svg
├── experiments/
│   └── org-hierarchy.html            ← first experiment write-up
└── media/                            ← put your images/GIFs here
```

---

## Step 1 — Create the GitHub repo

1. Go to github.com → New repository
2. Name it `hypothesis-labs` (or anything you want)
3. Set to **Public**
4. Do NOT initialize with README (you'll push your own files)

---

## Step 2 — Push the files

Open Terminal in the `hypothesis-labs-site/` folder:

```bash
git init
git add .
git commit -m "Initial launch"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/hypothesis-labs.git
git push -u origin main
```

---

## Step 3 — Enable GitHub Pages

1. Go to your repo on GitHub
2. Settings → Pages (left sidebar)
3. Source: **Deploy from a branch**
4. Branch: `main` / `/ (root)`
5. Click Save

GitHub will give you a URL like `https://yourusername.github.io/hypothesis-labs/`
It takes about 60 seconds to go live.

---

## Step 4 — Connect your Squarespace domain

In Squarespace:
1. Domains → click your domain → DNS Settings
2. Add a CNAME record:
   - Host: `www`
   - Points to: `yourusername.github.io`
3. For the apex domain (no www), add 4 A records pointing to GitHub's IPs:
   ```
   185.199.108.153
   185.199.109.153
   185.199.110.153
   185.199.111.153
   ```

In GitHub:
1. Repo Settings → Pages → Custom domain
2. Enter your domain (e.g. `hypothesislabs.com`)
3. Check "Enforce HTTPS" once it propagates (can take up to 24hrs)

Full guide: https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site

---

## Adding a new experiment

1. Duplicate `experiments/org-hierarchy.html`
2. Rename it (e.g. `experiments/info-asymmetry.html`)
3. Edit the content — title, lede, meta sidebar, write-up body
4. Add a new card in `index.html` pointing to the new file
5. `git add . && git commit -m "Add new experiment" && git push`

Done. Live in ~30 seconds.

---

## Adding media

Drop files into the `media/` folder and reference them in your experiment HTML:

```html
<!-- Full-width image -->
<div class="media-full">
  <img src="../media/your-image.png" alt="Description" />
  <div class="media-caption">Caption text</div>
</div>

<!-- Side-by-side -->
<div class="media-grid">
  <div><img src="../media/a.png" alt="" /><div class="media-caption">Left</div></div>
  <div><img src="../media/b.gif" alt="" /><div class="media-caption">Right</div></div>
</div>

<!-- GIF (constrained) -->
<div class="media-inline">
  <img src="../media/your.gif" alt="" />
</div>

<!-- Video embed -->
<div class="media-video">
  <iframe src="https://www.youtube.com/embed/VIDEO_ID" allowfullscreen></iframe>
</div>

<!-- Callout box -->
<div class="callout">
  <div class="callout-label">Note</div>
  <p>Your callout text.</p>
</div>
```

---

## Linking to external interactive demos

For experiments that have a live simulation (on Vercel, HuggingFace, etc.),
add a launch button at the top of the experiment page:

```html
<a href="https://your-demo.vercel.app" class="btn btn-primary" target="_blank">
  Launch Simulation ↗
</a>
```
