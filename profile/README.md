<div align="center">

# 🦆 Quect

### `quack a swarm. flat the bill.`

**Inferência flat-rate e API-compatível para agentes de código.**
Preço mensal fixo. Throughput dedicado. Sem medidor por token, sem conta surpresa.

**Português (BR)** · [English](README.en.md) · [Español](README.es.md)

[Discord](https://discord.gg/MuN6VzTEA3) · [Waitlist](https://quect.ai) · [quect.ai](https://quect.ai)

> ⚠️ **Pre-launch.** Beta fechado em waves num único nó A100 reserved. Nada aqui está no ar ainda — dá uma ⭐ e entra na waitlist pra ser puxado numa wave.

</div>

---

## O que é isso

Rodar agentes de código (Claude Code, Cline, Aider, Codex, OpenCode) em API por token significa conta imprevisível — $5–30/dia em BYOK, saltos surpresa quando o provider vira pro modelo de metering. Isso é a era do discado da inferência.

Quect é a camada de banda larga: uma **assinatura** no lugar de um medidor.

- **Tokens sem limite** — loop 24/7. (Não é "unlimited" — tokens uncapped sob fair-use AUP.)
- **Throughput dedicado** — limite em tokens/segundo, não em volume. A velocidade é sua.
- **Queue gateway** — bursts acima do seu throughput entram numa fila assíncrona de milissegundos. Nunca bloqueia, nunca cobra extra.
- **Sem CLI proprietário** — é um gateway compatível com a API da OpenAI/Anthropic. Aponta a base URL da ferramenta que você já usa pra cá. Pronto.

## Compatibilidade drop-in

Quect fala as APIs da OpenAI e da Anthropic. Troca uma URL:

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

## Modelos

Open-weight, servidos com quants [Unsloth Dynamic 2.0](https://huggingface.co/unsloth) (~82% top-1 vs original em 2-bit) sobre vLLM.

| Alias | Modelo | Caso de uso |
|-------|--------|-------------|
| `quect-lite` | Qwen3.6-27B (11.8GB Q2) | Autocomplete, lint-fix, single-file |
| `quect-swarm` ⭐ | Qwen3-Coder-Next — MoE 80B / 3B ativos (26.8GB Q2) | Refactor multi-file, 256k context |
| `quect-max` | GLM-5.2 / frontier pass-through *(Enterprise)* | Long-horizon, análise crítica |

**Por que é barato sem ser ruim:** `quect-swarm` é MoE com só ~3B params ativos por forward pass — 27GB no disco, mas batcha como um 3B. Um A100 serve 16–20 conexões simultâneas.

## Trade-off honesto

Isso é inferência open-weight: ~80% da qualidade do Sonnet em código, com gap de 10–15pp em SWE-bench. Ótimo pros 90% mecânicos do trabalho de agente; pros 10% difíceis, usa o frontier pass-through no tier de cima. Flat-rate vira o jogo de qualquer jeito — rodar 10 tentativas custa o mesmo que rodar 1.

Tese completa e unit economics: [`The economics of flat-rate inference`](https://quect.ai/blog/flat-rate-inference).

## Status & roadmap

- [x] Tese, pricing e unit economics validados
- [ ] Compat gateway (OpenAI + Anthropic) — **em progresso**
- [ ] Beta fechado · wave 1 (único A100 reserved)
- [ ] Métricas públicas: uptime · tok/s · tamanho da fila
- [ ] Tier CORP (seats, painel admin, SSO)

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
