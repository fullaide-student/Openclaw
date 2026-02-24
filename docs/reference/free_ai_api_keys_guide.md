# Free & Safe AI API Keys Guide

Last updated: 2026-02-23

> Important: I can help you manage providers and configs, but I **cannot** provide stolen/shared API keys.  
> Use only official signup links and your own keys.

## Goal
Build a reliable pool of legitimate API keys so we can rotate providers when one hits quota/rate limits.

## Priority providers (official + commonly usable)

### Tier A (set up first)
1. **Google Gemini API (AI Studio)**  
   - Console: https://aistudio.google.com/apikey  
   - Notes: usually has a free tier (depends on region/account)

2. **Groq API**  
   - Console: https://console.groq.com/  
   - Docs: https://console.groq.com/docs/quickstart  
   - Notes: fast inference; often has free developer usage

3. **OpenRouter**  
   - Console: https://openrouter.ai/  
   - Docs: https://openrouter.ai/docs/quickstart  
   - Notes: one API for multiple model providers

4. **Hugging Face Inference**  
   - Tokens: https://huggingface.co/settings/tokens  
   - Docs: https://huggingface.co/docs/inference-providers/index  
   - Notes: broad model access; good for experimentation

### Tier B (add for redundancy)
5. **Cohere** — https://dashboard.cohere.com/  
6. **Mistral** — https://console.mistral.ai/  
7. **Together AI** — https://api.together.xyz/  
8. **Fireworks AI** — https://fireworks.ai/  
9. **DeepInfra** — https://deepinfra.com/  
10. **Replicate** — https://replicate.com/  
11. **AI21 Studio** — https://studio.ai21.com/  
12. **Cloudflare Workers AI** — https://developers.cloudflare.com/workers-ai/

> Availability of free tier / trial credits changes frequently. Always verify in each provider console.

---

## Safety rules (non-negotiable)

- Never use keys from “free key” websites or leaked lists.
- Never commit keys to GitHub (`.env`, JSON secrets, screenshots).
- Rotate/revoke immediately if a key is exposed.
- Use separate keys per service/purpose when possible.
- Set spend caps and rate limits in each provider console.

---

## OpenClaw key inventory template

Use this section to track only metadata (never full key values):

| Provider | Account Email | Key Label | Created | Limit Type | Status |
|---|---|---|---|---|---|
| Gemini |  |  |  | free tier | ⬜ |
| Groq |  |  |  | free/trial | ⬜ |
| OpenRouter |  |  |  | free/paid mix | ⬜ |
| Hugging Face |  |  |  | free tier | ⬜ |
| Cohere |  |  |  | trial | ⬜ |
| Mistral |  |  |  | trial | ⬜ |
| Together |  |  |  | trial | ⬜ |
| Fireworks |  |  |  | trial | ⬜ |
| DeepInfra |  |  |  | trial | ⬜ |
| Replicate |  |  |  | usage-based | ⬜ |
| AI21 |  |  |  | trial | ⬜ |
| Cloudflare Workers AI |  |  |  | account plan | ⬜ |

---

## Integration checklist for this repo

- [ ] Keep secrets only in local machine config (`~/.openclaw/openclaw.json` or env), never in repo
- [ ] Ensure `agents.defaults.models` includes at least 3 providers
- [ ] Define fallback order for quota failures
- [ ] Test one prompt against each provider
- [ ] Record pass/fail in `docs/daily/`

---

## Suggested fallback order for stability

1. `openai-codex/gpt-5.3-codex` (primary)
2. `openrouter/openai/gpt-4o-mini`
3. `groq/llama-3.3-70b-versatile`
4. `google-gemini/gemini-2.0-flash`

This keeps a balance of quality, speed, and quota resilience.
