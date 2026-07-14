# 🤝 Contributing to Champion OS

Thanks for wanting to make the mirror sharper. This project is small and opinionated; contributions are welcome when they respect what it is.

## ⚖️ The one law

**The engine is generic. The dossier is personal. No personal fact ever lives in the engine.**

Everything in this repository is engine: agents, commands, references, the gauntlet spec. It must work for *anyone* who completes `/champion:setup`: a founder, a freelancer, an office veteran. Any PR that hardcodes a person's goal, numbers, history, employer, named pattern, or taste into an engine file will be declined, however useful it was to you. If an agent needs a fact about the user, it reads the dossier:

- The dossier schema (the complete list of files agents may rely on) is [`champion/references/dossier-schema.md`](champion/references/dossier-schema.md). If your change needs a fact the schema doesn't hold, propose the schema change (and the matching `/champion:setup` question) in the same PR.
- Illustrative examples are fine ("e.g. the scatter: a comparison-triggered uproot"); asserted facts are not.

## 🪞 What this project is (and isn't)

Champion OS is an **accountability mirror**: professional growth through honest, adversarial counsel. Soft on the person, hard on the truth. When contributing, protect both halves:

- **Don't soften the teeth.** The prosecutor tries to kill ideas. The viewer bails on weak hooks. The maintainer refuses merges. PRs that sand the personas down into agreeable assistants defeat the point.
- **Don't sharpen them into cruelty.** The kick lands because it's loving. The moment a persona reads as contempt for the person, it's a bug.
- It's not therapy, not a life coach, not a general assistant. Scope additions should be professional-growth mechanisms where having a champion changes the outcome.

## 🗺️ Repository layout

```
champion/                    the plugin (this is what installs)
├── .claude-plugin/plugin.json
├── commands/                slash commands: pipelines that orchestrate agents
├── agents/                  the council: one persona per file
├── references/              methodology docs the commands read
├── gauntlets/README.md      the canonical three-round spec
└── interview/INTERVIEW.md   the interview philosophy behind /champion:setup
.claude-plugin/marketplace.json   lets this repo act as a plugin marketplace
```

## 🛠️ Development

```bash
# run a session with your working copy loaded
claude --plugin-dir ./champion

# validate structure and frontmatter before pushing
claude plugin validate ./champion
```

To test end to end: from an empty directory (and ideally a scratch `~/.champion`), run `/champion:setup`, then `/champion:gut-check` on something real. The gate matters: every command except setup must refuse to run when `~/.champion/dossier/PROFILE.md` is missing.

## 🚦 Rules of the road

1. **YAML frontmatter must parse.** Quote any `description:` or `argument-hint:` value containing a colon-space or leading special character. `claude plugin validate` catches this; run it.
2. **Keep the contracts.** Agents end with an output contract (the RETURN/format block) that commands depend on. Change a contract only with the commands that consume it, in the same PR.
3. **Commands spawn agents with the `champion:` prefix** because plugin agents are namespaced. Each command carries a note saying so; keep it.
4. **No model pins.** Agents inherit the user's session model. Don't add `model:` frontmatter unless there's a strong argument, made in the PR.
5. **Paths:** engine files reference each other via `${CLAUDE_PLUGIN_ROOT}/...`; user data lives under `~/.champion/` (dossier, records, work products). No absolute paths from anyone's machine.
6. **Preserve dissent, preserve privacy.** Gauntlet output rules (dissent verbatim, records described in shape not detail) are load-bearing; don't optimize them away.
7. **One persona per agent file.** If a new voice is genuinely new, add an agent; if it's a variation, sharpen the existing one.

## 🔀 Pull requests

- Keep them small and reviewable: one concern per PR. (This project ships a command for oversized PRs; don't make us use it on yours.)
- Say what you changed and *why the mirror is better for it*, not just what the diff does.
- New commands or agents should come with: the persona/pipeline file, README table entries, and a note on which gauntlet round(s) they join.
- Never include a real dossier, real records, or excerpts of either, not even as test fixtures. Invent fixtures from whole cloth.

## 🐛 Reporting problems

Open an issue with the command you ran, what you expected the council to do, and what it did instead. Transcript excerpts help; scrub them of anything personal first; the maintainers should never see the contents of your dossier.
