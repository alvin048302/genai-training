# Generative AI for Working Professionals

A six-module interactive training deck designed to teach non-technical professionals how Gen AI works, where it helps, where it fails, and how to use it responsibly.

**🌐 Live deck:** [alvin048302.github.io/genai-training](https://alvin048302.github.io/genai-training)

---

## What this is

This is an end-to-end Gen AI literacy training tool — built as a teaching deck and a working demonstration of applied AI. The deck doesn't just *explain* Generative AI. Learners *experience* it directly through four embedded hands-on activities powered by real AI APIs.

Designed for working professionals across every sector — finance, healthcare, customer service, marketing — who need to understand AI well enough to use it confidently and responsibly in their work.

---

## What it covers

Six modules, structured for a 60–90 minute workshop or self-paced learning:

1. **What Is Generative AI?** — A plain-English explanation of how AI generates rather than retrieves
2. **How Gen AI Helps** — The three superpowers, plus deep dives across four high-impact sectors (Sales & Marketing, Customer Service, Finance, Healthcare)
3. **Limitations & Risks** — Hallucination, training cutoffs, bias, over-reliance, privacy
4. **Safeguards & Responsible Use** — Human-in-the-loop, prompting, ISO/IEC 5338 governance principles
5. **Real Application — FORGE** — A practical case study of AI applied to L&D programme design
6. **The Way Forward** *(optional)* — Singapore's National AI Strategy, what AI literacy means in practice

---

## Hands-on activities

Four embedded AI activities — learners run real AI inside the deck without leaving the page or signing up for anything:

| Activity | Module | What learners experience |
|----------|--------|--------------------------|
| **Generation, not Retrieval** | 1 | Same prompt, two different answers — proves AI generates fresh output every time |
| **Test the Speed Superpower** | 2 | One article, three audiences (CEO, colleague, child) generated simultaneously |
| **Frozen in Time** | 3 | An older AI confidently invents details about events it doesn't know — demonstrating hallucination and training cutoff |
| **Same Task, Two Prompts** | 4 | Vague vs specific prompt comparison — shows how prompt quality drives output quality |

Each activity takes about 5 minutes including debrief. Facilitator notes are built into every activity slide for live workshop use.

---

## Architecture

The deck is a single HTML file deployed via GitHub Pages, but the AI activities are powered by a Cloudflare Worker that securely proxies calls to multiple AI providers.

**Front-end:** Single-file HTML, no build step, no dependencies. Deployed via GitHub Pages.

**API layer:** Cloudflare Worker with four scoped endpoints — one per activity. Each endpoint has its prompt template baked in and accepts only minimal user input, preventing repurposing as a generic AI service.

**Provider strategy:** Multi-provider fallback for resilience.

| Activity | Primary | Fallback |
|----------|---------|----------|
| M1 — Generation | Gemini 2.0 Flash | Claude Haiku 4.5 |
| M2 — Speed | Gemini 2.0 Flash | Claude Haiku 4.5 |
| M3 — Frozen in Time | GPT-3.5-turbo *(Sept 2021 cutoff)* | Claude 3 Haiku *(Aug 2023 cutoff)* |
| M4 — Prompt Quality | Gemini 2.0 Flash | Claude Haiku 4.5 |

The M3 activity deliberately uses an older model with a pre-2024 training cutoff — guaranteeing the dramatic "confidently wrong" demonstration about the 2024 US election that anchors the lesson.

---

## Governance applied

The deck doesn't just teach AI governance principles — it applies them:

- **Origin allowlist** — Worker only accepts requests from approved domains
- **Rate limiting** — 30 requests per IP per hour, 150 per day, per endpoint
- **Scoped endpoints** — each activity has a locked prompt template; the API surface cannot be repurposed
- **Token caps** — output limited to 500 tokens per call to bound cost
- **Budget controls** — hard monthly spending limits set on all three providers
- **API key isolation** — keys live only in Cloudflare Worker environment variables, never in client-side code
- **Provider transparency** — every AI response shows which model produced it

This is what *Module 4 — Safeguards & Responsible Use* looks like in practice. The deck demonstrates the principles by being built on them.

---

## Design principles

- **Visual + analogy on every slide** — every Gen AI concept is paired with a simple visual and an everyday analogy
- **Animated diagrams** — input data flows into the AI engine, output appears progressively, reinforcing the concepts visually
- **Mobile-first** — works on phones, tablets, and desktops; swipe-friendly navigation
- **Module 6 optional** — a "skip to closing" button lets facilitators tailor the session for different audiences
- **Activity badges on module dividers** — sets expectations that hands-on practice is coming

---

## Why this exists

Singapore is positioning AI literacy as a baseline workforce capability — through SSG's SkillsFuture programme, the IBF GenAI Jobs Transformation Map, and Budget 2026's National AI Missions in finance and healthcare. But most existing AI training is either too technical (built for developers) or too superficial (built for marketing).

This deck sits in the middle: rigorous on substance, accessible in delivery, designed for the working professional who needs to use AI well — not build it.

---

## About

Built by **Alvin Nambiar** — Learning & Development professional with sixteen years in financial services. Currently building practical AI tools for workforce capability development across the Singapore L&D ecosystem.

Other projects:
- **FORGE** — AI-powered training programme builder for L&D practitioners
- **APPT.COACH** — Deployed AI roleplay simulator for sales conversation practice

---

## Contact

For training enquiries, collaboration, or feedback — [LinkedIn](https://www.linkedin.com/in/alvin-nambiar-724b486b/)) *(update with your link)*

---

*Last updated: May 2026*
