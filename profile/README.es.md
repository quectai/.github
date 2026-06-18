<div align="center">

# 🦆 Quect

### `quack a swarm. flat the bill.`

**Inferencia flat-rate y compatible con API para agentes de código.**
Precio mensual fijo. Throughput dedicado. Sin medidor por token, sin factura sorpresa.

[Português (BR)](README.md) · [English](README.en.md) · **Español**

[Discord](https://discord.gg/MuN6VzTEA3) · [Waitlist](https://quect.ai) · [quect.ai](https://quect.ai)

> ⚠️ **Pre-launch.** Beta cerrada por waves en un único nodo A100 reserved. Todavía no hay nada en vivo — dale ⭐ y únete a la waitlist para entrar en una wave.

</div>

---

## Qué es esto

Correr agentes de código (Claude Code, Cline, Aider, Codex, OpenCode) con APIs por token significa una factura impredecible — $5–30/día en BYOK, saltos sorpresa cuando el proveedor cambia a medición por uso. Esa es la era del dial-up de la inferencia.

Quect es la capa de banda ancha: una **suscripción** en lugar de un medidor.

- **Tokens sin tope** — loop 24/7. (No es "unlimited" — tokens uncapped bajo un fair-use AUP.)
- **Throughput dedicado** — limitado en tokens/segundo, no en volumen. La velocidad es tuya.
- **Queue gateway** — los picos por encima de tu throughput entran en una cola asíncrona de milisegundos. Nunca bloquea, nunca cobra de más.
- **Sin CLI propietario** — es un gateway compatible con la API de OpenAI/Anthropic. Apunta la base URL de tu herramienta actual aquí. Listo.

## Compatibilidad drop-in

Quect habla las APIs de OpenAI y Anthropic. Cambia una URL:

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
    "messages": [{"role": "user", "content": "refactoriza este módulo"}]
  }'
```

*(Los endpoints entran en vivo por wave de beta. El contrato de arriba es el objetivo.)*

## Modelos

Open-weight, servidos con quants [Unsloth Dynamic 2.0](https://huggingface.co/unsloth) (~82% top-1 vs original en 2-bit) sobre vLLM.

| Alias | Modelo | Caso de uso |
|-------|--------|-------------|
| `quect-lite` | Qwen3.6-27B (11.8GB Q2) | Autocomplete, lint-fix, single-file |
| `quect-swarm` ⭐ | Qwen3-Coder-Next — MoE 80B / 3B activos (26.8GB Q2) | Refactor multi-file, 256k context |
| `quect-max` | GLM-5.2 / frontier pass-through *(Enterprise)* | Long-horizon, análisis crítico |

**Por qué es barato sin ser malo:** `quect-swarm` es MoE con solo ~3B params activos por forward pass — 27GB en disco, pero batchea como un 3B. Un A100 sirve 16–20 conexiones simultáneas.

## Trade-off honesto

Esto es inferencia open-weight: ~80% de la calidad de Sonnet en código, con una brecha de 10–15pp en SWE-bench. Excelente para el 90% mecánico del trabajo de agente; para el 10% difícil, usa el frontier pass-through en el tier superior. Flat-rate da vuelta la cuenta de todos modos — correr 10 intentos cuesta lo mismo que correr 1.

Tesis completa y unit economics: [`The economics of flat-rate inference`](https://quect.ai/blog/flat-rate-inference).

## Status & roadmap

- [x] Tesis, pricing y unit economics validados
- [ ] Compat gateway (OpenAI + Anthropic) — **en progreso**
- [ ] Beta cerrada · wave 1 (único A100 reserved)
- [ ] Métricas públicas: uptime · tok/s · tamaño de cola
- [ ] Tier CORP (seats, panel admin, SSO)

## Únete

1. ⭐ este repo
2. Únete al [Discord](https://discord.gg/MuN6VzTEA3)
3. [Waitlist](https://quect.ai) — cuéntanos cuánto gastas/mes en tokens + qué harness usas

## Licencia

MIT.

---

<div align="center">
🦆 <i>quack a swarm. flat the bill.</i> · hecho por <a href="https://quect.ai">Quect.ai</a>
</div>
