# Google Analytics (GA4) Tracking Guidelines

This document outlines the Google Analytics implementation for the oh-my-claudecode website.

## Setup

**Measurement ID:** `G-DY1SMZBQT0`

The GA4 tracking code is loaded in the `<head>` section of `index.html`:

```html
<script async src="https://www.googletagmanager.com/gtag/js?id=G-DY1SMZBQT0"></script>
<script>
    window.dataLayer = window.dataLayer || [];
    function gtag(){dataLayer.push(arguments);}
    gtag('js', new Date());
    gtag('config', 'G-DY1SMZBQT0');
</script>
```

---

## Event Types

### 1. Resource Clicks (Outbound Links)

**Event Name:** `resource_click`

**Parameters:**
| Parameter | Description |
|-----------|-------------|
| `event_category` | Always `resource_click` |
| `event_label` | Unique identifier for the resource |
| `link_url` | Full URL of the clicked link |
| `link_text` | Text content of the link (truncated to 100 chars) |

**Implementation:**
Add `data-ga-category` and `data-ga-label` attributes to any clickable resource:

```html
<a href="https://example.com/article"
   class="resource-card"
   data-ga-category="resource_click"
   data-ga-label="unique_article_id">
   Article Title
</a>
```

**Current Labels:**
- `medium_joe_njenga` - Joe Njenga's Medium article
- `roboco_korean` - ROBOCO Korean analysis
- `medium_recep_sen` - Recep Şen's Medium guide
- `devto_beginners_tutorial` - DEV Community tutorial
- `builderio_tips` - Builder.io tips article
- `codewithmukesh_guide` - CodeWithMukesh guide
- `bearblog_experience` - Sankalp's experience blog
- `github_45_tips` - ykdojo's 45 tips repo
- `github_awesome_plugins` - Awesome Claude Plugins repo
- `firecrawl_top10` - Firecrawl top 10 plugins
- `github_claude_flow` - claude-flow project
- `gist_swarm_guide` - Swarm orchestration gist
- `paddo_hidden_swarm` - Hidden multi-agent system article
- `hackernews_swarm` - Hacker News discussion
- `theunwindai_multiagent` - The Unwind AI multi-agent article
- `medium_piercelamb` - Pierce Lamb's plugin development article
- `aibit_multiagent` - AIBit multi-agent automation article
- `roboco_comparison` - ROBOCO enterprise comparison (Korean)
- `shipyard_multiagent` - Shipyard multi-agent orchestration guide
- `skywork_largecodebase` - Skywork AI large codebase best practices
- `medium_clairebluepark_migration` - OpenCode to OMC migration (Korean)
- `vibesparking_steroids` - Vibe Sparking AI review
- `eeselai_multiagent_guide` - eesel.ai complete multi-agent guide
- `github_awesomeccplugins` - ccplugins/awesome-claude-code-plugins
- `github_awesomeclaudecode` - hesreallyhim/awesome-claude-code
- `github_wshobson_agents` - wshobson/agents framework
- `github_claudeorchestration` - mbruhler/claude-orchestration
- `official_reference_docs` - Official reference documentation
- `official_changelog` - Official changelog
- `official_releases` - Official releases page
- `addyosmani_swarms` - Addy Osmani's Claude Code Swarms article
- `zenvanriel_swarms` - Zen van Riel's multi-agent AI coding article
- `datanorth_guide` - DataNorth complete Claude Code guide

---

### 2. Section Impressions (Visibility Tracking)

**Event Name:** `section_view`

**Parameters:**
| Parameter | Description |
|-----------|-------------|
| `event_category` | Always `engagement` |
| `event_label` | Section ID |
| `section_id` | HTML ID of the section |
| `section_name` | Human-readable section name |

**Tracked Sections:**
| Section ID | Section Name |
|------------|--------------|
| `install` | Quick Start |
| `features` | Execution Modes |
| `agents` | Specialized Agents |
| `resources` | Resources & Articles |
| `faq` | FAQ |

**Implementation:**
Automatically tracked for all `<section>` elements with an `id` attribute. Triggered when 30% of the section is visible. Each section is only tracked once per page load.

