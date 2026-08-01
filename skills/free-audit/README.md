# free-audit

Low-cost multi-model audit — Cursor packs context, Grok CLI audits + orchestrates claude-ds (DeepSeek V4 Flash) and ≥2 live free OpenRouter models (excluding DeepSeek/Grok). Minimal Cursor Task spend.

**Requires:** `grok` CLI, `OPENROUTER_API_KEY`, `DEEPSEEK_API_KEY` (or `CEMINI_LLM_ROUTING_ENV`). TipDrop `handoff-to-grok.ps1` recommended for always-approve.

## Install

```bash
git clone https://github.com/cemini23/agent-toolkit-demo.git
cp -r agent-toolkit-demo/skills/free-audit ~/.cursor/skills/
```

## Validate

```bash
vet skills/free-audit/SKILL.md --profile skillmd --strict
```

## Invoke

- `/free-audit` · `free audit on …` · `cheap audit` · `low-cost council`

## Toolkit stack

Sibling skills: [cursor-audit](../cursor-audit/) (3× Cursor) · [super-audit](../super-audit/) (3× Cursor + paid API).
