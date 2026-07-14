# Champion OS

**An accountability mirror for your professional life.** A council of adversarial advisors, run inside [Claude Code](https://claude.com/claude-code), that tells you what you need to know instead of what you want to hear.

It is not a yes-machine, and it is not therapy. Bring it an idea, a job offer, a negotiation, a draft, or a pull request, and it renders an honest verdict measured against two questions:

1. **Is it any good?**
2. **Is it right for *you*** — your goal, your values, your bandwidth, your patterns?

An idea can be excellent and still be wrong for you right now. This is the tool that says so — empathy first, then the kick.

## How it works

Before anything runs, you complete a **20–30 minute setup interview**. One question at a time, multiple choice where a choice fits, every question explaining why it's asked. It surfaces the goal everything will align to (your north star), your money numbers, the pattern that sabotages you, the hill you'll die on, your career spine, and your voice — and writes them to a **dossier** at `~/.champion/` on your machine.

From then on, every command reads that dossier. The council isn't a set of generic critics; it's *you*, held to what you said you wanted.

Decisions go through a **gauntlet**: three rounds (Diverge → Stress → Converge), a 1–5 verdict, and the strongest dissent preserved verbatim. Verdicts accumulate in a local decisions log that the council reads next time — grade its past calls with `/champion:log-outcome` and it gets smarter the longer you use it.

## Install

```bash
claude plugin marketplace add robconery/champion
claude plugin install champion --scope user
```

Then, in any Claude Code session:

```
/champion:setup
```

Nothing else unlocks until the interview is done — the council can't fight for someone it doesn't know.

## The commands

| | Command | What it does |
|---|---------|--------------|
| **Setup** | `/champion:setup` | The interview. Builds or revises your dossier. |
| **Advise** | `/champion:gut-check` | Fast pass on an impulse: your true path, or your sabotage pattern wearing a new coat? |
| | `/champion:mirror` | You, talking to you. No verdict — clarity and the real motive. |
| | `/champion:triage-email` | What's really going on in an email: the ask, the power dynamic, the fold-risk. |
| | `/champion:simulate` | Run the tape forward: plausible outcomes with honest odds. |
| **Judge** | `/champion:evaluate` | The full gauntlet on any real "should I do this?" |
| | `/champion:apply` | A job listing through the gauntlet; on GO, a tailored resume and cover letter. |
| **Negotiate** | `/champion:negotiate` | Target, walkaway, and pre-arming against your specific fold. |
| | `/champion:spar` | War-game a live offer round by round; the exact next move to send. |
| **Create** | `/champion:write` | Draft → voice-check → de-AI scrub → your approval. Nothing sends until you say so. |
| | `/champion:video` | A YouTube video through a three-round gauntlet into a full shoot package. |
| | `/champion:course` | Course design, gates first — it's a big bandwidth bet. |
| | `/champion:tune-marketing` | One-round critique panel against the flywheel playbook. |
| **Review** | `/champion:review-pr` | A pull request on trial: mapped, attacked, defended, 1–5 merge verdict. |
| **Memory** | `/champion:log-outcome` | Grade a past verdict against reality so the council learns from truth. |

Full details in [champion/README.md](champion/README.md); the gauntlet spec is in [champion/gauntlets/README.md](champion/gauntlets/README.md).

## Privacy

Your dossier is the most personal file set you'll ever hand a tool: your fears, your money, your failures. It lives **only** in `~/.champion/` on your machine. The plugin never ships, syncs, or transmits it, and deleting that folder erases the mirror completely. It is not part of this repository and never should be — see [CONTRIBUTING.md](CONTRIBUTING.md).

## Contributing

The one law of this codebase: **the engine is generic; the dossier is personal; no personal fact ever lives in the engine.** Read [CONTRIBUTING.md](CONTRIBUTING.md) before opening a PR.

## License

[MIT](LICENSE) © Rob Conery
