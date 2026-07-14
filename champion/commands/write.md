---
description: The writing gauntlet. Anything in the user's voice goes through draft, voice-check, and a de-AI scrub, then is handed to the user in markdown for their edit and approval. Rendering or sending happens only after they approve. All writing is theirs, checked by them.
argument-hint: <type + topic, e.g. "newsletter on agent fleets" or "cover letter for Pinecone">
---

> **Plugin note:** this command ships in the `champion` plugin, so every council agent it names is a plugin agent. When spawning any agent mentioned below, use the `champion:` prefix for the agent type (e.g. `champion:historian`, `champion:north-star`, `champion:viewer`).
>
> **Setup gate:** before doing anything else, check that `~/.champion/dossier/PROFILE.md` exists. If it does not, stop immediately and tell the user, politely, that the council cannot work without knowing who it fights for: run `/champion:setup` first (a 20–30 minute interview). Do not proceed in any form until setup is complete.

# write, the writing gauntlet

The piece:

$ARGUMENTS

This is a process, not a one-shot. The machine drafts and cleans. The user gets the last word. The center of gravity is their voice, and the iron rule is that nothing leaves in markdown form until they have edited and approved it.

## Read first

- `~/.champion/dossier/VOICE.md`: the rubric, taste, aesthetic, and their actual writing samples. The positive target. **Write through it.** If the samples are thin, say so and ask for more rather than guessing at a voice.
- `${CLAUDE_PLUGIN_ROOT}/references/voice-scrub.md`: the cleaning checklist. The list of AI tells to strip.
- For a **newsletter or marketing email**: `${CLAUDE_PLUGIN_ROOT}/references/marketing-playbook.md`: teach a real outcome, link the lead magnet, invite softly. The newsletter is a flywheel asset, not an announcement.

## The pipeline

1. **Clarify the job.** What is the piece, who reads it, what should they feel or do after. If it is not obvious from `$ARGUMENTS`, ask one tight question, then go.

2. **Draft in voice** (`VOICE.md`). Do not write "content." Write the way the user talks on the page: a real opinion, stated, then earned.

3. **Voice-check.** Read it whole against `VOICE.md`. Does it sound like the user or like a feed. Fix where it drifts.

4. **Scrub** against `${CLAUDE_PLUGIN_ROOT}/references/voice-scrub.md`. Run the two sweeps that always catch something: the em-dash sweep and the punchy-fragment sweep. Then the rest of the ban list.

5. **Adversarial verify.** Spawn a fresh read whose only job is to hunt remaining tells (em-dashes, arrows, "here's the thing", staccato fragments, contrast-formula sentences, hype words, hedges). Whatever it flags, fix, then verify again. Repeat until it comes back clean. Do this as a separate pass so it is not the same mind that wrote it.

6. **GATE for public/marketing pieces (optional but default-on for anything public):** spawn the **`customer`** agent. Does the opening earn the next line. Would the reader keep going or click the CTA. Apply the top fix, then re-run the scrub on whatever you changed.

7. **Hand to the user in markdown.** Present the clean draft. Note any place you deliberately held an opinion they might want to soften, and tell them not to (if `~/.champion/dossier/PROFILE.md` names a fold, hedging the true thing is how it shows up in prose). Then **stop and wait.** They edit and approve.

## Output and the approval gate

- Deliver the finished piece **in markdown**, in their voice, scrubbed clean. For a newsletter or email, include the subject line(s) and the CTA.
- **Do not render to PDF, publish, post, or send anything until the user approves the markdown.** When they approve (with or without their own edits), then and only then produce the final form they asked for.
- If the user edits the markdown themselves, treat their version as the source of truth. Run the scrub once more on the merged result so nothing slipped back in, but never overwrite their wording with yours.
