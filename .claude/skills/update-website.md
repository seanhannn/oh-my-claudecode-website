# update-website

Update oh-my-claudecode website with latest changes and resources.

## Metadata

- **name**: update-website
- **description**: Sync oh-my-claudecode repo changes and curate latest resources for the website
- **keywords**: website, update, sync, resources, omc, oh-my-claudecode
- **author**: seanhan

## Trigger Patterns

- "update omc website"
- "sync omc website"
- "update oh-my-claudecode website"
- "웹사이트 업데이트"
- "사이트 업데이트"

## Instructions

You are a website maintainer for oh-my-claudecode-website. Your job is to keep the site fresh with the latest information.

### Step 1: Sync Repository Changes

1. **Fetch latest from oh-my-claudecode repo:**
   ```
   WebFetch https://github.com/Yeachan-Heo/oh-my-claudecode
   ```

2. **Check for updates:**
   - Review CHANGELOG.md for new versions
   - Check for new features, agents, or skills
   - Note any breaking changes or deprecations

3. **Update website sections:**
   - Hero section: Update version badge if new release
   - Stats: Update agent/skill counts if changed
   - Features: Add new execution modes
   - Agents table: Add new agents
   - Keywords: Add new magic keywords

### Step 2: Search for New Resources

1. **Search the internet for fresh content:**
   ```
   WebSearch "oh-my-claudecode" tutorial article blog 2026
   WebSearch "oh-my-claudecode" review tips use case
   WebSearch "claude code" multi-agent orchestration swarm
   WebSearch "claude code plugins" best practices 2026
   ```

2. **Evaluate resources for quality:**
   - Must be relevant to oh-my-claudecode or Claude Code plugins
   - Prioritize recent content (2025-2026)
   - Include diverse sources (Medium, DEV, GitHub, blogs)
   - Check for Korean/international content

3. **Categorize new resources:**
   - Featured Articles (in-depth reviews, tutorials)
   - Tutorials & Guides (how-to content)
   - Community Resources (GitHub repos, tools)
   - Related Projects (complementary tools)

### Step 3: Update Website

1. **Navigate to website directory:**
   ```
   cd /Users/seanhan/Development/ai/oh-my-claudecode-website
   ```

2. **Read current index.html:**
   ```
   Read index.html
   ```

3. **Add new resources to Resources section:**
   - Use card layout for featured articles
   - Use list layout for tutorials
   - Include proper GA tracking attributes

4. **GA Tracking Requirements (CRITICAL):**

   Every new clickable element MUST have:
   ```html
   <a href="..."
      class="resource-card"
      data-ga-category="resource_click"
      data-ga-label="unique_descriptive_label">
   ```

   Label naming convention:
   - `{source}_{author}` for articles (e.g., `medium_joe_njenga`)
   - `{source}_{topic}` for tutorials (e.g., `devto_beginners_tutorial`)
   - `github_{repo_name}` for GitHub repos

5. **Update GA_TRACKING_GUIDELINES.md:**
   - Add new labels to documentation
   - Document any new event types

### Step 4: Verify & Deploy

1. **Verify changes:**
   - Check HTML syntax
   - Verify all links work
   - Confirm GA attributes are present

2. **Commit with descriptive message:**
   ```bash
   git add index.html GA_TRACKING_GUIDELINES.md
   git commit -m "Update website with latest resources and features

   - [List specific changes]
   - Add new resources: [list sources]
   - Update [sections modified]

   Co-Authored-By: Claude Opus 4.5 <noreply@anthropic.com>"
   ```

3. **Push to deploy:**
   ```bash
   git push origin main
   ```

4. **Confirm deployment:**
   - Site URL: https://ohmyclaudecode.com
   - GitHub Pages auto-deploys in 1-2 minutes

### Card Templates

**Featured Article Card:**
```html
<a href="URL" target="_blank"
   class="resource-card feature-card bg-dark-card border border-dark-border rounded-xl p-6 group"
   data-ga-category="resource_click" data-ga-label="UNIQUE_LABEL">
    <div class="flex items-center gap-2 mb-3">
        <span class="px-2 py-1 text-xs bg-accent-green/10 text-accent-green rounded">SOURCE</span>
        <span class="text-xs text-gray-500">DATE</span>
    </div>
    <h4 class="font-bold text-lg mb-2 group-hover:text-accent-red transition-colors">TITLE</h4>
    <p class="text-gray-400 text-sm mb-4">DESCRIPTION</p>
    <div class="flex items-center gap-2 text-sm text-gray-500">
        <span>By AUTHOR</span>
        <span class="text-accent-red group-hover:translate-x-1 transition-transform">→</span>
    </div>
</a>
```

**Tutorial List Item:**
```html
<a href="URL" target="_blank"
   class="resource-card flex items-center gap-4 bg-dark-card border border-dark-border rounded-xl p-4 hover:border-accent-blue/50 transition-colors group"
   data-ga-category="resource_click" data-ga-label="UNIQUE_LABEL">
    <div class="w-12 h-12 bg-accent-blue/10 rounded-lg flex items-center justify-center text-xl shrink-0">EMOJI</div>
    <div class="flex-grow min-w-0">
        <h4 class="font-semibold group-hover:text-accent-blue transition-colors truncate">TITLE</h4>
        <p class="text-sm text-gray-500">SOURCE • DESCRIPTION</p>
    </div>
    <span class="text-accent-blue opacity-0 group-hover:opacity-100 transition-opacity">→</span>
</a>
```

**Community Resource Card:**
```html
<a href="URL" target="_blank"
   class="resource-card bg-gradient-to-br from-dark-card to-dark-hover border border-dark-border rounded-xl p-5 hover:border-accent-pink/50 transition-all group"
   data-ga-category="resource_click" data-ga-label="UNIQUE_LABEL">
    <div class="flex items-center gap-3 mb-3">
        <svg class="w-6 h-6 text-gray-400" fill="currentColor" viewBox="0 0 24 24"><!-- GitHub icon --></svg>
        <span class="font-bold text-white group-hover:text-accent-pink transition-colors">TITLE</span>
    </div>
    <p class="text-sm text-gray-400 mb-3">DESCRIPTION</p>
    <span class="text-xs text-accent-pink">REPO_NAME</span>
</a>
```

### Important Notes

- ALWAYS apply GA tracking to new elements
- ALWAYS update GA_TRACKING_GUIDELINES.md when adding new labels
- ALWAYS commit and push to deploy
- Check for duplicate resources before adding
- Prioritize quality over quantity
- Keep the design consistent with existing cards
