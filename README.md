# Agent Toolkit Demo

[![Agent toolkit CI](https://github.com/cemini23/agent-toolkit-demo/actions/workflows/agent-toolkit.yml/badge.svg)](https://github.com/cemini23/agent-toolkit-demo/actions/workflows/agent-toolkit.yml)

Minimal repo showing **vet + phase0 + wikilint** in CI — good artifacts pass, bad ones fail on purpose.

| Tool | Path | Expected in CI |
|------|------|----------------|
| [vet](https://github.com/cemini23/vet) | `skills/good-skill/` | PASS |
| vet | `skills/bad-skill/` | REJECT (job asserts failure) |
| vet | `briefs/good-brief.md` | PASS |
| [phase0](https://github.com/cemini23/phase0) | `evals/sample-eval.md` | Mismatch detected (assert failure) |
| [wikilint](https://github.com/cemini23/wikilint) | `wiki/` | PASS (clean graph) |

Schema reference: [ara-schema](https://github.com/cemini23/ara-schema)

## Run locally

```bash
pip install git+https://github.com/cemini23/vet.git
pip install git+https://github.com/cemini23/phase0.git
pip install git+https://github.com/cemini23/wikilint.git

vet skills/good-skill/SKILL.md --profile skillmd --strict
vet skills/bad-skill/SKILL.md --profile skillmd --strict   # exit 2
phase0 verify-eval evals/sample-eval.md                    # exit 2 on mismatch
wikilint wiki/
```

## Use as template

Fork this repo or copy `.github/workflows/agent-toolkit.yml` into your project.

## Related

- Methodology newsletter: [Outlier Weekly](https://outlierweekly.substack.com)
- Agent meta-wiki: [cemini-claude-code-CCC](https://github.com/cemini23/cemini-claude-code-CCC)
- Toolkit: [vet](https://github.com/cemini23/vet) · [wikilint](https://github.com/cemini23/wikilint) · [phase0](https://github.com/cemini23/phase0) · [ara-schema](https://github.com/cemini23/ara-schema)

## License

MIT — see [LICENSE](LICENSE).