---

### 3. CTA Button Clicks

**Event Name:** `cta_click`

**Parameters:**
| Parameter | Description |
|-----------|-------------|
| `event_category` | Always `cta` |
| `event_label` | `github_link` or `get_started` |
| `button_text` | Text content of the button |
| `destination` | URL destination |

**Automatically Tracked:**
- All links to `#install` (Get Started buttons)
- All links to `github.com` (GitHub buttons)

---

### 4. Copy Actions

**Event Name:** `copy_code`

**Parameters:**
| Parameter | Description |
|-----------|-------------|
| `event_category` | Always `engagement` |
| `event_label` | `install_command`, `setup_command`, or `example_code` |
| `code_snippet` | First 100 characters of copied code |

**Tracked Automatically:**
When users click copy buttons on code blocks.

---

### 5. Navigation Clicks

**Event Name:** `navigation_click`

**Parameters:**
| Parameter | Description |
|-----------|-------------|
| `event_category` | Always `navigation` |
| `event_label` | Link text |
| `link_type` | `internal` or `external` |
| `destination` | URL destination |

**Tracked Automatically:**
All links within the `<nav>` element.

---

### 6. FAQ Interactions

**Event Name:** `faq_expand`

**Parameters:**
| Parameter | Description |
|-----------|-------------|
| `event_category` | Always `engagement` |
| `event_label` | First 50 chars of question |
| `faq_question` | Full question text |

**Tracked Automatically:**
When users expand FAQ accordion items.

---

### 7. Scroll Depth

**Event Name:** `scroll_depth`

**Parameters:**
| Parameter | Description |
|-----------|-------------|
| `event_category` | Always `engagement` |
| `event_label` | `25%`, `50%`, `75%`, or `100%` |
| `percent_scrolled` | Numeric percentage (25, 50, 75, 100) |

**Milestones:** 25%, 50%, 75%, 100%

---

### 8. Time on Page

**Event Name:** `time_on_page`

**Parameters:**
| Parameter | Description |
|-----------|-------------|
| `event_category` | Always `engagement` |
| `event_label` | `30s`, `60s`, `120s`, or `300s` |
| `seconds_on_page` | Numeric seconds |

**Milestones:** 30s, 60s, 120s (2 min), 300s (5 min)

---

## Adding New Tracking

### For New Resource Cards

```html
<a href="https://new-resource.com"
   target="_blank"
   class="resource-card"
   data-ga-category="resource_click"
   data-ga-label="descriptive_unique_label">
   Resource Title
</a>
```

### For New Sections

Simply add an `id` attribute to the section:

```html
<section id="new-section" class="py-20 px-4">
    <!-- Content -->
</section>
```

Then update the `sectionNames` object in JavaScript:

```javascript
const sectionNames = {
    // ... existing sections
    'new-section': 'New Section Name'
};
```

### For Custom Events

Use the `trackEvent` helper function:

```javascript
trackEvent('custom_event_name', {
    event_category: 'category',
    event_label: 'label',
    custom_param: 'value'
});
```

---

## GA4 Reports to Monitor

1. **Realtime** - Live visitor activity
2. **Engagement > Events** - All custom events
3. **Engagement > Pages and screens** - Page views
4. **Acquisition > Traffic acquisition** - Traffic sources
5. **User > Demographics** - User location and devices

---

## Best Practices

1. **Unique Labels:** Always use unique, descriptive labels for tracking
2. **Consistent Categories:** Use existing categories when possible
3. **No PII:** Never track personally identifiable information
4. **Test First:** Verify events in GA4 DebugView before deploying
5. **Document Changes:** Update this file when adding new tracking

---

## Debugging

Enable GA4 DebugView:
1. Install [Google Analytics Debugger](https://chrome.google.com/webstore/detail/google-analytics-debugger/jnkmfdileelhofjcijamephohjechhna) Chrome extension
2. Enable the extension
3. Open GA4 > Configure > DebugView
4. Interact with the site to see events in real-time

Or add `?debug_mode=true` to the URL.

---

## Contact

For questions about analytics implementation, contact the repository maintainers.
