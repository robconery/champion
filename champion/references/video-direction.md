# Video Direction, the production spec

The canonical reference for `/video`. The showrunner builds against the structure model here; Round 3 builds the scene sheet and demo plan against the templates here. The script lives in the user's voice (`~/.champion/dossier/VOICE.md`); this file governs *shape, retention, and what gets handed to the camera.*

The target: a **15-minute** teach/build video, **20 if the subject is dense**. The reference aesthetic is **MKBHD**: clean, no fluff, high craft, the reasonable one in the room who has actually done the thing. Not a hype channel. The pace is calm and confident; the retention comes from structure, not from yelling.

---

## Part 1, The structure model (MKBHD-clean + retention spine)

A video is a chain of **open loops**. You open a question the brain wants closed, you pay it off, and the instant you pay it off you open the next one. A well-built 15-minute video runs **5–7 setup→tension→payoff loops** end to end. The viewer stays because every answer is replaced by a new question before they can reach for the back button.

### The spine (the order the viewer lives it)

1. **Cold open (0:00–0:20).** Drop straight into the most compelling moment, the result, the surprise, the "wait, what." No "hey everyone," no throat-clearing, no slow ramp. The hook does three jobs in ~20 seconds: **validate the click** (yes, you're in the right place), **raise the stakes** (why this matters right now), and **open loop #1** (tease the grand payoff without giving it away). MKBHD move: open on the answer to a harder question than the obvious one.
2. **Title hit (~0:20–0:25).** A short, clean beat, the title/standup/logo moment, 3–7 seconds. A breath, then go. Keep it tight; this is where slow channels lose people.
3. **The body, 5 to 7 loops.** Each section is **rehook → content → payoff**. Rehook = a one-line tease of what *this* section pays off, planted before you fully close the last one, so there's never a flat seam between topics. Teach the real thing inside the loop. The **demo is the centerpiece loop**: the biggest open loop in the video, usually opened early ("by the end I'll show you X working") and paid off in the back half.
4. **The payoff / "why it works."** The reframe that makes the whole thing land. The viewer feels smarter than when they clicked. This is the dopamine they came for.
5. **CTA (the flywheel capture step).** Point to the lead magnet, the exact thing demoed. Soft, not salesy. They download the outcome, not a promise (`${CLAUDE_PLUGIN_ROOT}/references/marketing-playbook.md`).
6. **Binge loop.** End on a real line that opens the door to the next video or the comment-bait question, not a summary. Never "in conclusion." The outro's job is the next click.

### The write order (do NOT write top to bottom)

Write the loops **payoffs first, then setups, then tension, then the hook last.** You can't write a hook that promises a payoff you haven't decided on. Decide what each loop pays off, build the setup that earns it, lace in the tension that holds it, then go back and write the cold open to promise the biggest payoff in the stack.

### The retention curve (where videos die, and the fix)

- **The 30-second cliff.** Most drop-off is in the first 30 seconds. If the cold open ramps slowly or explains before it intrigues, they're gone. Front-load the most interesting thing you have.
- **The mid-video sag (~40–60%).** The classic dead zone. This is where a loop closed and no new one opened, or a setup ran too long. Every section boundary needs a rehook. If a beat doesn't open or close a loop, cut it.
- **The demo dead-air.** Demos drag when they show *process* instead of *result*. Narrate to the payoff, cut the boring parts, never make the viewer watch something compile.
- **The pre-CTA drop.** People bail the moment they smell the ask. Earn the CTA by making the payoff land first, then keep it short.

---

## Part 2, The scene & direction sheet

This is the first deliverable. It is the thing the user walks through with a checkbox: shoot this, screen-record that, drop this on screen here. Every scene is a row. The full voiceover script comes *after* the sheet (Part 4 of the output), clean enough to read off a teleprompter.

### Scene row format

Each scene gets a numbered block:

```
### Scene N, <name>   [loop: open/close #X]   [~MM:SS running]

- SHOT: <talking-head | screen-record | b-roll | overlay/motion | hands-on-keyboard>
- ON CAMERA: <what the user does / where they are / energy of the beat>
- SCREEN / B-ROLL: <what's being shown, the demo step, the diagram, the cutaway>
- ON-SCREEN TEXT: <lower-third, callout, or keyword to pop up, if any>
- VO REF: <the first few words of the matching voiceover line, so the sheet maps to the script>
- NOTE: <retention or craft note, "this is the rehook, keep it under 4s", "cut to result, don't show the wait">
```

### Shot vocabulary (keep it to these)

- **talking-head**: the user to camera. The spine of trust. Use for hooks, reframes, opinions.
- **screen-record**: the demo, the code, the terminal. The proof.
- **b-roll**: cutaways that cover an edit or set a mood. Texture, never filler.
- **overlay/motion**: on-screen text, a diagram building, a callout arrow. Carries the concept beats.
- **hands-on-keyboard**: the tactile "I'm really doing this" shot. Sells the build.

### On-screen text rules

Short. A keyword or a number, not a sentence. It reinforces the spoken line, never duplicates it. Use it to mark loop opens ("by the end: X working") and to land the punch of a payoff. No em-dashes on screen either (`${CLAUDE_PLUGIN_ROOT}/references/voice-scrub.md`).

---

## Part 3, The demo: scout, then prototype

If a demo is involved, it is the centerpiece loop and it has to actually work before the user films. Do not hand them a demo you haven't run.

### Scout

- What's the single outcome the demo proves? One thing. The demo earns its screen time by paying off the video's biggest loop.
- What's the most *showable* version? Favor a result you can see land in seconds over a process that takes minutes. The 3ms instinct applies: smallest thing that proves the point (`${CLAUDE_PLUGIN_ROOT}/references/3ms-framework.md`).
- Is there a cleaner or more surprising demo than the obvious one? Propose 1–2 options with a recommendation.

### Prototype (in the sandbox)

- Actually build and run it. Confirm it works end to end before it goes in the sheet.
- Put the **real, tested code** in the sheet, runnable, not pseudo-code, with the exact commands and any setup.
- If prompts are involved, write the **exact prompts** out, copy-pasteable.
- Note what could go wrong on camera (the thing that needs a network, the step that's slow, the bit to pre-bake) and how to de-risk it.

### Demo block format (goes in the scene sheet)

```
## DEMO, <name>

WHAT IT PROVES: <the one outcome, tied to which loop it pays off>
SETUP: <what's installed/open before recording; pre-baked state>
STEPS (on camera):
  1. <action> → <what the viewer sees>
  2. ...
CODE / PROMPTS: <the real, tested artifact, fenced, runnable>
RECORDING NOTES: <cut points, what to speed up, what to never show, the failure mode to avoid>
VERIFIED: <yes, ran in sandbox on YYYY-MM-DD / or what's left to confirm>
```

---

## Part 4, The production checklist

Ends the sheet. The walk-through. The user ticks each box, tweaks what they want, and films.

```
## CHECKLIST

PRE-PRODUCTION
- [ ] Angle and hook locked (Round 1 verdict)
- [ ] Demo prototyped and verified in sandbox
- [ ] Script read aloud once, timed to ~15 min (20 if dense)
- [ ] Scene sheet skimmed; any shot the user wants to drop is dropped

SHOOT
- [ ] Talking-head scenes (list)
- [ ] Screen recordings (list, in demo order)
- [ ] B-roll / hands-on shots (list)
- [ ] Cold open shot first while fresh

POST
- [ ] Cold open cut to under 20s, lands the loop
- [ ] Every section boundary has a rehook (no flat seams)
- [ ] Demo cut to result; dead air removed
- [ ] On-screen text placed at loop-opens and payoffs
- [ ] CTA short, after the payoff lands

PUBLISH
- [ ] Title chosen (3 options in sheet, strip test passed)
- [ ] Thumbnail concept built (face + one idea, no tool-tour cliché)
- [ ] Description + shared lead-magnet link (~/.champion/work/lead-magnet/)
- [ ] Index row added to ~/.champion/work/videos/README.md (linking the episode folder)
```

---

## The non-negotiables

- The voice is the user's, always (`~/.champion/dossier/VOICE.md`, scrubbed via `${CLAUDE_PLUGIN_ROOT}/references/voice-scrub.md`). The structure here never overrides the voice.
- The build is the marketing. The demo and the lead magnet are the same thing (`${CLAUDE_PLUGIN_ROOT}/references/marketing-playbook.md`).
- Nothing renders, publishes, or sends until the user approves the markdown. The machine drafts, scouts, and prototypes. The user films and ships.
