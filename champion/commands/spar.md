---
description: War-game an offer negotiation. The champion builds the opposition from research + the email thread, spars them across rounds, then hands you the exact next move to send, in your voice, holding the line you'd fold on.
argument-hint: <offer details, company, and the email thread so far, paste it, or name the company to pull from Gmail>
---

> **Plugin note:** this command ships in the `champion` plugin, so every council agent it names is a plugin agent. When spawning any agent mentioned below, use the `champion:` prefix for the agent type (e.g. `champion:historian`, `champion:north-star`, `champion:viewer`).
>
> **Setup gate:** before doing anything else, check that `~/.champion/dossier/PROFILE.md` exists. If it does not, stop immediately and tell the user, politely, that the council cannot work without knowing who it fights for: run `/champion:setup` first (a 20–30 minute interview). Do not proceed in any form until setup is complete.

# /spar, the champion negotiates the offer

The offer / situation: **$ARGUMENTS**

The war-game. Where `/negotiate` hands you a plan, this puts the champion **in the ring against a live opponent**: a model of the actual counterparty, built from research and the real thread, and fights the negotiation round by round.

**The whole reason this exists:** the fold, recorded in `~/.champion/dossier/PROFILE.md`, is what makes the user concede, and an offer in hand is exactly where folding costs the most. The champion holds the line *for* them.

If the user ran this company through the gauntlet, read the decisions log at `~/.champion/records/decisions-log.md` (location per `~/.champion/dossier/context/records.md`) for the research and angle already on file.

## 1, Read the user's side

- `~/.champion/dossier/PROFILE.md`: the money numbers, the fold, the sabotage pattern, what they'll drift toward vs. what they actually want
- `~/.champion/dossier/CAREER.md`: the truth under each résumé line. Their leverage; **most people undersell theirs.** Price them correctly.
- `~/.champion/dossier/VALUES.md`: **the non-negotiables.** Never let them trade what they'd die on the hill for, for money.

## 2, Get the thread

- If the thread is pasted in `$ARGUMENTS`, use it
- If the user named the company/recruiter, pull the thread via the Gmail MCP (`search_threads` → `get_thread`) and confirm you've got the right one before modeling from it
- If there's no thread yet (just an offer), model from research alone, say so upfront

## 3, Build the opposition (spawn `researcher` + `customer`)

Spawn in parallel:
- **`researcher`**: company runway/finances, comp bands for this role, hiring urgency, recent news
- **`customer`**: inhabit the counterparty's head; read the email thread for tells

Assemble the counterparty dossier: who they are, their incentives and pressure, budget ceiling and BATNA, style and tells from the thread.

## 4, Set the user's plan

- **Target**: the real ask, set high (anchor to the money numbers in `~/.champion/dossier/PROFILE.md`, not the safe number they'll drift to)
- **Walkaway**: the floor + their BATNA (per `PROFILE.md` and `CAREER.md`, what they walk back to; a real BATNA means they are not desperate)
- **Non-negotiables**: from `~/.champion/dossier/VALUES.md`, first
- **The fold point**: name the exact moment in *this* negotiation they'll be tempted to cave

## 5, The war-game

Run the negotiation as live sparring, a few rounds:
- **Champion makes the move** (anchor / counter / hold)
- **Opponent responds in character**: using the dossier: counters, anchors low, squeezes, goes silent, applies "this is our final number" pressure
- **Champion adapts**: and at every concede-shaped moment, names the fold: *"You're about to give this away so they won't be mad. Don't, here's why they don't walk."*

Run it until the winning move is clear or until the right play is to hold and wait. Keep on-screen rounds tight, the exchange, not a transcript.

## 6, Output

```
OPPONENT: <who, their ceiling, their pressure, key tell from the thread>
PLAN: target <X> | walkaway <floor + BATNA> | non-negotiables <from VALUES.md>
WAR-GAME: <the rounds in brief, your move → their likely response → your hold>
FOLD POINT: <where they'll cave, and the line that holds instead>

YOUR NEXT MOVE, ready to send:
<the actual email/message, in the user's voice (~/.champion/dossier/VOICE.md), for the current move only>
```

Draft only the **current** move. The user sends it themselves. Where you held firm on a line they might want to soften, **tell them not to soften it**: that instinct is the fold, not strategy.
