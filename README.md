# Agent Toolkit Demo

Minimal repo showing **vet + phase0 + wikilint** in CI on intentionally bad agent artifacts.

| Tool | Path | Expected in CI |
|------|------|----------------|
| [vet](https://github.com/cemini23/vet) | `skills/good-skill/` | PASS |
| vet | `skills/bad-skill/` | REJECT |
| vet | `briefs/good-brief.md` | PASS |
| phase0 | `evals/sample-eval.md` | verify license column |
| wikilint | `wiki/` | WARN (orphans + gaps by design) |

## Run locally

```bash
pip install git+https://github.com/cemini23/vet.git
pip install git+https://github.com/cemini23/phase0.git
pip install git+https://github.com/cemini23/wikilint.git

vet skills/good-skill/SKILL.md --profile skillmd --strict
vet skills/bad-skill/SKILL.md --profile skillmd --strict   # exit 2
phase0 verify-eval evals/sample-eval.md
wikilint wiki/
```

## Use as template

Fork this repo or copy `.github/workflows/agent-toolkit.yml` into your project.
