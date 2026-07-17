# Agent Toolkit Demo

[![Agent toolkit CI](https://github.com/cemini23/agent-toolkit-demo/actions/workflows/agent-toolkit.yml/badge.svg)](https://github.com/cemini23/agent-toolkit-demo/actions/workflows/agent-toolkit.yml)

Minimal repo showing **vet + phase0 + wikilint** in CI — good artifacts pass, bad ones fail on purpose.

| Tool | Path | Expected in CI |
|------|------|----------------|
| [vet](https://github.com/cemini23/vet) | `skills/good-skill/` | PASS |
| vet | `skills/cursor-audit/` | PASS |
| vet | `skills/super-audit/` | PASS |
| vet | `skills/bad-skill/` | REJECT (job asserts failure) |
| vet | `briefs/good-brief.md` | PASS |
| [phase0](https://github.com/cemini23/phase0) | `evals/sample-eval.md` | Mismatch detected (assert failure) |
| [wikilint](https://github.com/cemini23/wikilint) | `wiki/` | PASS (clean graph) |

### cursor-audit skill

Open-source multi-model Cursor audit harness — three readonly Task subagents, Glasswing conflict synthesis. Ships in `skills/cursor-audit/`; install into any workspace:

```bash
cp -r skills/cursor-audit ~/.cursor/skills/
# or per-project: cp -r skills/cursor-audit .cursor/skills/
```

See [skills/cursor-audit/README.md](skills/cursor-audit/README.md). Wiki: [cemini-claude-code-CCC → cursor-audit](https://github.com/cemini23/cemini-claude-code-CCC/blob/main/wiki/entities/skills/cursor-audit.md).

### super-audit skill

Five-model pre-ship council — three Cursor Task subagents plus two **OpenRouter** API auditors (`openrouter/fusion` + premium task model, default `z-ai/glm-5.2`). Requires **`OPENROUTER_API_KEY`** in `~/.cemini/llm-routing.env` for full coverage. Tailor a prompt pack per run. Ships in `skills/super-audit/`:

```bash
cp -r skills/super-audit ~/.cursor/skills/
# or per-project: cp -r skills/super-audit .cursor/skills/
```

See [skills/super-audit/README.md](skills/super-audit/README.md).

Schema reference: [ara-schema](https://github.com/cemini23/ara-schema)

## Run locally

```bash
pip install git+https://github.com/cemini23/vet.git
pip install git+https://github.com/cemini23/phase0.git
pip install git+https://github.com/cemini23/wikilint.git

vet skills/good-skill/SKILL.md --profile skillmd --strict
vet skills/cursor-audit/SKILL.md --profile skillmd --strict
vet skills/super-audit/SKILL.md --profile skillmd --strict
vet skills/bad-skill/SKILL.md --profile skillmd --strict   # exit 2
phase0 verify-eval evals/sample-eval.md                    # exit 2 on mismatch
wikilint wiki/
```

## Use as template

Fork this repo or copy `.github/workflows/agent-toolkit.yml` into your project.

## Related

- Methodology newsletter: [Outlier Weekly](https://outlierweekly.substack.com)
- YouTube: [@Cemini23](https://www.youtube.com/@Cemini23)
- Agent meta-wiki: [cemini-claude-code-CCC](https://github.com/cemini23/cemini-claude-code-CCC)
- Toolkit: [vet](https://github.com/cemini23/vet) · [wikilint](https://github.com/cemini23/wikilint) · [phase0](https://github.com/cemini23/phase0) · [ara-schema](https://github.com/cemini23/ara-schema) · [cursor-audit](skills/cursor-audit/) · [super-audit](skills/super-audit/)


## Support

Voluntary tips fund open research and tooling. **Donation-only addresses** — not trading or production wallets.

| Chain family | Address |
|--------------|---------|
| **EVM** (Ethereum, Polygon, Base, Arbitrum, …) | `0x444C5C2eC439E0382aa5a17F70313c536BcC5D58` |
| **Solana / SVM** | `J4zNn4hK9jTrKBFY8sbAGJHLoZvXvQf4B9pQSbSrocZE` |
| **Polymarket** (referral) | [polymarket.com/?r=Cemini23](https://polymarket.com/?r=Cemini23) |


## License

MIT — see [LICENSE](LICENSE).
