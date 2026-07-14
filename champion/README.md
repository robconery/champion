# Champion OS

An **accountability mirror** for your professional life: a council of adversarial advisors, run by Claude Code, that tells you what you need to know instead of what you want to hear. It is *you* — future you, reaching back to keep present you on the path you said you wanted. Empathy first, then the kick.

It is not therapy, and it is not a yes-machine. Bring it an idea, an offer, a negotiation, a draft, or a pull request, and it renders an honest verdict measured against two questions: **is it good**, and **is it right for you** — your goal, your values, your bandwidth, your patterns. An idea can be excellent and still be wrong for you right now. This is the tool that says so.

## Install

```bash
claude plugin marketplace add <this-repo-or-path>
claude plugin install champion --scope user
```

## First run — the interview

Nothing works until the council knows who it fights for. Run:

```
/champion:setup
```

A 20–30 minute interview: one question at a time, multiple choice where a choice fits, and every question explains why it's asked. It surfaces your north star, your money numbers, the pattern that sabotages you, the hill you'll die on, your career spine, and your voice — and writes them to your **dossier** at `~/.champion/`.

**Privacy:** the dossier lives only in `~/.champion/` on your machine. The plugin never ships, syncs, or transmits it. Delete the folder and the mirror is gone. You can revise any section later with `/champion:setup revise`.

## The commands

| Command | What it does |
|---------|--------------|
| `/champion:setup` | The interview. Builds or revises your dossier. Everything else is locked until it's done. |
| `/champion:gut-check` | The fast pass on an impulse: your true path, or your sabotage pattern wearing a new coat? |
| `/champion:evaluate` | The full gauntlet: three rounds, the whole council, a 1–5 verdict, logged. For any real "should I do this?" |
| `/champion:mirror` | You, talking to you. No verdict — clarity and the real motive surfaced. |
| `/champion:simulate` | Run the tape forward: plausible outcomes with honest odds when you push back on a verdict. |
| `/champion:negotiate` | Prep a negotiation: the target, the walkaway, and pre-arming against your specific fold. |
| `/champion:spar` | War-game a live offer negotiation round by round; hands you the exact next move. |
| `/champion:triage-email` | Read an email for what's really going on — the ask, the power dynamic, the fold-risk. |
| `/champion:apply` | A job listing through the gauntlet; on GO, a tailored resume and cover letter in your voice. |
| `/champion:write` | The writing gauntlet: draft → voice-check → de-AI scrub → handed to you for approval. Nothing sends until you say so. |
| `/champion:video` | A YouTube video through a three-round gauntlet into a full shoot package. |
| `/champion:course` | Course design with the gates run first — it's a big bandwidth bet. |
| `/champion:tune-marketing` | One-round critique panel against the flywheel playbook. |
| `/champion:review-pr` | A pull request on trial: mapped, attacked from every angle, defended, and given a 1–5 merge verdict. |
| `/champion:log-outcome` | Grade a past verdict against what actually happened, so the council learns from truth. |

## How the gauntlet works

Three rounds: **Diverge** (the biggest version of the idea, no killing yet), **Stress** (prosecutor, protectionist, operator, and values voices attack it from every angle), **Converge** (synthesis, a 1–5 verdict, and the strongest dissent preserved verbatim). Verdicts and outcomes accumulate in `~/.champion/records/decisions-log.md` — the council reads its own history, so it gets smarter the more you use it and grade it.

The full spec lives in the plugin under `gauntlets/README.md`.

## What it needs from you

Honesty in the interview, and outcomes afterward. The mirror is only as true as the dossier — and it only compounds if you `/champion:log-outcome` what reality did to its verdicts.

## License

MIT © Rob Conery. See the LICENSE file at the repository root.
