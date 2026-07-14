---
description: Grade a past decision or gauntlet verdict against what actually happened, and write it back to the log so the historian learns from truth, not just its own past guesses.
argument-hint: "<which decision: subject or date>"
---

> **Plugin note:** this command ships in the `champion` plugin, so every council agent it names is a plugin agent. When spawning any agent mentioned below, use the `champion:` prefix for the agent type (e.g. `champion:historian`, `champion:north-star`, `champion:viewer`).
>
> **Setup gate:** before doing anything else, check that `~/.champion/dossier/PROFILE.md` exists. If it does not, stop immediately and tell the user, politely, that the council cannot work without knowing who it fights for: run `/champion:setup` first (a 20–30 minute interview). Do not proceed in any form until setup is complete.

# log-outcome

Grade this past call: **$ARGUMENTS**

The council only gets smarter if verdicts get checked against reality. This is the feedback loop. Without it, the historian compounds opinions; with it, it compounds truth.

## Procedure

1. **Find the entry** in the decisions log at `~/.champion/records/decisions-log.md` that matches the argument (by subject or date). (If `~/.champion/dossier/context/records.md` points the log somewhere else, follow it.) Read its Decision, Verdict, Why, and Dissent.
2. **Establish what actually happened.** Ask the user directly for the outcome if it isn't obvious. Did the thing ship? Did it work? Did the predicted upside / risk / objection materialize?
3. **Grade the call honestly:**
   - Was the verdict right, wrong, or right-for-the-wrong-reasons?
   - **Did the dissent turn out to be correct?** (This is the highest-value signal, the minority view we preserved is exactly what we're checking.)
   - What did the council miss, and which voice should have caught it?
4. **Write it back.** Append a dated follow-up to that entry in `~/.champion/records/decisions-log.md` (edit the file in place, directly under the matching entry):

```
**Outcome (YYYY-MM-DD):** what actually happened.

**Verdict held?** right / wrong / right-for-wrong-reasons, and whether the dissent was vindicated.

**Lesson for the council:** the one thing the historian should carry forward (e.g. "operator under-weighted maintenance cost again").
```

## Output

A short summary: the original call, what happened, whether it held, and the lesson now recorded for next time. Keep it honest, a wrong verdict logged truthfully is worth more than a flattering one.
