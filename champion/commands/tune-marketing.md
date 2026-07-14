---
description: Fine-tune a marketing effort against the flywheel playbook. A one-round critique panel, not a full gauntlet. Returns concrete fixes (and the rewrite if it's copy).
argument-hint: "<the asset/effort: email, landing copy, video idea, launch plan, funnel step>"
---

> **Plugin note:** this command ships in the `champion` plugin, so every council agent it names is a plugin agent. When spawning any agent mentioned below, use the `champion:` prefix for the agent type (e.g. `champion:historian`, `champion:north-star`, `champion:viewer`).
>
> **Setup gate:** before doing anything else, check that `~/.champion/dossier/PROFILE.md` exists. If it does not, stop immediately and tell the user, politely, that the council cannot work without knowing who it fights for: run `/champion:setup` first (a 20–30 minute interview). Do not proceed in any form until setup is complete.

# tune-marketing

The marketing effort:

$ARGUMENTS

This is Optimize mode, a focused critique loop, **one round, not three**. The spec it optimizes against is the flywheel.

## Read first (the spec)

- `${CLAUDE_PLUGIN_ROOT}/references/marketing-playbook.md`: the whole system on one page: the flywheel, the three disciplines (one engine/asset/offer; the build is the marketing; value over scheme), and the cadence. Every fix must fit on that page or it's a scheme, not a strategy.
- `~/.champion/dossier/VALUES.md`: the user's brand line, the values every piece of marketing has to honor.

## The panel (one round, spawn in parallel)

Spawn these agents on the effort:

- **`customer`**: does the message land? Would I click / open / convert? Top objection, in one blunt line.
- **`researcher`**: what's actually working for this tactic in the wild, and what are the strongest comparable players in the user's space doing here?
- **`opportunist`**: is this the highest-leverage move, or busywork dressed as marketing? Where's the real return?
- **`north-star`**: the value-over-scheme check: is this teaching a real outcome and inviting softly, or has it drifted into selling/hype/ego?

## Synthesize (you, the champion)

Score the effort against the three disciplines and the cadence. Then give the user the fixes, concrete, not vague.

## Output

```
VERDICT: <ship / revise / kill>
FITS THE FLYWHEEL?: <which stage it serves, or where it breaks discipline>
TOP 3 FIXES:
  1. <fix>
  2. <fix>
  3. <fix>
THE REWRITE: <if it's copy, the revised version in the user's voice (per ~/.champion/dossier/VOICE.md), else "n/a">
```

The default move when stuck is the playbook's: make the free thing more valuable, not the scheme more clever.
