# ReadLog PM Discovery Portfolio

An AI-powered portfolio piece demonstrating three discovery workflows for the ReadLog reading journal app. Built by Molly Rankin.

---

## What This Is

A single-page interactive demo showing how a PM can use AI to:
1. **Mine competitor reviews** (Goodreads, StoryGraph) for unmet needs
2. **Build a continuous signal pipeline** (automated weekly digest)
3. **Translate insights into specs** (prioritized opportunity brief + feature drafts)

Includes a live "Try It Yourself" mode powered by Claude, with a 2-run-per-IP rate limit.

---

## Deploy to Netlify (Step by Step)

### 1. Create a GitHub repository

```bash
git init
git add .
git commit -m "Initial commit"
# Create a new repo on github.com, then:
git remote add origin https://github.com/YOUR_USERNAME/readlog-portfolio.git
git push -u origin main
```

### 2. Connect to Netlify

1. Go to [netlify.com](https://netlify.com) and log in
2. Click **Add new site → Import an existing project**
3. Choose **GitHub** and select your `readlog-portfolio` repo
4. Build settings:
   - **Build command:** leave blank
   - **Publish directory:** `.` (just a dot)
5. Click **Deploy site**

### 3. Add your API key

1. In Netlify, go to **Site configuration → Environment variables**
2. Click **Add a variable**
3. Key: `ANTHROPIC_API_KEY`
4. Value: your Anthropic API key (get one at console.anthropic.com)
5. Click **Save**
6. Trigger a redeploy: **Deploys → Trigger deploy → Deploy site**

### 4. Enable Netlify Blobs (for rate limiting)

Netlify Blobs is enabled automatically on any deployed site. No extra setup needed.

### 5. Link from Squarespace

Copy your Netlify URL (e.g. `https://readlog-portfolio-molly.netlify.app`) and:
- Add it as a button/link on your Squarespace portfolio page, **or**
- Embed it as an iframe using Squarespace's **Code Block** element:

```html
<iframe 
  src="https://YOUR-SITE.netlify.app" 
  width="100%" 
  height="800px" 
  frameborder="0"
  style="border-radius: 8px;">
</iframe>
```

---

## Project Structure

```
readlog-portfolio/
├── index.html                  # Main portfolio page (static)
├── netlify.toml                # Netlify config (functions, headers)
├── package.json                # Dependencies for Netlify functions
├── netlify/
│   └── functions/
│       └── analyze.js          # Claude API proxy + rate limiter
└── README.md
```

---

## Customization

- **Rate limit:** Change `MAX_RUNS` in `analyze.js` (currently 2 per IP per 24h)
- **Your name/contact:** Update references in `index.html` header and footer
- **Synthetic data:** All review examples in `index.html` are synthetic — replace with real data if available
- **API model:** Currently uses `claude-sonnet-4-20250514` — update in `analyze.js` if needed

---

## Cost Estimate

At 2 runs per visitor, ~1000 tokens per run, Claude Sonnet pricing:
- 100 visitors = ~200 API calls = under $1.00
- Safe for portfolio traffic with no spend controls needed

---

Built with Claude API · Hosted on Netlify · Linked from Squarespace
