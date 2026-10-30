# Conversation Confidence App — Product Idea

## One-line summary
A real-time, audio-only AI conversation partner that helps shy / low-English speakers practice everyday communication, building confidence and vocabulary. Ships first as a sellable project/demo for grads and junior devs, then evolves into a live product.

## Target user (v1)
- Shy English learners (low confidence, limited mastery) — any age, but v1 focuses on a narrow reachable slice.
- Secondary later: job seekers (interview simulator) — deferred to v2.

## Problem
Users watch English content (YouTube) and quit — they never actually speak. The gap is between *watching* English and *speaking* it. Generic AI voice tools exist but feel intimidating and aren't built for shy beginners.

## Unfair advantage
- Native-language understanding (code-switching, cultural nuance).
- Distribution via YouTube + Instagram (build-in-public content).

## Validation plan
- Landing page + content test (Reels/Shorts) demonstrating the concept.
- Kill criteria: low engagement/DMs or no willingness to pay even ₹49–₹99/mo.

## Business model (staged)
1. **Stage 1 — Fundraising:** Release v1 as a sellable project/resume/academic project to college students, grads, and junior devs (~₹4k). Group-buying for students; affordable for earners.
2. **Stage 2 — Infrastructure:** Use sales revenue to fund infra.
3. **Stage 3 — Live product:** Improve and release to real end users (shy English learners).

## MVP scope (v1 = free-flowing conversation, not structured lessons)

**Must-have:**
- Voice in/out with a warm AI coach (listens, responds, gently corrects, encourages).
- Gentle real-time correction + encouragement (not harsh).
- Native-language onboarding; coach can code-switch/explain in user's language.
- Simple "start talking" entry — no lesson selection, no forced sessions.
- Basic progress: streak + words encountered.
- BYOK (Bring Your Own Key): buyer uses their own Groq API key.
- Settings page: key input + "test connection" + provider/model selector.
- Debug panel (collapsible): live API log, classified error hints (401/429/404/network), masked keys, copy-to-clipboard.

**Should-have (v1.1):**
- Topic prompts ("let's talk about your day").
- Post-conversation summary (new words, one tip).
- Accent/pace adaptation.

**Could-have (later):**
- Personalized memory across sessions.
- Confidence score / gamification.
- Multiple coach personalities.

**Won't-have (v1):**
- Video, structured curriculum, assessments, leaderboards, multi-user, native mobile app (web/PWA first).

## Success metric
Retention — if shy users come back, everything else follows.

## Tech direction
- **Stack:** Next.js 14 (App Router) + Tailwind + shadcn/ui, single repo, `npm install && npm run dev`.
- **LLM (primary):** Groq — Llama 3.1 8B Instant (free tier: 30 RPM, 30K TPM, ~1M TPD). Fast, free, no credit card.
- **LLM (fallback):** Gemini Flash (free tier).
- **LLM (opt-in offline):** Ollama — Llama 3.1 8B (or 3B for weak machines). Fully local, private, $0.
- **STT:** Web Speech API (Chrome, free).
- **TTS:** Edge TTS / browser speechSynthesis (free).
- **State:** localStorage only — no DB, runs anywhere with zero setup.
- **Deploy:** Vercel free tier → live demo URL.

## Rate-limit handling
- Use 8B (not 70B) for 5× token budget.
- Cap `max_tokens` ~150; trim history to last 6–8 turns.
- Exponential backoff on 429 (1s, 2s, 4s).
- Fallback to Gemini Flash on sustained 429.
- Per-user keys so limits aren't shared across customers.
- Client-side turn throttling.

## LLM usage notes
- The product is the PROMPT, not the model. Warm, patient, never judgmental persona; short sentences; simple vocab; code-switching; gentle correction; one question at a time.
- Local 3B-on-CPU gives ~4–7s latency (fine for shy learners); cloud Groq gives <1s (better for demos).

## Milestones
- **M1 (Week 1) — Core loop:** Voice in → LLM → voice out (<2s). Basic chat UI with listening/speaking states. Settings (BYOK key + test) + debug panel. Deliverable: runnable demo.
- **M2 (Week 2) — Polish & persona:** Warm coach persona prompt, native-language toggle, onboarding, session summary card, polished UI (avatar, waveform, dark/light, mobile). Deliverable: "wow" demo video (30–60s).
- **M3 (Week 3) — Packaging & launch:** README with setup + provider swap guide + screenshots. Vercel deploy + live demo. Landing page + pricing (₹4k) + payment link. Deliverable: sellable project + hosted demo + first sales.

## Effort estimate
- Solo dev, ~3 weeks part-time (or ~1.5 weeks full-time).
- Buyer run-cost: $0 (free tiers).

## Risks & unknowns
- Selling "resume projects" is a crowded market (GitHub templates, Fiverr, YouTube tutorials) — thin margins.
- Buyers need decent hardware for local/Ollama mode → support burden.
- Free-tier rate limits if centralized hosted product.
- "Anyone of any age group" is too broad — must narrow for v1.

## v2 backlog seeds
- Job interview simulator (role-specific, real-time audio, generated from job details, audio-only).
- Structured curriculum / topic prompts.
- Personalized memory, confidence score, gamification.
- Native mobile app.

## Status
Idea finalized. Not built yet. Repo used for storing ideas.