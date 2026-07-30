# Backlog: AI Chat Sidebar

**Status:** Idea / not started
**Goal:** Let a reader ask clarifying questions mid-section (e.g. "how do I install", "how do I
prompt", "how do I publish to GitHub + Vercel") from a slide-in sidebar, answered by a fast/cheap
LLM grounded in this guide's content.

---

## Core constraint

The site is a **static `index.html` on Vercel with no backend**. A provider API key must **never**
ship in client-side JS (anyone could read it via View Source / Network tab and run up the bill).
The whole architecture is built around keeping the key server-side.

**Decision:** use a **Vercel serverless function** as a proxy. The key lives as a Vercel
environment variable; the browser only ever talks to our own `/api/chat` endpoint.

---

## Files

```
index.html              # existing page + new chat sidebar markup/CSS/JS (client)
api/
  chat.js               # NEW — Vercel serverless function (the proxy; holds the key)
vercel.json             # OPTIONAL — config (functions, headers) if needed
.env.local              # local dev only, gitignored — LLM_API_KEY=...
                        # (production key is set in Vercel dashboard env vars, not committed)
```

Client additions inside `index.html` (keep it self-contained, like the rest of the site):

- **Markup:** a collapsible right-side panel + a floating "Ask" button.
- **CSS:** slide-in panel, message bubbles, input box — theme-matched (orange/yellow palette),
  responsive (full-width sheet on mobile).
- **JS:** open/close, capture question, `fetch('/api/chat')`, stream/append the answer,
  keep a short in-memory message history. Bilingual (EN/PT) via the existing `data-i18n` pattern.

---

## Data flow

```
┌──────────────┐   1. question + section id     ┌────────────────────┐   3. provider request
│  Browser     │ ─────────────────────────────► │  /api/chat.js       │ ─────────────────────►  ┌───────────┐
│  (chat UI)   │      POST (no key involved)     │  (Vercel function)  │   key from env var      │  LLM API  │
│              │ ◄───────────────────────────── │                     │ ◄─────────────────────  │ (Haiku /  │
└──────────────┘   4. answer (text/stream)       └────────────────────┘   provider response       │  Gemini / │
                                                                                                    │  OpenAI)  │
                                                                                                    └───────────┘
      2. function builds the prompt:
         system = short instructions + relevant guide section text (grounding)
         user   = the reader's question
```

Step by step:

1. Reader types a question in the sidebar. Client `POST`s `{ question, sectionId, lang, history }`
   to `/api/chat`. **No API key in this request.**
2. The function assembles the prompt: a small system prompt (persona + "answer only from this
   guide") plus the relevant section's text as grounding context. Section text is small, so no
   vector DB / RAG infra is needed — just inline the content (or a static JSON of section texts).
3. The function calls the LLM provider using the key from `process.env.LLM_API_KEY`.
4. The answer streams (or returns) back to the browser and renders in the panel.

---

## Grounding (keeping answers about THIS guide)

- Extract each section's text into a small map: `{ install, build, publish, ... }` (could live in
  the function or a generated `content.json`).
- Inject the current section (and maybe the whole page — it's short) as system context.
- Optional nicety: the client passes which section the reader is currently viewing so the model
  focuses there.

---

## Security & cost guardrails (must-haves before going live)

- **Key server-side only** — Vercel env var, never in the client bundle, never committed.
- **Hard spend cap** on the provider account (billing limit) — the endpoint is public.
- **Rate limiting** in the function — per-IP throttle + max tokens per request/day. (Vercel KV or
  Upstash Redis for counters, or a simple in-memory/edge limiter to start.)
- **Input caps** — max question length; reject empty/oversized payloads.
- **CORS** — restrict the function to the site's own origin.
- Consider a lightweight abuse guard (e.g. a simple challenge) if traffic grows.

---

## Model options (fast + cheap, pick by whichever key we have)

- **Claude Haiku** (Anthropic)
- **Gemini Flash** (Google)
- OpenAI small/mini tier

Any handles short grounded Q&A well. The function abstracts the provider so it can be swapped by
changing one call + env var.

---

## What changes about the project

- Still essentially one static page — **plus** one serverless function and an env var.
- No separate server to run; Vercel handles the function natively.
- Local dev: `vercel dev` (to run the function) instead of `python -m http.server`.

---

## Suggested phases

1. **Prototype UI, mocked** — build the sidebar with a fake/echo response. No key, no cost. Validate
   UX and bilingual copy.
2. **Serverless proxy** — add `api/chat.js`, wire a real model, env var, grounding context.
3. **Guardrails** — spend cap, rate limit, input caps, CORS.
4. **Polish** — streaming responses, section-aware context, error/empty states, mobile sheet.

---

## Open questions

- BYOK fallback? (let power users paste their own key, stored only in their `localStorage`) — zero
  cost to us, optional alongside the proxy.
- Streaming vs. single response for v1? (streaming feels better but adds a little complexity)
- Which provider/key to standardize on?
