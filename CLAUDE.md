# oh-my-claudecode Website

This is the marketing website for oh-my-claudecode plugin.

## Project Info

- **Live URL:** https://ohmyclaudecode.com
- **Source Repo:** https://github.com/Yeachan-Heo/oh-my-claudecode
- **GA4 Measurement ID:** G-DY1SMZBQT0

## Local Skills

### /update-website

Updates the website with latest oh-my-claudecode changes and curated resources.

**Usage:** Just say "update website" or "/update-website"

**What it does:**
1. Syncs changes from the main oh-my-claudecode repo
2. Searches for new articles, tutorials, and resources
3. Adds them to the Resources section with proper styling
4. Applies Google Analytics tracking to all new elements
5. Commits and deploys automatically

**Skill file:** `.claude/skills/update-website.md`

## Development Guidelines

### Adding Resources

Always include GA tracking:
```html
<a href="..."
   class="resource-card"
   data-ga-category="resource_click"
   data-ga-label="unique_label">
```

### Deploying

```bash
git add .
git commit -m "message"
git push origin main
```

GitHub Pages auto-deploys from main branch.

## Key Files

| File | Purpose |
|------|---------|
| `index.html` | Main website (single-page) |
| `CNAME` | Custom domain config |
| `GA_TRACKING_GUIDELINES.md` | GA implementation docs |
| `.claude/skills/` | Local skills for this project |
