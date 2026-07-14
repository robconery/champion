---
description: Design a course, curriculum, modules, lessons, scripts. A production pipeline that front-loads council gates, because a course is a big bandwidth bet.
argument-hint: <course topic / working title>
---

> **Plugin note:** this command ships in the `champion` plugin, so every council agent it names is a plugin agent. When spawning any agent mentioned below, use the `champion:` prefix for the agent type (e.g. `champion:historian`, `champion:north-star`, `champion:viewer`).
>
> **Setup gate:** before doing anything else, check that `~/.champion/dossier/PROFILE.md` exists. If it does not, stop immediately and tell the user, politely, that the council cannot work without knowing who it fights for: run `/champion:setup` first (a 20–30 minute interview). Do not proceed in any form until setup is complete.

# course

The course:

$ARGUMENTS

Create mode, like `video`: but a course is a **major bandwidth commitment**, so the gates run *first* and hard. We do not design a curriculum for something that shouldn't be built or that the user can't afford to build right now.

## Read first

- `~/.champion/dossier/VOICE.md`: the voice for all lesson content.
- `~/.champion/dossier/PROFILE.md` + `~/.champion/dossier/NORTH-STAR.md`: the contract (if any), the work situation, and what's already on the plate.
- `${CLAUDE_PLUGIN_ROOT}/references/marketing-playbook.md`: how a course feeds (or competes with) the user's existing offers.

## Gates first (spawn in parallel before designing anything)

Spawn these agents up front. If they don't clear, say so plainly and stop, the most valuable outcome here can be "not now":

- **`operator`**: bandwidth + opportunity cost. Honest hours to build *and maintain* it. Does it starve the user's core work or violate the contract in `~/.champion/dossier/PROFILE.md` (if any)? What gets dropped?
- **`customer`**: would a buyer actually pay for this, and at what price? Top objection.
- **`researcher`**: is there real demand? Who already teaches this, at what price, and where's the gap?

**Gate verdict: GO / GO-LATER / NO.** Only proceed to design on GO.

## If GO, design pipeline

1. **Promise & outcome.** The one transformation the course delivers. Who finishes it and what can they now do?
2. **Curriculum.** Modules in learning order, each with its outcome.
3. **Lessons.** Per module, the lesson breakdown with objectives.
4. **Scripts.** Draft lesson scripts in the user's voice (`~/.champion/dossier/VOICE.md`), starting with the first module.
5. **Offer fit.** How it ties to the user's existing offers and the north star.

## Output

```
GATE VERDICT: <GO / GO-LATER / NO>, <one-line why>
```
On GO, follow with: promise, full curriculum (modules → lessons), first-module scripts, and the offer tie-in. On GO-LATER/NO, give the condition that would change the answer.
