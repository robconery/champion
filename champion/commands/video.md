---
description: "Build a YouTube video through a three-round gauntlet into a full production package, Round 1 finds the sharpest angle and hook, Round 2 architects the retention structure and writes the script, Round 3 scouts and prototypes the demo and builds the scene-by-scene direction sheet. Output: a scene & direction sheet (shots, demo, code, prompts, checklist) followed by a full voiceover script, in the user's voice."
argument-hint: '<topic / angle, or "next video">'
---

> **Plugin note:** this command ships in the `champion` plugin, so every council agent it names is a plugin agent. When spawning any agent mentioned below, use the `champion:` prefix for the agent type (e.g. `champion:historian`, `champion:north-star`, `champion:viewer`).
>
> **Setup gate:** before doing anything else, check that `~/.champion/dossier/PROFILE.md` exists. If it does not, stop immediately and tell the user, politely, that the council cannot work without knowing who it fights for: run `/champion:setup` first (a 20–30 minute interview). Do not proceed in any form until setup is complete.

# video

The video:

$ARGUMENTS

Create mode. A **three-round gauntlet** wrapped around a production pipeline. Round 1 decides the video is worth making and finds the sharpest angle. Round 2 architects the retention structure and writes the script. Round 3 turns the approved script into a real shoot package, scene-by-scene direction, a scouted-and-prototyped demo, runnable code and exact prompts, and a checklist the user walks through. The spine is the user's voice, the retention model, and the flywheel.

The bar: when this finishes, the user should be able to read the sheet top to bottom, tick boxes, tweak what they want, and film. Not "interesting." **Usable.**

## Read first

- `~/.champion/dossier/VOICE.md`, the voice. Non-negotiable; everything written passes through it. If the samples are thin, say so and ask for more rather than guessing.
- `${CLAUDE_PLUGIN_ROOT}/references/video-direction.md`: the production spec: the structure model (MKBHD-clean + retention spine), the scene-sheet format, the demo scout-and-prototype protocol, the checklist. This governs shape and retention.
- `${CLAUDE_PLUGIN_ROOT}/references/voice-scrub.md`: the deslop checklist (used in Round 2).
- `${CLAUDE_PLUGIN_ROOT}/references/marketing-playbook.md`: the build *is* the marketing: each video teaches a real outcome and the lead magnet is the exact thing demoed.
- Content conventions: each video is a **self-contained folder** `~/.champion/work/videos/NN-slug/` (episode number = production order, never changes; create the folders on demand) holding `script.md` (the scene sheet + the voiceover script), a folder `README.md`, and a `shorts/` subfolder. Frontmatter on `script.md`: `episode`, `title`, `status`, `format`, `length`, `publish_date`, `version`. Add a row to the index at `~/.champion/work/videos/README.md`. The user's shared lead magnet, if one exists, lives at `~/.champion/work/lead-magnet/` and is NOT copied into episode folders, videos reference it.

Target length: **~15 minutes, 20 if the subject is dense.** Reference channel: **MKBHD**: clean, calm, no fluff, high craft.

## Round 1, Angle & Hook (is it worth making, and what's the sharpest version)

Draft the angle around the real outcome it teaches, not the topic, plus 2–3 hook + title options. If the audience or demand is unclear, seed a quick **`researcher`** brief first. Then spawn in parallel:

- **`expansionist`**: the biggest version of the angle, the reframe, the nugget worth building the video on.
- **`north-star`**: on-path, or ego / off-brand? If it's off-path, stop or refit before going further.
- **`viewer`**: given the title + hook options, would I click this over my feed? Which hook survives the click test? Top objection.

Synthesize: the chosen angle and hook. If north-star says off-path, or no hook earns the click, fix that before scripting. **Don't architect a video that shouldn't exist.**

## Round 2, Structure & Script (engineer the retention, then write it)

1. **`showrunner` (structure).** Hand the locked angle to the showrunner. It returns the retention skeleton: cold open beat-by-beat, the 5–7 setup→tension→payoff loops in order, the demo loop marked, payoffs built backward first, rehooks at every seam, and the retention pre-empts (30-sec cliff, mid-video sag, demo dead-air, pre-CTA drop). This is the architecture the script gets written onto.
2. **Script.** Write the full script in the user's voice (`~/.champion/dossier/VOICE.md`) onto the showrunner's skeleton. Spoken cadence, not prose. Every loop opens and closes where the showrunner placed it; every seam carries its rehook.
3. **Deslop.** Run the script through `${CLAUDE_PLUGIN_ROOT}/references/voice-scrub.md`. The em-dash sweep and the punchy-fragment sweep first, then the rest. A spoken script has to lose both the written-prose tells and the AI cadence and still sound like the user actually talking.
4. **`viewer` (retention test).** On the real script now: instant click-away or hold? First ten seconds? Where's the drop-off beat? Does the payoff land? Apply **THE ONE FIX** it names, then re-scrub anything you changed.

Round 2 ends with an approved script. Do not move to production direction until the retention test passes (viewer ≥ 4, or the named fix applied).

## Round 3, Production & Direction (turn the script into a shoot package)

1. **Scout the demo.** What single outcome does it prove? What's the most *showable* version? Propose 1–2 options with a recommendation (`${CLAUDE_PLUGIN_ROOT}/references/video-direction.md`, Part 3). If the video genuinely has no demo, say so and skip to step 3.
2. **Prototype the demo in the sandbox.** Actually build and run it. Confirm it works end to end. Capture the **real, tested code**, the **exact commands**, and any **copy-pasteable prompts**. Note the on-camera failure mode and how to de-risk it. Mark it `VERIFIED` with the date.
3. **Build the scene & direction sheet.** Walk the approved script and break it into numbered scenes (`video-direction.md`, Part 2). Each scene: shot type, what's on camera, what's on screen / b-roll, on-screen text, the VO line it maps to, and the retention note. Insert the demo block where its loop pays off.
4. **Title + thumbnail.** 3 title options (strip test), 1–2 thumbnail concepts. No tool-tour cliché, a point of view, not a screenshot tour.
5. **CTA + checklist.** CTA points to the user's lead magnet, the flywheel's capture step (if they don't have one yet, say so and propose the one this video's demo implies). Then the production checklist (`video-direction.md`, Part 4).

> Each spawned agent returns text only, never writes to disk. If an agent returns boilerplate or goes off-task, re-run it once; if it fails again, run that voice inline rather than stalling.

## Output

Create the episode folder `~/.champion/work/videos/NN-slug/`. Write the deliverable to `~/.champion/work/videos/NN-slug/script.md` with full frontmatter, in this order, and add a short folder `README.md` orienting it (title, status, what's in the folder, and that the CTA points to the shared lead magnet at `~/.champion/work/lead-magnet/`, if one exists):

1. **The angle block**: the outcome it teaches, the chosen hook, the CTA target (short, at the top).
2. **The scene & direction sheet**: numbered scenes with shots, the demo block (scouted + prototyped + verified code/prompts), on-screen text, and the production checklist. This is the part the user films from.
3. **The full voiceover script**: clean, in the user's voice, scrubbed, in spoken cadence. Readable straight off a teleprompter. The scene sheet's VO refs map into this.

Then add the index row to `~/.champion/work/videos/README.md` (link the folder) and summarize to screen: the chosen angle, Round 1 results, the showrunner's loop map in one line, the viewer retention read and the fix applied, the demo and whether it's verified, title options, thumbnail concept, and the CTA. Keep the screen summary tight; the file holds the detail.
