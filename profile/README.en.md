<div align="center">

# 🦆 Quect

### `quack a swarm. flat the bill.`

**Flat-rate, API-compatible inference for coding agents.**
Fixed monthly price. Dedicated throughput. No per-token meter, no surprise bill.

[Português (BR)](README.md) · **English** · [Español](README.es.md)

[Discord](https://discord.gg/MuN6VzTEA3) · [Waitlist](https://quect.ai) · [quect.ai](https://quect.ai)

> ⚠️ **Pre-launch.** Closed beta in waves on a single reserved A100 node. Nothing here is live yet — star + join the waitlist to get pulled into a wave.

</div>

---

## What is this

Running coding agents (Claude Code, Cline, Aider, Codex, OpenCode) on per-token APIs means an unpredictable bill — $5–30/day on BYOK, surprise jumps when providers flip to metering. That's the dial-up era of inference.

Quect is the broadband layer: a **subscription** instead of a meter.

- **Uncapped tokens** — loop 24/7. (Not "unlimited" — uncapped tokens under a fair-use AUP.)
- **Dedicated throughput** — capped in tokens/second, not in volume. The speed is yours.
- **Queue gateway** — bursts over your throughput go into a millisecond async queue. Never blocks hard, never bills extra.
- **No proprietary CLI** — it's an OpenAI/Anthropic-API-compatible gateway. Point your existing tool's base URL at it. Done.

## Drop-in compatibility

Quect speaks the OpenAI and Anthropic APIs. Change one URL:

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

## Models

Open-weight, served with [Unsloth Dynamic 2.0](https://huggingface.co/unsloth) quants (~82% top-1 vs original at 2-bit) on vLLM.

| Alias | Model | Use case |
|-------|-------|----------|
| `quect-lite` | Qwen3.6-27B (11.8GB Q2) | Autocomplete, lint-fix, single-file |
| `quect-swarm` ⭐ | Qwen3-Coder-Next — MoE 80B / 3B active (26.8GB Q2) | Multi-file refactor, 256k context |
| `quect-max` | GLM-5.2 / frontier pass-through *(Enterprise)* | Long-horizon, critical analysis |

**Why it's cheap without being bad:** `quect-swarm` is MoE with only ~3B active params per forward pass — 27GB on disk, but it batches like a 3B model. One A100 serves 16–20 concurrent connections.

## Honest trade-off

This is open-weight inference: ~80% of Sonnet's coding quality, with a 10–15pp gap on SWE-bench. Great for the mechanical 90% of agent work; for the hard 10%, use the frontier pass-through on the top tier. Flat-rate flips the math anyway — running 10 attempts costs the same as 1.

The full thesis and unit economics: [`The economics of flat-rate inference`](https://quect.ai/blog/flat-rate-inference).

## Status & roadmap

- [x] Thesis, pricing, unit economics validated
- [ ] Compat gateway (OpenAI + Anthropic) — **in progress**
- [ ] Closed beta · wave 1 (single reserved A100)
- [ ] Public metrics: uptime · tok/s · queue depth
- [ ] CORP tier (seats, admin panel, SSO)

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
