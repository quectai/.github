<div align="center">

# 🦆 Quect

### `quack a swarm. flat the bill.`

**Dedicated bandwidth for swarms of coding agents.**
Flat-rate inference: uncapped tokens, dedicated throughput, a predictable bill — no bill-shock.

[Português (BR)](README.md) · **English** · [Español](README.es.md)

[Discord](https://discord.gg/MuN6VzTEA3) · [Waitlist](https://quect.ai) · [quect.ai](https://quect.ai)

> ⚠️ **Pre-launch · June 2026.** Closed beta in waves. Nothing live yet — star + join the waitlist; we'll ping you when the first node is up.

</div>

---

## The problem

The 2026 power-user dev pays **$200–600/mo** in tokens, and the market flipped entirely to metering over the last 12 months. The bill is unpredictable:

- **Copilot** — $29 became **$750**/mo after the metering flip
- **Replit** — $25 plan, surprise **$100–300** bills
- **Uber** — capped engineers at **$1,500/mo** after burning the annual budget in 4 months

Leaving a swarm running 24/7 turns into invoice roulette.

## The fix: broadband for inference

The same leap broadband made over telephony — from per-minute metering → a fixed subscription with dedicated speed. Quect applies it to tokens:

- **🦆 Uncapped tokens** — fixed subscription, loops and swarms 24/7 with no meter running in the background. *(uncapped tokens, fair-use AUP — not "unlimited".)*
- **⚡ Dedicated throughput** — bandwidth in tokens/s per account. Honest, predictable, no fine print.
- **🌊 Queue gateway** — overflow goes into a millisecond queue. Never blocks hard, never bills extra.

## Plug into the tools you already use

**OpenAI-API-compatible** endpoint (+ Anthropic). If your agent/harness speaks the API, point its base URL at Quect — no new CLI, no migration.

```bash
# OpenAI-compatible (Cline, Aider, Codex, Continue, OpenCode…)
export OPENAI_BASE_URL="https://api.quect.ai/v1"
export OPENAI_API_KEY="qk_..."

# Anthropic-compatible (Claude Code)
export ANTHROPIC_BASE_URL="https://api.quect.ai/anthropic"
export ANTHROPIC_API_KEY="qk_..."
```

```bash
curl https://api.quect.ai/v1/chat/completions \
  -H "Authorization: Bearer $OPENAI_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "model": "quect-swarm",
    "messages": [{"role": "user", "content": "refactor this module"}]
  }'
```

*(Endpoints go live per beta wave. The shape above is the target contract.)*

## Multi-model OSS · automatic routing

The right model per task, picked automatically. Need the top? Frontier (Sonnet/GPT) comes in via pass-through on Enterprise.

| Model | Use case | Tier |
|-------|----------|------|
| **Qwen3-Coder-Next** ⭐ | flagship · multi-file · 256k context | SWARM |
| **Qwen3.6-27B** | daily driver · refactor + TDD · vision | LITE · SWARM |
| **GLM-5.2** | long-horizon · 1M token context | ENTERPRISE |
| **MiniMax-M3** | massive analysis · extended reasoning | ENTERPRISE |
| **MiMo-V2.5-Pro** | complex agent harnesses | ENTERPRISE |

*Catalog curated from the top open-source models on the [LMArena WebDev leaderboard](https://arena.ai/leaderboard/code/webdev?license=open-source) · subject to change — new models added, old ones deprecated.*

## Plans

| Tier | Price | Throughput | For whom |
|------|-------|-----------|----------|
| **DEV LITE** | $30/mo | 30–40 tok/s · 1 agent | student · beginner |
| **DEV SWARM** ⭐ | $59/mo | 90–120 tok/s · 3 agents | senior · freelancer |
| **CORP SWARM** | $249/mo | 400–500 tok/s · 5 seats | startup · agency |
| **ENTERPRISE** | $999+/mo | 150–300 tok/s · dedicated | compliance · privacy |

*Uncapped tokens, fair-use AUP · throughput per account on LITE/SWARM, per seat on CORP. Plans and numbers subject to adjustment until launch.*

## Get in

1. ⭐ this repo
2. Join the [Discord](https://discord.gg/MuN6VzTEA3)
3. [Waitlist](https://quect.ai) — tell us your current monthly token spend + which harness you use

## License

MIT.

---

<div align="center">
🦆 <i>quack a swarm. flat the bill.</i> · built by <a href="https://quect.ai">Quect.ai</a>
</div>
