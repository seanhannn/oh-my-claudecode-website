# Google Analytics (GA4) Tracking Guidelines

This document outlines the Google Analytics implementation for the oh-my-claudecode website.

## 🆕 2026-05-04 v4.13.5 + Resource Refresh

**Version bump**: v4.13.1 → **v4.13.5** (HUD Stability & Ralph PRD Fixes)
**Star count**: 30,300 → **32,400**

### New Resource Labels (5 added, 108 total hidden articles)
- `andrewooo_omc_review` — andrew.ooo OMC multi-agent review (Apr 2026)
- `codex_danielvaughan_ecosystem` — Daniel Vaughan multi-agent ecosystem (Apr 2026)
- `mejba_top10_skills_plugins` — Engr Mejba Ahmed top 10 plugins/skills/CLIs (2026)
- `redwerk_best_plugins` — Redwerk 7 best Claude Code plugins (2026)
- `firecrawl_top10_plugins` — Firecrawl top 10 Claude Code plugins (2026)

---

## 🆕 2026-04-21 README Alignment Update

**Version bump**: v4.13.0 → **v4.13.1** (Cursor IDE Support & Bug Fixes)
**Star count**: 30,100 → **30,300**

### Mode Tab Label Change (⚠️ breaks historical data)
- `mode_tab_ultrapilot` → **`mode_tab_ultrawork`**
  - Reason: Ultrapilot is deprecated per README. Ultrawork is the correct parallel mode.
  - GA4 reports for Ultrapilot will stop; new `mode_tab_ultrawork` event replaces it.

### New Resource Labels (4 added, 103 total hidden articles)
- `youtube_joe_njenga_howto` — How to Use OMC Properly (YouTube video)
- `github_techdufus_ultrawork` — TechDufus/oh-my-claude ultrawork prompts
- `github_frankbria_ralph` — frankbria/ralph-claude-code Ralph loop
- `github_zephyrpersonal_ultrawork` — zephyrpersonal Ultrawork fork

### Syntax corrections (not GA, but noted for copy_code tracking)
- `/team 3 "..."` → `/team 3:executor "..."` (role suffix required)
- `/oh-my-claudecode:omc-setup` → `/omc-setup` (shorter form per README)

---

## 🆕 2026-04-20 Redesign: New Event Taxonomy

The v2 site introduces rich engagement tracking across all sections. **143 GA data points** (up from 108).

### New Event Categories
| Category | Fires On | Use For |
|----------|----------|---------|
| `cta_click` | Hero/Final/Nav CTAs | Conversion funnel |
| `testimonial_click` | Community quote cards | Social proof impact |
| `mode_tab_click` | Autopilot/Ultrapilot/Team/Ralph tabs | Feature interest |
| `copy_code` | Install step copy buttons | Install intent |
| `section_view` | Section visibility (once/session) | Content engagement |
| `scroll_depth` | 25/50/75/100% milestones | Page depth |
| `time_on_page` | 30/60/120/300s milestones | Dwell time |
| `faq_expand` | FAQ item opens | Question interest |
| `terminal_demo_complete` | Hero terminal cycle completes | Hero engagement |
| `show_more_articles` | Expand 99 hidden resources | Deep interest |
| `engagement` | Miscellaneous interactions | Granular tracking |

### Key Conversion Labels (Watch These!)
- `hero_cta_install` — Primary hero CTA (top of funnel)
- `hero_cta_github` — Secondary hero CTA (star the repo)
- `nav_install` — Sticky nav install button
- `nav_github_stars` — Nav star counter click
- `final_cta_install` — Bottom of page install CTA
- `final_cta_github` — Bottom of page GitHub CTA
- `install_step_1` / `install_step_2` / `install_step_3` — Copy buttons per step
- `mode_tab_autopilot` / `mode_tab_ultrapilot` / `mode_tab_team` / `mode_tab_ralph` — Which mode users explore
- `testimonial_joe_njenga` / `testimonial_addy_osmani` / `testimonial_alex_kerber` — Testimonial drives
- `show_more_articles_button` — Resources deep dive

