---
description: Run the full gauntlet on an idea, venture, job listing, or offer. Three rounds, the whole council, a 1–5 verdict, logged. Use for any real "should I do this?" decision.
argument-hint: <the idea / venture / @link to a job or offer>
---

> **Plugin note:** this command ships in the `champion` plugin, so every council agent it names is a plugin agent. When spawning any agent mentioned below, use the `champion:` prefix for the agent type (e.g. `champion:historian`, `champion:north-star`, `champion:viewer`).
>
> **Setup gate:** before doing anything else, check that `~/.champion/dossier/PROFILE.md` exists. If it does not, stop immediately and tell the user, politely, that the council cannot work without knowing who it fights for: run `/champion:setup` first (a 20–30 minute interview). Do not proceed in any form until setup is complete.

# /evaluate, run the gauntlet

Subject: **$ARGUMENTS**

Full decision engine. Read `${CLAUDE_PLUGIN_ROOT}/gauntlets/README.md` first. The **orchestrator** agent runs the session; the **champion** is the user's advocate inside the room.

## 0, Frame the conversion

Identify what's actually being decided and who the buyer is:

- **Venture / product** → customer = the target buyer; researcher fetches market, comps, pricing, demand
- **Job listing** → customer = the hiring manager *and* the user-as-candidate; researcher fetches company (funding, news, sentiment), role, and salary bands. If a URL is in the argument, fetch it first.
- **Offer / contract / partnership** → customer = the counterparty; researcher fetches comps and the other side's incentives
- **Pure idea** → customer = whoever the idea ultimately has to win over

## 1, Seed (spawn in parallel, before any rounds)

Spawn two agents simultaneously. Each returns its output contract:

- **`researcher`** → the fact brief (balanced, sourced)
- **`historian`** → precedent + sabotage-pattern/brave-walk read from the decisions log at `~/.champion/records/decisions-log.md` (location per `~/.champion/dossier/context/records.md`) and `~/.champion/dossier/CAREER.md`

Both briefs feed every voice in every round.

## 2, Round 1: Diverge

Spawn in parallel, giving each the researcher brief:
- **`expansionist`** (leads), biggest version, the nugget, the reframe
- **`opportunist`**: money math and leverage

No killing yet. Then synthesize the round: the biggest version, the nugget, the money thesis.

## 3, Round 2: Stress

Spawn in parallel, each given the briefs + Round 1 synthesis:
- **`prosecutor`**: build the case to kill
- **`protectionist`**: surface risks and mitigations
- **`operator`**: feasibility and opportunity cost
- **`north-star`**: values and path alignment
- **`opportunist`**: sharpen the money thesis under pressure
- **`customer`**: buyer verdict, top objection (in first person, in character, they role-play the actual buyer, not describe one)

This is where it breaks if it's going to. Synthesize, and **preserve the strongest dissent verbatim**; do not smooth it.

Between rounds, **the champion** integrates or defends each point on the user's behalf, and flags any moment the fold or the sabotage pattern (per `~/.champion/dossier/PROFILE.md`) is steering the decision.

## 4, Round 3: Converge

No new spawns. Synthesize what survived into a real recommendation. The **customer** returns the final 1–5 score.

## 5, Output (tight, no round-by-round transcript on screen)

Present ONLY:

```
RECOMMENDATION: <the call, one line>
VERDICT: <1–5> → <action>
WHY:
  - <load-bearing reason>
  - <load-bearing reason>
DISSENT: <strongest minority view, one line>
CHEAPEST 48-HOUR TEST: <the smallest, fastest thing the user can do in ~2 days to validate the riskiest assumption BEFORE building anything>
```

The **48-hour test** is the most important line in the verdict. Not "someday research this", the concrete thing the user can start now and learn from this week. Make it specific enough to act on without asking a follow-up.

Then **append the FULL verdict** (round detail, what each voice surfaced, synthesis, dissent verbatim) to the decisions log at `~/.champion/records/decisions-log.md` (or wherever `~/.champion/dossier/context/records.md` points), newest entry at the top.

> Each spawned agent returns text only, never writes to disk. If an agent returns boilerplate or goes off-task, re-run it once; if it fails again, run that voice inline rather than stalling the gauntlet.
