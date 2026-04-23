# Claude Skills

A collection of 24+ bundled capabilities for automating business and content workflows. Each skill combines LLM instructions with deterministic scripts for reliable execution.

## Quick Start

### Prerequisites

- Python 3.10+
- Node.js 18+ and npm
- [Claude Code CLI](https://docs.anthropic.com/en/docs/claude-code) installed
- API keys (only add the ones you need):
  - `ANTHROPIC_API_KEY` — Required. Get from [console.anthropic.com](https://console.anthropic.com/)
  - `APIFY_API_TOKEN` — For lead scraping (optional)
  - `INSTANTLY_API_KEY` — For cold email campaigns (optional)
  - `PANDADOC_API_KEY` — For proposal generation (optional)
  - `OPENAI_API_KEY` — For embeddings in RAG (optional)
  - `PINECONE_API_KEY` — For vector search (optional)

### Installation

1. **Clone and install dependencies:**
   ```bash
   cd "Claude Skills"
   pip install -r requirements.txt
   npm install
   ```

2. **Configure environment variables:**
   ```bash
   cp .env.example .env
   ```
   Edit `.env` and add your API keys. Only required keys: `ANTHROPIC_API_KEY`

3. **Configure Gmail (optional):**
   ```bash
   cp gmail_accounts.json.example gmail_accounts.json
   ```
   - Create OAuth credentials in [Google Cloud Console](https://console.cloud.google.com/) (Desktop app type)
   - Download as `credentials.json`
   - Edit `gmail_accounts.json` with your email addresses and token paths
   - Run any Gmail skill once to complete OAuth

4. **Deploy to Modal (optional, for cloud webhooks):**
   ```bash
   modal deploy execution/modal_webhook.py
   ```
   Update webhook URLs in skill files with your Modal username.

5. **Start using Claude Code:**
   ```bash
   claude
   ```

## Skills Overview

### Lead Generation & Enrichment
- `scrape-leads` — Scrape and verify leads via Apify
- `gmaps-leads` — Google Maps B2B lead scraping
- `classify-leads` — LLM-based lead classification
- `casualize-names` — Convert names for personalization

### Email & Campaigns
- `instantly-campaigns` — Cold email campaigns with A/B testing
- `instantly-autoreply` — Intelligent auto-reply to emails
- `welcome-email` — Send welcome sequences
- `gmail-inbox` — Unified Gmail management

### Sales & Proposals
- `create-proposal` — Generate PandaDoc proposals
- `deep-research-pitch` — Research and pitch generation
- `upwork-apply` — Upwork job scraping and proposals

### Content & Video
- `video-edit` — Remove silences, add transitions
- `pan-3d-transition` — 3D swivel effects
- `recreate-thumbnails` — Face-swap thumbnails
- `cross-niche-outliers` — Find viral videos in adjacent niches
- `youtube-outliers` — Monitor for outlier videos
- `title-variants` — Generate YouTube title variations

### Community & Research
- `skool-monitor` — Monitor Skool communities
- `skool-rag` — Query Skool content via RAG
- `literature-research` — Academic database search

### Utilities
- `onboarding-kickoff` — Post-call automation
- `design-website` — Generate prospect mockups
- `generate-report` — Weather reports (example)
- `add-webhook` — Add Modal webhooks
- `modal-deploy` — Deploy to Modal
- `local-server` — Local orchestration

## Usage

Skills auto-activate based on your requests in Claude Code. Try examples:

```
"Scrape leads for marketing agencies in New York"
"Create a cold email campaign for SaaS companies"
"Find viral YouTube videos in the AI niche"
"Label my Gmail inbox"
```

## Architecture

**Three-layer system:**
1. **Skills** — Intent + execution bundled (`.claude/skills/`)
2. **Orchestration** — Your decision-making (routing, error handling)
3. **Shared Utilities** — Common scripts (`execution/`)

Each skill is self-contained with:
- `SKILL.md` — Instructions and workflows
- `scripts/` — Python/Node execution code

## Directory Structure

```
Claude Skills/
├── .claude/
│   ├── CLAUDE.md           # Full instructions
│   ├── skills/             # Skill definitions + scripts
│   ├── agents/             # Subagents (code-reviewer, qa, research)
│   └── settings.local.json # Local configuration
├── execution/              # Shared utilities
├── .env                    # API keys (not in git)
└── requirements.txt        # Python dependencies
```

## Self-Annealing Loop

When something breaks:
1. Read the error and stack trace
2. Fix the script
3. Test it again
4. Update SKILL.md with learnings
5. System is now stronger

## Support

See `.claude/CLAUDE.md` for full agent instructions and workflow details.