### Funnel to watch in GA4 Reports
1. `section_view:install` impressions
2. `copy_code:install_step_1` (intent signal)
3. `cta_click:final_cta_install` (final push)
4. Outbound to GitHub (star conversion)

---



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
- `sonim1_legal_doping` - Sonim1 "Legal Doping for Claude Code" practical guide
- `rosmur_best_practices` - Claude Code Best Practices community guide
- `medium_piercelamb_trilogy` - Pierce Lamb's Deep Trilogy plugins article
- `medium_vinay_chatbox` - Vinay Bhaskarla's non-technical Claude Code guide
- `hackceleration_review` - Hackceleration Claude Code 2026 review
- `devgenius_plugin_stack` - JP Caparas plugin starter stack for web devs
- `datacamp_build_plugins` - DataCamp step-by-step plugin building guide
- `wasp_fullstack_essentials` - Wasp fullstack development essentials
- `medium_benyamin_codereview` - Benyamin Salimi's interactive code review
- `claudepluginsdev_registry` - Claude Plugins community registry
- `github_shanraisshan_bestpractice` - shanraisshan/claude-code-best-practice
- `claudecoderun_agentrooms` - Claude Code Agentrooms workspace
- `github_claudecodebyagents` - baryhuang/claude-code-by-agents
- `lenny_claude_code` - Lenny Rachitsky's "Everyone should be using Claude Code more"
- `oreilly_auto_review` - O'Reilly Radar auto-reviewing Claude's code
- `creatorsai_practical_tips` - The Creator's AI practical plugin & swarm tips
- `alexop_tasks_to_swarms` - alexop.dev agent teams coordination patterns
- `perrotta_swarm_mode` - perrotta.dev swarm mode deep dive
- `official_agent_teams_docs` - Official Anthropic agent teams documentation
- `github_ohmyclaude_dotnet` - stefandevo/oh-my-claude .NET port
- `composio_top_plugins` - Composio top 10 Claude Code plugins ranking
- `prismic_claude_code` - Prismic "Why Claude Code Changed My Mind"
- `apiyi_swarm_guide` - Apiyi.com Claude Swarm Mode complete guide
- `atcyrus_swarm_explained` - Cyrus Claude Code swarm feature explainer
- `github_wesammustafa_guide` - wesammustafa/Claude-Code-Everything-You-Need-to-Know
- `jeongil_agent_ecosystem` - Jeongil Jeong's AI coding agent ecosystem article
- `brightcoding_plugins_plus` - BrightCoding 270+ Claude Code plugins directory
- `boristane_howto` - Boris Tane's "How I Use Claude Code" guide
- `codingnexus_swarms` - Coding Nexus multi-agent teams article
- `claudefast_agent_teams` - ClaudeFast agent teams complete guide
- `medium_darasoba_teams` - Dára Sobaloju agent teams setup guide
- `producttalk_features` - Product Talk Claude Code features guide
- `theneuron_guide` - The Neuron's complete Claude Code beginner-to-power-user guide
- `official_subagents_docs` - Official Claude Code custom subagents documentation
- `vscode_multiagent` - VS Code multi-agent development blog post
- `anthropic_c_compiler` - Anthropic engineering building a C compiler with Claude Code
- `medium_kargar_agent_sdk` - Isaac Kargar agent teams with Claude Agent SDK
- `marc0_agent_teams` - marc0.dev practical agent teams setup guide
- `anthropic_security` - Anthropic official security best practices documentation
- `aitoolanalysis_plugins_review` - AI Tool Analysis 9,000+ plugins comprehensive review
- `cuttlesoft_macos_teams` - Cuttlesoft macOS agent teams setup guide
- `devto_opencode_teams` - Ugo Enyioha porting agent teams to OpenCode
- `devto_oikon_changelog` - oikon's Claude Code CHANGELOG reflections
- `github_quemsah_metrics` - quemsah/awesome-claude-plugins adoption metrics
- `devto_felixchan_plugin_teams` - FelixChan building plugins for agent teams
- `geekygadgets_50tips` - Geeky Gadgets 50 Claude Code tips and tricks
- `sshh_every_feature` - Shrivu Shankar using every Claude Code feature
- `jangwook_openclaw_teams` - Jangwook Lee agent teams with OpenClaw guide
- `byteiota_swarms_discovered` - ByteIota hidden multi-agent swarms feature
- `github_ruflo_orchestration` - ruflo enterprise agent orchestration platform
- `adambernard_swarm_orchestration` - Adam Bernard's OMC agent swarm orchestration guide
- `sitepoint_agent_teams` - SitePoint agent teams setup guide
- `medium_cobusgreyling_teams` - Cobus Greyling's agent teams article
- `turingcollege_agent_teams` - Turing College agent teams guide
- `anthropic_plugins_blog` - Official Anthropic plugins blog post
- `freekdev_claude_setup` - Freek Van der Herten's Claude Code setup
- `github_claudeswarm_hackathon` - affaan-m/claude-swarm hackathon project
- `deepakkarkala_omc_guide` - Deepak Karkala's comprehensive oh-my-claudecode framework guide
- `medium_danavila_teams` - Daniel Avila's agent teams in Claude Code article
- `medium_habib_teams` - Michael Habib's experience trying Claude Code Teams
- `github_bruniaux_ultimate_guide` - FlorianBruniaux/claude-code-ultimate-guide
- `lobehub_omc_setup` - OMC omc-setup skill on LobeHub Skills Marketplace
- `medium_leogodin_great` - Leo Godin's "Claude Code is Great" practical guide
- `rockcyber_zerg_orchestration` - Rock Cyber Musings parallel orchestration deep dive
- `scottspence_swarm_unlock` - Scott Spence's swarm mode unlock guide
- `similarlabs_tutorial_guide` - SimilarLabs ultimate Claude Code tutorial 2026
- `anthropic_code_review_blog` - Anthropic official Code Review launch blog post
- `techcrunch_code_review` - TechCrunch coverage of Claude Code Review launch
- `thenewstack_code_review` - The New Stack multi-agent code review deep-dive
- `aicorner_code_review` - The AI Corner analysis of Code Review capabilities
- `claudeworld_complete_guide` - ClaudeWorld "From Zero to Hero" complete guide 2026
- `devto_umesh_code_review` - Umesh Malik's Code Review setup & pricing guide
- `thesys_code_review` - Thesys Code Review features, pricing & setup guide
- `uxplanet_top7_plugins` - UX Planet top 7 Claude Code plugins (Nick Babich)
- `analyticsvidhya_claude_flow` - Analytics Vidhya Claude Flow orchestration framework
- `turbodocx_best_plugins` - TurboDocx best plugins, skills & MCP servers directory
- `dataconomy_code_review` - Dataconomy AI-powered Code Review launch coverage
- `nxcode_beginners_guide` - NxCode Claude Code beginner tutorial 2026
- `nxcode_agent_teams` - NxCode Opus 4.6 agent teams parallel setup guide
- `serenitiesai_agent_teams` - Serenities AI agent teams documentation
- `github_workflow_orchestration` - barkain/claude-code-workflow-orchestration plugin
- `substack_karozieminski_cowork` - Karo Zieminski's 50+ tested tips on plugins, skills & memory
- `medium_unicodeveloper_skills` - unicodeveloper's 10 must-have skills for Claude
- `sabrinadev_concepts_explained` - sabrina.dev's Claude Code concepts for beginners
- `geekygadgets_cli_plugins` - Geeky Gadgets 10 CLI plugins for workflows
- `atalupadhyay_ultimate_guide` - Atal Upadhyay's ultimate Claude Code 2.0 guide
- `mindwiredai_essential_skills` - MindWired AI 5 must-know Claude Code skills
- `paddo_one_year` - paddo.dev one year of Claude Code retrospective
- `devto_chand1012_agentic` - DEV Community best way to do agentic development in 2026
- `devto_claude_vs_codex` - DEV Community Claude Code vs Codex 2026 Reddit survey
- `github_plugins_plus_skills` - jeremylongshore/claude-code-plugins-plus-skills marketplace
- `github_shinpr_workflows` - shinpr/claude-code-workflows production workflows
- `hackernews_sisyphus` - HN discussion "Sisyphus Now Lives in Oh My Claude"
- `claudedirectory_best_plugins` - Claude Directory best plugins for every stack ranking
- `github_cmux` - craigsc/cmux tmux-based worktree manager for Claude Code
- `github_ohmyopenagent` - code-yeongyu/oh-my-openagent universal agent harness
- `github_manaflow_cmux` - manaflow-ai/cmux native macOS terminal for AI agents
- `github_matrixy_swarm` - MaTriXy/claude-swarm-orchestration TeammateTool patterns
- `medium_heeki_teams` - Heeki Park's collaborating with agent teams in Claude Code
- `novaglio_agent_teams` - Claudio Novaglio's agent teams multi-agent orchestration paper
- `maecapozzi_orchestrator` - Mae Capozzi's building a multi-agent AI system with Claude Code
- `medium_kapil_workspace` - CodeToDeploy "Claude Code Stopped Being a Tool and Became the Workspace"
- `medium_joe_code_review` - Joe Njenga's Claude Code Review workflow article
- `medium_mohit_opencode_block` - Mohit Aggarwal's Claude Code vs OpenCode January 2026 block analysis
- `devto_jandedobbeleer_posh` - Oh My Posh ❤️ Claude Code integration guide
- `medium_tihomir_simplify` - Tihomir Manushev's /simplify skill replaces self-review article
- `github_composio_awesome_skills` - ComposioHQ/awesome-claude-skills curated skills list
- `github_alirezarezvani_skills` - alirezarezvani/claude-skills personal skills collection
- `devto_tessak_laravel_overnight` - Laravel backend rebuild overnight with 18 parallel multi-agents
- `devto_matkarimov_12_subagents` - How to split Claude Code into 12 specialized sub-agents for React
- `devto_tsekatm_agent_memory` - Layered markdown memory architecture for multi-agent systems
- `medium_alirezarezvani_teams_leap` - From subagents to agent teams: Claude Code's multi-agent leap
- `devto_plugin_agent_teams_service` - Building a plugin and service for Claude Code agent teams
- `substack_johnkim_30tips` - John Kim's 30 tips for Claude Code agent teams
- `seankim_teammode_march2026` - Sean Kim's TeammateTool and swarm mode March 2026 update
- `pillitteri_march2026_updates` - Pasquale Pillitteri's Claude Code March 2026 all updates roundup
- `byteiota_omc_review` - ByteIota review: oh-my-claudecode trending #1 on GitHub, 3-5x speedup
- `aitoolly_omc_teams` - AIToolly: oh-my-claudecode multi-agent orchestration for teams (Mar 29, 2026)
- `shipyard_multiagent_2026` - Shipyard: multi-agent orchestration for Claude Code in 2026 (Mar 18, 2026)
- `aitoolly_multiagent_teams` - AIToolly: oh-my-claudecode new multi-agent orchestration tool for team collaboration (Mar 29, 2026)
- `devto_raxxo_best_plugins` - DEV Community (Raxxo Studios): Best Claude Code Skills & Plugins 2026 Guide
- `medium_guljabeen_top10` - Medium (Gul Jabeen): Top 10 Claude Code Plugins That Actually Changed How I Build Software in 2026 (Feb 2026)
- `buildtolaunch_plugins_review` - Substack (Jenny Ouyang): Best Claude Code Plugins 2026 - 10 Tested 4 Worth Keeping (Mar 2026)
- `corpwaters_skills_guide` - Substack (Mikhail Shcheglov): The Ultimate Guide to Claude Code Skills (Mar 2026)
- `medium_joe_swarm_discovery` - Medium (Joe Njenga): I Discovered This Claude Code Agent Swarm Mode You Don't Know Exists (Jan 2026)
- `medium_joe_agent_teams` - Medium (Joe Njenga): I Tried New Claude Code Agent Teams And Discovered New Way to Swarm (Feb 2026)
- `medium_buzzgrewal_swarm` - Medium (Abdullah Grewal): I Gave My Code to a Swarm of AI Agents and Here's What Happened (Feb 2026)
- `aitoolly_team_solution` - AIToolly: Oh-My-ClaudeCode New Multi-Agent Orchestration Solution for Team-Based Workflows (Mar 31, 2026)
- `aitoolly_team_framework` - AIToolly: oh-my-claudecode Multi-Agent Orchestration Framework for Team-Based Claude Code (Apr 2, 2026)
- `medevel_omc_review` - MEDevel: oh-my-claudecode Review - Turn Claude Code Into a Coordinated Agent System
- `mindstudio_q1_roundup` - MindStudio: Claude Code Q1 2026 Update Roundup - Every Feature That Actually Matters
- `medevel_master_guide` - MEDevel (Hazem Abbas): Master Claude Code in 2026 Ultimate Guide featuring OMC
- `builderio_50tips` - Builder.io (Vishwas Gopinath): 50 Claude Code Tips and Best Practices For Daily Use
- `vibetip_omc_hub` - VibeTip: Oh My ClaudeCode community hub for multi-agent orchestration tips
- `emelia_omc_32agents` - Emelia.io: oh-my-claudecode turn Claude Code into a full 32-agent development team
- `freecodecamp_handbook` - freeCodeCamp: The Claude Code Handbook - Professional introduction to AI-assisted dev
- `sanity_staff_engineer_journey` - Sanity.io: First Attempt Will Be 95% Garbage - Staff engineer's 6-week Claude Code journey
- `aihero_real_engineers` - AI Hero (Apr 2026): Claude Code for Real Engineers cohort course featuring OMC workflows
- `devto_yukifuruta_gamechanger` - DEV Community (Yuki Furuta): oh-my-claudecode is a Game Changer — local AI swarm orchestration experience (Apr 2026)
- `medium_rickhightower_daily_os` - Medium (Rick Hightower): Claude Code 2026 as the daily operating system top developers use (Apr 2026)
- `selfmd_best_plugins` - self.md: Best Claude Code Plugins 2026 ranking featuring OMC as top orchestration pick
- `mcpmarket_omc_help_skill` - MCP Market: oh-my-claudecode interactive help skill and guide listing
- `scriptbyai_resource_list` - ScriptByAI: The Ultimate Claude Code Resource List 2026 Edition featuring OMC
- `htdocs_conductor_orchestrator` - htdocs.dev: From Conductor to Orchestrator practical multi-agent coding guide (Apr 2026)
- `claudefast_agent_teams_guide` - ClaudeFast: Claude Code Agent Teams setup & usage guide 2026
- `botmonster_agent_teams` - Botmonster Tech: orchestrating multiple AI sessions as agent teams
- `lushbinary_agent_teams` - Lushbinary: Claude Code Agent Teams multi-agent development guide
- `releasebot_april2026` - Releasebot: Claude Code April 2026 release notes auto-tracked changelog
- `gist_multiagent_system` - Kieran Klaassen gist: Claude Code Multi-Agent Orchestration System reference
- `devopsdaily_plugins_2026` - DevOps Daily: Best Claude Code plugins for DevOps engineers in 2026
- `agensi_marketplace_guide` - Agensi: Claude Code Plugin Marketplace complete guide 2026
- `openclawapi_32_agents` - OpenClaw API: oh-my-claudecode deployment & tips with 32 specialized agents (Mar 2026)
- `paulgp_researcher_setup` - Paul Goldsmith-Pinkham Substack: Getting Started with Claude Code researcher setup
- `specterops_secure_reviews` - SpecterOps: Leveling Up Secure Code Reviews with Claude Code (Mar 2026)
- `addyosmani_code_orchestra` - Addy Osmani: The Code Agent Orchestra multi-agent coding patterns (Mar 2026)
- `anthropic_managed_agents` - Anthropic Engineering: Scaling Managed Agents architecture deep-dive (2026)
- `alexkerber_korea_stars` - Alex Kerber: What +100K Stars in 24 Hours tells about AI Coding and OMC (Apr 2026)

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
