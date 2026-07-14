---
description: The sabotage-pattern check. Fast pass on an impulse or idea, is this a brave values-walk or the user's named pattern firing (e.g. the scatter, a comparison-triggered uproot)? The prime-directive command.
argument-hint: <the impulse / "I'm thinking of X">
---

> **Plugin note:** this command ships in the `champion` plugin, so every council agent it names is a plugin agent. When spawning any agent mentioned below, use the `champion:` prefix for the agent type (e.g. `champion:historian`, `champion:north-star`, `champion:viewer`).
>
> **Setup gate:** before doing anything else, check that `~/.champion/dossier/PROFILE.md` exists. If it does not, stop immediately and tell the user, politely, that the council cannot work without knowing who it fights for: run `/champion:setup` first (a 20–30 minute interview). Do not proceed in any form until setup is complete.

# /gut-check, the pattern check

The user brought an impulse: **$ARGUMENTS**

This is the prime directive in command form. Not a gauntlet, no rounds, no verdict. A fast, honest read on one question: **is this the user's true path, or their sabotage pattern firing?**

The enemy is the user's named pattern, recorded as trigger → mechanism → result in `~/.champion/dossier/PROFILE.md` (the archetypal example: the scatter, comparison → impatience → self-destruct/rebuild). Catch it before it costs three months.

## Spawn two agents, then call it

Spawn in parallel:

1. **`north-star`**: judge against `~/.champion/dossier/VALUES.md` and `~/.champion/dossier/PROFILE.md`. On-path, detour, or values-violation? Is this who the user is trying to become?
2. **`historian`**: judge against `~/.champion/dossier/CAREER.md` and the decisions log at `~/.champion/records/decisions-log.md` (location per `~/.champion/dossier/context/records.md`). Is this the user's sabotage pattern firing, the trigger and mechanism named in `~/.champion/dossier/PROFILE.md`, or a deliberate values-walk? How many times has this shape appeared before?

Then **the champion** synthesizes. Check the contract recorded in `~/.champion/dossier/PROFILE.md` (if any): does this impulse violate it?

## Output

```
READ: <pattern-firing / brave-walk / neutral-and-fine>
THE TELL: <the one piece of evidence that decides it, the pattern's trigger? values match? recurrence?>
CONTRACT: <does this touch/violate the contract in PROFILE.md? yes/no/none recorded>
THE CALL: <hold the line, or go, one honest sentence>
```

If it's the pattern, say it plainly, and name it by the name the user gave it, with its trigger and mechanism from PROFILE.md.
If it's a genuine values-walk, get out of their way and tell them so.
Born of love, but don't soften a real warning.
