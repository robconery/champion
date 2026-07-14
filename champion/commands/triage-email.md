---
description: Read an email and think through what's really going on, subtext, the ask, the power dynamic, and where the fold-risk hides. No council. Optional reply draft in voice.
argument-hint: <paste the email, or name the sender/thread to pull from Gmail>
---

> **Plugin note:** this command ships in the `champion` plugin, so every council agent it names is a plugin agent. When spawning any agent mentioned below, use the `champion:` prefix for the agent type (e.g. `champion:historian`, `champion:north-star`, `champion:viewer`).
>
> **Setup gate:** before doing anything else, check that `~/.champion/dossier/PROFILE.md` exists. If it does not, stop immediately and tell the user, politely, that the council cannot work without knowing who it fights for: run `/champion:setup` first (a 20–30 minute interview). Do not proceed in any form until setup is complete.

# /triage-email

The email: **$ARGUMENTS**

No council. The champion reads this 1:1. Your job is to see what the user might miss when they're reading it through the fold.

If `$ARGUMENTS` names a sender or thread rather than pasting the content, pull it via the Gmail MCP (`search_threads` → `get_thread`) before proceeding.

Optionally spawn the **`historian`** agent if there's a relationship or thread history worth recalling ("we've been here with this person before").

## Read first

- `~/.champion/dossier/PROFILE.md`: the fold, what makes the user cave, over-apologize, or concede to keep the peace. The #1 thing to watch for in how they will want to respond.
- `~/.champion/dossier/VALUES.md`: the non-negotiables. Watch for anything that's an inch toward giving one away.

## What to surface

- **The real ask.** What does the sender actually want, under the politeness, the framing, the length? Separate the stated ask from the real one.
- **The power dynamic.** Who needs whom here? Is the user negotiating from strength and about to act like they aren't?
- **The fold-risk.** Where will the fold make the user cave, apologize for something that isn't their fault, say yes to keep the peace, soften a fair boundary? **Name the exact sentence they'll be tempted to write, and tell them not to.**
- **What the user actually wants** from this exchange, and whether the obvious reply gets them there.

## Output

```
WHAT'S GOING ON: <the real read, 2–4 sentences>
THEY WANT: <the actual ask under the surface>
THE TRAP: <where the fold will make the user cave, and the line to hold instead>
YOUR MOVE: <recommended stance>
```

If the user wants a reply, draft it in their voice (`~/.champion/dossier/VOICE.md`), warm where it should be, but holding the line where they'd otherwise give it away. Offer it; don't assume they want to send it.
