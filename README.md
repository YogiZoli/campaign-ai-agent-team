# Campaign AI Agent Team

A 4-agent AI campaign system for building complete marketing campaigns — from Click Sequence to PLF Launch — with isolated per-domain folder structures that support parallel multi-client management.

## The Team

| Agent | Role | Key Trigger Phrases |
|-------|------|---------------------|
| **Campaign Manager** | Language selection, domain setup, folder structure | "set up domain", "new client", "switch domain", "start campaign" |
| **Copy Agent** | All text: emails, landing pages, lead magnets, PLC, survey, webinar | "write the emails", "landing page copy", "PLC 1", "email sequence" |
| **Design Agent** | Canva briefs for all visual assets | "design brief", "thumbnail", "slide deck", "landing page design" |
| **Campaign Logic Agent** | Sequence maps, tag logic, automation blueprints | "campaign logic", "workflow", "tag structure", "sequence map" |
| **Video Script Agent** | Scripts (YouTube/VSL/PLC/Short-form) + HeyGen/Vento briefs + thumbnail handoff | "write the script", "YouTube script", "VSL", "PLC script" |

## Campaign Structure

Every domain is fully isolated — multiple clients never cross-contaminate:

```
campaigns/
├── _active_domain.md         ← which domain + language is currently active
└── ZoltanGero/               ← one folder per domain/client
    ├── _config.md            ← ICP, Offer, Hero Story (fill LATER)
    ├── _active_campaign.md   ← current campaign tracker
    ├── 01_Onboarding_Flow/
    │   ├── copy/
    │   ├── design/
    │   ├── logic/
    │   └── video/
    ├── 02_Click_Sequence/
    ├── 03_Survey_Funnel/
    ├── 04_Webinar_Campaign/
    ├── 05_PLF_Launch/
    ├── 06_Invisible_Campaign/
    └── 07_4_Day_Cash_Machine/
```

## Campaign Order

| # | Campaign | Method | Purpose |
|---|----------|--------|---------|
| 01 | Onboarding Flow | Welcome sequence | Trust + first value |
| 02 | Click Sequence | Frank Kern — universal filter | Separate engaged from cold |
| 03 | Survey Funnel | Ryan Levesque — ASK Method | Segment + capture language |
| 04 | Webinar Campaign | Live or automated | Educate + convert |
| 05 | PLF Launch | Jeff Walker — Seed → Internal | Big launch event |
| 06 | Invisible Campaign | Frank Kern | Evergreen nurture + embedded offer |
| 07 | 4 Day Cash Machine | Frank Kern | Short revenue burst |

## Core Principles

- **Platform-independent output** — no specific CRM or email tool names in any agent prompt. The Logic Agent outputs blueprints that implement in any platform.
- **No fake scarcity** — only natural deadlines (real launch dates, real cohort limits).
- **Owned audience first** — every campaign drives toward the email list.
- **Copy-paste ready** — all agent output is ready for human review and direct implementation.
- **Human approval required** — agents produce, humans approve before anything goes live.
- **Simplicity over over-engineering** — one CTA per email, one idea per video section.

## How to Start a Session

1. **Run Campaign Manager** → select language (English / Magyar / Other) + confirm active domain
2. **Run the relevant agent** for the asset you need today
3. **Review output** → copy-paste into your tools
4. **Agents hand off to each other** — Video Script Agent → thumbnail brief → Design Agent

## Multi-Client Usage

Add a new domain folder for each client:
- `campaigns/ClientA/`
- `campaigns/ClientB/`
- `campaigns/ZoltanGero/`

Switch between them by updating `_active_domain.md`. All agents always write only to the active domain.

## Tool Stack

| Tool | Role |
|------|------|
| Claude | AI orchestration — runs all agents |
| Canva Free | Design execution (from Design Agent briefs) |
| Google Workspace | Drive (file storage), Slides (presentations), Docs (copy review) |
| Email/CRM platform | Campaign implementation (Logic Agent blueprints are platform-agnostic) |
| Subscribr (optional) | YouTube SEO for Video Script Agent |
| TranscriptLOL (optional) | Voice matching from existing transcripts |
| Castmagic (optional) | Audio/video → copy repurposing |
| Subeasy (optional) | Subtitle generation for video |
| HeyGen / Vento (optional) | AI avatar video production |

## Offer Context (ZoltanGero Default)

Comprehensive education bundle — designed to grow over time:
- Video Course (evergreen, self-paced)
- Group Coaching + Accountability
- Exclusive Community
- Free Guide + Templates (lead magnet entry point)
- Future: Apps / Tools (leave open — no specific promises until ready)

Positioning: Purposeful. Peaceful. Profitable. Abundant.

## Setup Notes

- ICP, Offer detail, and Hero Story live in `_config.md` — intentionally left as TODO until Survey Funnel data is collected
- Start with `02_Click_Sequence` for ZoltanGero (as decided in initial setup)
- Language default: English, with Magyar available session-by-session

## Version

0.1.0 — Initial build. First active campaign: 02_Click_Sequence / ZoltanGero.
