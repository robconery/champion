---
description: Put a pull request on trial. A three-round adversarial gauntlet, map the diff, attack it from every angle a real review would (correctness to spec, quality, maintainability, standards, security, scope), with the author defending, then a 1–5 merge verdict. Built for AI-generated PRs that are too big for one human to read.
argument-hint: <PR number, PR url, or nothing to review the current branch's diff>
---

> **Plugin note:** this command ships in the `champion` plugin, so every council agent it names is a plugin agent. When spawning any agent mentioned below, use the `champion:` prefix for the agent type (e.g. `champion:historian`, `champion:north-star`, `champion:viewer`).
>
> **Setup gate:** before doing anything else, check that `~/.champion/dossier/PROFILE.md` exists. If it does not, stop immediately and tell the user, politely, that the council cannot work without knowing who it fights for: run `/champion:setup` first (a 20–30 minute interview). Do not proceed in any form until setup is complete.

# /review-pr, put the PR on trial

Subject: **$ARGUMENTS**

A critique gauntlet for code, not a "should the user do this" decision. It exists to make an oversized, AI-generated PR reviewable by one human, and to find the truth about whether it should merge. The **orchestrator** runs the rounds. The defender is the **author** (the developer who wrote the code, on trial), not the champion.

The gate that matters most: **is the code correct to the spirit of the spec?** Everything else, quality, maintainability, standards, security, scope, is weighed under that.

## 0, Fetch and frame

- If `$ARGUMENTS` is a PR number or URL: `gh pr view <pr> --json title,body,files,additions,deletions,baseRefName,headRefName` and `gh pr diff <pr>`. Pull the linked issue/spec if referenced.
- If empty: review the current branch's diff against the main branch (`git diff <main>...HEAD`), treat the branch/commit messages and any linked task as the spec.
- Read the repo's standards: `CLAUDE.md`, the `.claude/` directory, and any lint/format/structure config. These are the house rules the senior-engineer judges against.

If the diff can't be fetched, stop and say so, don't review a guess.

## 1, Seed, Round 1: Map (spawn in parallel, no attacks yet)

- **`cartographer`** → the compression map: the shape, the load-bearing 20% to actually read, the blast radius, and anything changed that the spec doesn't explain.
- **`spec-keeper`** → the ground truth: the intent (spirit), explicit + implicit acceptance, the standards in play, what was left to judgment.

Both briefs feed every voice. Print the cartographer's map to screen early, it's the thing that makes the rest reviewable.

## 2, Round 2: Trial (the adversarial core)

Spawn the attackers in parallel, each given the diff + both seed briefs:
- **`correctness-prosecutor`**: the gap between code and the spirit of the spec; test integrity. (Weight this heaviest.)
- **`senior-engineer`**: quality, maintainability (cost to change later), standards adherence.
- **`security-reviewer`**: reachable security findings in this diff, with severity and fix.
- **`scope-critic`**: over-engineering, scope creep, and the split proposal if it's too big.

Then run the **iterative rebuttal, capped**:
1. Hand the **`author`** all charges. The author returns CONCEDED / DEFENDED / PARTIAL for each.
2. For any charge the author DEFENDED or called PARTIAL, hand it back to the originating voice for **one** press: hold or concede.
3. Stop after that exchange (max ~2 passes per charge). A charge unresolved after the press is recorded as **contested**, preserved verbatim, not smoothed.

The **champion** sits in once here: flag if the user is about to wave through a big PR just to avoid friction, or kill a sound one out of irritation at the volume. The user's sabotage pattern, named in `~/.champion/dossier/PROFILE.md`, shows up in review too.

## 3, Round 3: Converge + verdict

No new spawns. The orchestrator resolves what survived the trial into the final picture. The **`maintainer`** renders the 1–5 merge gate from the surviving (post-defense) findings.

## 4, Output (screen only, verdict-first, no round-by-round transcript)

```
MERGE VERDICT: <1–5> → <MERGE | MERGE WITH FIXES | CHANGES REQUESTED | SEND BACK | CLOSE>
THE CALL: <one line>

THE MAP: <cartographer's compression — N files, the load-bearing few, blast radius>
SPEC FIT (the gate): <does it honor the spirit? the single biggest gap, or "clean">

BLOCKERS (must fix before merge — survived the author's defense):
  - <finding> [file:line]
NON-BLOCKING (nits, follow-ups):
  - <finding> [file:line]
CONTESTED (unresolved after rebuttal — the user decides):
  - <charge vs. defense, both sides, one line each>

SPLIT?: <the N smaller PRs to break this into, in order — or "scope is fine">
TOP 3 FIXES, IN ORDER:
  1. <highest-leverage fix first>
  2.
  3.
```

Screen only. Nothing is posted to the PR and nothing is written to the decisions log, this is a code-review tool, not a path decision. If the user wants findings as inline PR comments later, that's a follow-up they ask for explicitly.

> Each spawned agent returns text only, never writes to disk or to GitHub. If an agent returns boilerplate or goes off-task, re-run it once; if it fails again, run that voice inline rather than stalling the trial.
