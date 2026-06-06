# cursor-audit

Multi-model Cursor audit skill — three parallel readonly subagents on different model families, synthesized into consensus / unique / conflicts before ship.

**Requires:** Cursor with Task subagents and multi-model access. Not a Claude Code `Agent`-tool skill without adaptation.

## Install

```bash
# Option A — from agent-toolkit-demo (this repo)
git clone https://github.com/cemini23/agent-toolkit-demo.git
cp -r agent-toolkit-demo/skills/cursor-audit ~/.cursor/skills/

# Option B — from CCC meta-wiki (same files)
git clone https://github.com/cemini23/cemini-claude-code-CCC.git
cp -r cemini-claude-code-CCC/.cursor/skills/cursor-audit ~/.cursor/skills/

# Per-project (committed in repo)
cp -r skills/cursor-audit /path/to/your-project/.cursor/skills/
```

## Validate

```bash
pip install git+https://github.com/cemini23/vet.git
vet skills/cursor-audit/SKILL.md --profile skillmd --strict
```

## Invoke

In Cursor chat:

- `cursor audit on <target>`
- `/cursor-audit mode: security`
- `council audit on briefs/my-brief.md`
- `quick cursor audit on scripts/foo.sh`

## Toolkit stack

| Layer | Tool |
|-------|------|
| Static skill/brief gates | [vet](https://github.com/cemini23/vet) |
| Multi-model qualitative review | **cursor-audit** (this skill) |
| Third-party repo adoption | [phase0](https://github.com/cemini23/phase0) |
| Wiki graph health | [wikilint](https://github.com/cemini23/wikilint) |

Run **vet** and **cursor-audit** on adoption briefs — static REJECT overrides multi-model SHIP.

## Docs

- Wiki: [cursor-audit entity page](https://github.com/cemini23/cemini-claude-code-CCC/blob/main/wiki/entities/skills/cursor-audit.md)
- Model matrix: [reference.md](reference.md)
- Examples: [examples.md](examples.md)

## License

MIT — see [LICENSE](../../LICENSE) in agent-toolkit-demo root.
