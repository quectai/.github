<div align="center">

# 🦆 Quect

### `quack a swarm. flat the bill.`

**Banda dedicada para swarms de agentes de código.**
Inferência flat-rate: uncapped tokens, throughput dedicado, conta previsível — sem bill-shock.

**Português (BR)** · [English](README.en.md) · [Español](README.es.md)

[Discord](https://discord.gg/MuN6VzTEA3) · [Waitlist](https://quect.ai) · [quect.ai](https://quect.ai)

> ⚠️ **Pre-launch · junho 2026.** Beta fechado em waves. Nada no ar ainda — dá uma ⭐ e entra na waitlist; a gente avisa quando o primeiro nó subir.

</div>

---

## O problema

O dev power-user de 2026 paga **$200–600/mês** em token, e o mercado migrou todo pra metering nos últimos 12 meses. A conta é imprevisível:

- **Copilot** — $29 virou **$750**/mês depois do flip pra metering
- **Replit** — plano de $25, bills surpresa de **$100–300**
- **Uber** — capou engenheiros em **$1.500/mês** após queimar o budget anual em 4 meses

Deixar um swarm rodando 24/7 vira roleta-russa de fatura.

## A solução: banda larga para inferência

O mesmo salto que a banda larga deu na telefonia — de pagar por minuto → assinatura fixa com velocidade dedicada. Quect aplica isso a tokens:

- **🦆 Tokens sem limite** — assinatura fixa, loops e swarms 24/7 sem contador rodando no fundo. *(uncapped tokens, fair-use AUP — não "unlimited".)*
- **⚡ Throughput dedicado** — largura de banda em tokens/s por conta. Honesto, previsível, sem letrinha miúda.
- **🌊 Queue gateway** — excesso entra em fila de milissegundos. Nunca bloqueia, nunca cobra extra.

## Pluga nas ferramentas que você já usa

Endpoint **OpenAI-API-compatible** (+ Anthropic). Se o seu agent/harness fala a API, aponta a base URL pro Quect — sem CLI novo, sem migração.

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
    "messages": [{"role": "user", "content": "refatora esse módulo"}]
  }'
```

*(Os endpoints entram no ar por wave de beta. O contrato acima é o alvo.)*

## Multi-modelo OSS · routing automático

O modelo certo pra cada tarefa, escolhido automaticamente. Precisa do topo? Frontier (Sonnet/GPT) entra por pass-through no Enterprise.

| Modelo | Caso de uso | Tier |
|--------|-------------|------|
| **Qwen3-Coder-Next** ⭐ | flagship · multi-file · 256k context | SWARM |
| **Qwen3.6-27B** | daily driver · refactor + TDD · vision | LITE · SWARM |
| **GLM-5.2** | long-horizon · 1M token context | ENTERPRISE |
| **MiniMax-M3** | análise massiva · raciocínio extenso | ENTERPRISE |
| **MiMo-V2.5-Pro** | agent harnesses complexos | ENTERPRISE |

*Catálogo curado pelos melhores modelos open-source do [LMArena WebDev leaderboard](https://arena.ai/leaderboard/code/webdev?license=open-source) · sujeito a mudança — modelos novos entram, antigos são depreciados.*

## Planos

| Tier | Preço | Throughput | Pra quem |
|------|-------|-----------|----------|
| **DEV LITE** | $30/mês | 30–40 tok/s · 1 agente | estudante · iniciante |
| **DEV SWARM** ⭐ | $59/mês | 90–120 tok/s · 3 agentes | sênior · freelancer |
| **CORP SWARM** | $249/mês | 400–500 tok/s · 5 seats | startup · agência |
| **ENTERPRISE** | $999+/mês | 150–300 tok/s · dedicada | compliance · privacidade |

*Uncapped tokens, fair-use AUP · throughput por conta no LITE/SWARM, por seats no CORP. Planos e números sujeitos a ajuste até o launch.*

## Entra na fila

1. ⭐ neste repo
2. Entra no [Discord](https://discord.gg/MuN6VzTEA3)
3. [Waitlist](https://quect.ai) — conta quanto você gasta/mês em token + qual harness usa

## Licença

MIT.

---

<div align="center">
🦆 <i>quack a swarm. flat the bill.</i> · feito por <a href="https://quect.ai">Quect.ai</a>
</div>
