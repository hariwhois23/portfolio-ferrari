# 🏎️ Ferrari F1 DevOps Portfolio

> **Engineering Speed. Automating Performance.**

A stunning, F1-inspired personal portfolio for DevOps & Cloud Engineers. Built with bold Ferrari aesthetics, racing telemetry UI, and smooth animations.

---

## ✨ Features

- 🚦 F1 Start Lights loading animation
- 🖱️ Custom red cursor with glow trail
- ⚡ Speed line background animations
- 🏎️ Embedded Ferrari SF-25 3D Sketchfab model
- 📊 Telemetry skill dashboard with animated progress bars
- 🔢 Animated stat counters
- 📍 Race progression timeline
- 🃏 Project cards with hover effects
- 🔺 Scroll reveal animations
- 📱 Fully responsive (mobile-first)
- 🎨 Pure Ferrari red/black/carbon fiber theme

---

## 🗂️ Project Structure

```
ferrari-portfolio/
├── index.html          # Complete single-file portfolio
├── README.md           # This file
└── assets/             # (optional) Add your own images/icons here
```

This is a **single-file HTML project** — no build tools, no dependencies, no npm install. Just open and deploy.

---

## 🛠️ Customization Checklist

Before deploying, update these in `index.html`:

| Location | What to Change |
|---|---|
| `<title>` tag | Your name |
| `hero-pretag` div | Your title |
| `.about-text` section | Your bio |
| `.stat-card` values | Your actual stats |
| `timeline` section | Your work history |
| `.project-card` sections | Your real projects |
| `contact-link` hrefs | Your email, GitHub, LinkedIn |
| `footer` | Your name |
| Hero ghost number `16` | Your favourite F1 number |

---

## 🚀 Deployment

### Option 1 — Vercel (Recommended)

```bash
# Install Vercel CLI
npm i -g vercel

# Deploy from project folder
cd ferrari-portfolio
vercel

# Follow prompts — it auto-detects static HTML
# Your site is live at: https://your-project.vercel.app
```

Or drag-and-drop the folder at **vercel.com/new** → "Import" → drop folder.

**Custom domain on Vercel:**
```
Settings → Domains → Add → yourdomain.com
```

---

### Option 2 — Netlify

```bash
# Install Netlify CLI
npm i -g netlify-cli

# Deploy
cd ferrari-portfolio
netlify deploy --prod --dir .
```

Or go to **app.netlify.com** → "Add new site" → "Deploy manually" → drag the folder.

---

### Option 3 — GitHub Pages

```bash
# Initialize git repo
git init
git add .
git commit -m "Initial portfolio commit"

# Push to GitHub
git remote add origin https://github.com/yourusername/portfolio.git
git push -u origin main

# Enable GitHub Pages:
# Repo Settings → Pages → Source: main branch / root
# Live at: https://yourusername.github.io/portfolio
```

---

### Option 4 — AWS S3 + CloudFront (The DevOps Way 🏆)

```bash
# Create S3 bucket
aws s3 mb s3://your-portfolio-bucket --region us-east-1

# Enable static website hosting
aws s3 website s3://your-portfolio-bucket \
  --index-document index.html \
  --error-document index.html

# Upload files
aws s3 sync . s3://your-portfolio-bucket \
  --exclude ".git/*" \
  --exclude "README.md" \
  --acl public-read

# (Optional) Create CloudFront distribution for HTTPS + CDN
# Use AWS Console or Terraform module below
```

**Terraform for S3 + CloudFront:**
```hcl
module "portfolio" {
  source  = "terraform-aws-modules/s3-bucket/aws"
  bucket  = "your-portfolio-bucket"
  
  website = {
    index_document = "index.html"
  }
}
# Then attach a CloudFront distribution with ACM SSL cert
```

---

## 🐳 Local Development

No build step needed. Just open in browser:

```bash
# Option A — Python server
python3 -m http.server 8080
open http://localhost:8080

# Option B — Node.js
npx serve .
open http://localhost:3000

# Option C — Just open the file
open index.html
```

---

## 🎨 Theming

Core colors defined in CSS custom properties at the top of `index.html`:

```css
:root {
  --red: #DC0000;          /* Ferrari Red */
  --red-bright: #FF1801;   /* Bright race red */
  --red-dim: #8B0000;      /* Deep red */
  --black: #0A0A0A;        /* Background */
  --black-card: #161616;   /* Card surfaces */
  --silver: #C0C0C0;       /* Metallic accents */
  --gold: #C8A84B;         /* Gold accents */
}
```

---

## 📋 SEO Checklist

- [x] `<title>` tag
- [x] `<meta name="description">`
- [x] `<meta name="keywords">`
- [x] Open Graph tags (`og:title`, `og:description`, `og:type`)
- [ ] Add `og:image` with a screenshot of your portfolio
- [ ] Add `<link rel="canonical" href="https://yourdomain.com">`
- [ ] Add Google Analytics / Plausible script

---

## 🏁 Lighthouse Scores (Expected)

| Metric | Score |
|---|---|
| Performance | 95+ |
| Accessibility | 88+ |
| Best Practices | 95+ |
| SEO | 92+ |

*Single HTML file = minimal render-blocking resources*

---

## 🔧 Optional Enhancements

### Add real sound (engine rev on load)
```html
<!-- Add after <body> -->
<audio id="engineRev" preload="auto">
  <source src="assets/engine-rev.mp3" type="audio/mpeg" />
</audio>
<script>
  // Play after loader completes
  setTimeout(() => {
    document.getElementById('engineRev').play().catch(() => {});
  }, 2500);
</script>
```

### Add Three.js particle field
```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
<!-- Then initialize a particle system in the hero section -->
```

### Connect contact form (Formspree)
```html
<!-- Replace the email link with: -->
<form action="https://formspree.io/f/YOUR_ID" method="POST">
  <input name="email" type="email" placeholder="Your email" required />
  <textarea name="message" placeholder="Message" required></textarea>
  <button type="submit" class="btn btn-primary">Send</button>
</form>
```

---

## 📝 License

MIT — Build fast, deploy faster. Forza Ferrari! 🏎️
