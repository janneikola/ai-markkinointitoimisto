# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

AI-Markkinointitiimi is a SaaS platform by Aava & Bang AI that replaces traditional marketing agencies with 6 autonomous AI agents (Orgaaninen SEO, Tekninen SEO, Maksettu some, SEM, Sisältö, Analytiikka). Finnish-language product targeting SMBs at €299–999/month.

**Current state:** Early prototype phase — static HTML demos and a comprehensive PRD. No application framework set up yet.

## Repository Contents

- `demo.html` — Interactive dashboard prototype (self-contained, Nordic Control Room UI theme)
- `presentation.html` — Product pitch presentation with animations
- `PRD.md` — Full product requirements document (Finnish, ~1265 lines)
- `assets/` — UI mockup PNGs (dashboard, agent cards, approval queue, onboarding)
- `.agents/skills/frontend-design/SKILL.md` — Frontend design guidelines

## Planned Tech Stack (from PRD)

- **Frontend:** Next.js 15 + React 19, Tailwind CSS + shadcn/ui, Zustand + React Query
- **Backend:** Next.js API Routes + tRPC, PostgreSQL (Supabase) with RLS, Redis (Upstash)
- **AI:** Claude API (Anthropic) for reasoning/content, Voyage AI embeddings, Pinecone/pgvector
- **Auth:** Clerk or NextAuth
- **Payments:** Stripe
- **Hosting:** Vercel (frontend) + Railway (backend services)

## Design System (Nordic Control Room)

Key CSS variables from `demo.html`:
- Background: `#111110` (primary), `#1a1a18` (secondary)
- Text: `#ece8e1` (primary), `#a09a90` (secondary)
- Accent: `#d4882b` (warm gold/orange)
- Status colors: green `#5cb85c`, orange `#e8a84c`, red `#c9544d`, cyan `#5ba4b5`
- Fonts: Gambetta (serif display), Switzer (sans-serif body) via Fontshare API

## Agent Architecture Pattern

Each of the 6 agents follows: Gather Data → Analyze → Decide Actions → Classify autonomy level → Execute auto / Queue approval → Update shared context. Agents communicate with each other (e.g., SEO briefs Content agent, Analytics distributes insights to all).

## Autonomy Levels

- **Automatic:** monitoring, reporting, routine optimization
- **Post-notification:** execute then notify (A/B tests, minor budget shifts)
- **Pre-approval:** propose and wait (content, major changes)
- **Collaborative:** real-time collaboration for strategy

## Language

- UI text: Finnish
- Code and variable names: English
- PRD: Finnish

## Git Remote

- GitHub: `janneikola/ai-markkinointitoimisto`
- Railway deployment connected to this repo
