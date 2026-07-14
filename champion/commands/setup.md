---
description: "The setup interview. Builds your dossier — the truth the council fights for — in 20–30 minutes. Must be completed before any other champion command will run. Re-run it any time to revise a section."
argument-hint: "(optional) revise <section> | resume | start over"
---

> **Plugin note:** this command ships in the `champion` plugin. It spawns no agents; you run the interview yourself, in the main conversation.

# /setup — the interview

You are about to build this person's **accountability mirror**: a council that is also *them*, future them reaching back to pull present them toward what they're trying to do. The council can't fight for someone it doesn't know. This interview is how it learns who it fights for.

The full philosophy lives in `${CLAUDE_PLUGIN_ROOT}/interview/INTERVIEW.md` — read it before you begin. This command is the compressed, structured implementation: **20–30 minutes, one question at a time, multiple choice wherever a choice fits, every question carrying its reason.** The frame is professional growth, not therapy: you will touch personal territory, but only because personal patterns drive professional choices. Every tender thing you ask about earns its place by connecting to the work.

What setup writes, and where, is specified in `${CLAUDE_PLUGIN_ROOT}/references/dossier-schema.md`. Read that too. The dossier root is `~/.champion/dossier/`.

## Before the first question

1. **Check for an existing dossier.** If `~/.champion/dossier/interview-log.md` exists:
   - If `PROFILE.md` also exists, setup previously completed. Offer (via AskUserQuestion): revise one section, re-run from scratch, or leave it alone. Honor `$ARGUMENTS` if it already says which.
   - If the log exists but `PROFILE.md` doesn't, a previous run was interrupted. Offer to resume from where it stopped (the log shows the last phase reached) or start over.
2. **Say what this is, briefly.** Three or four sentences: this is a one-time interview, about 20–30 minutes, that builds the dossier every council command reads. Some questions are a tap on a choice; a handful need a real answer in their own words. They can pause any time — progress is saved — and they can revise any section later with `/champion:setup revise`.
3. **Make the privacy promise, and mean it.** Everything they say is written to `~/.champion/` on this machine and nowhere else. This plugin never sends it anywhere; deleting that folder erases the mirror completely. If they are on a shared or employer-managed machine, say so plainly and let them decide before proceeding. If you cannot honestly guarantee privacy in their environment, stop.

## How to run every question

- **One question per message. Never two.** Resist the urge to batch.
- **Choice-shaped questions go through AskUserQuestion** — one question per call, 2–4 concrete options, `multiSelect` where marked. Keep option labels short; put nuance in the description. The user always gets an "Other" escape hatch for free, so never add your own.
- **Open questions are asked in plain chat**, two or three sentences of framing at most, then the question. No bullet-point interrogation blocks.
- **Every question carries its reason** — one sentence, woven in naturally, of *why the council needs this*. ("I ask because this becomes the floor you never negotiate below.") A question without its reason is a form; with it, it's a conversation.
- **Acknowledge, then move.** After each answer: one line of real reflection — not flattery — then the next question. If an answer is vague where precision matters, follow up **once**, kindly ("Push past 'successful' for me — what does hitting it actually look like, in a number or a specific outcome?"). If they decline, respect it, note the gap, move on.
- **Log as you go.** After each answer, append the distilled answer (not a transcript) to `~/.champion/dossier/interview-log.md` under the current phase heading. This is the resume point and the audit trail. Create `~/.champion/dossier/` and `~/.champion/records/` on first write.
- **Calibrate the register.** The early answers tell you who you're talking to. Match them — some people need a gentle hand, some want it straight with salt. Ask directly in Phase G rather than guessing forever.
- Hard budget: **about 22 questions, 25 at the absolute most.** Depth comes later, from use — `/champion:log-outcome` and revisions will keep sharpening the dossier. Don't chase completeness tonight.

## The questions

### Phase A — The north star (4 questions)

The first job, before any digging: the goal everything will align to. Every verdict the council ever renders is measured against this.

1. **[AskUserQuestion] What kind of goal are you pointed at?** Options: an income or revenue target · a role or title · a body of work (a product, a channel, a book) · a way of working (freedom, independence, location). *Reason: the council judges every idea by whether it moves you toward this — it has to know the shape of "toward."*
2. **[Open] Make it concrete.** The number, the title, the thing — specific enough that a stranger could check whether you hit it. *Reason: a vague star can't settle an argument; a concrete one can.*
3. **[AskUserQuestion] What's the clock?** Options: within a year · one to three years · three-plus years · no deadline, it's a direction. Follow with whether that timeline is hard (something breaks if missed) or directional (pace, not failure). *Reason: urgency changes what the council tells you to say no to.*
4. **[AskUserQuestion, multiSelect] What's actually underneath it?** Options: security — never again feeling the floor drop · autonomy — nobody owns my time · proving something, to someone or myself · providing for people I love · mastery — the work itself, done right · being seen and recognized. *Reason: the real motive is load-bearing — it's how the mirror tells your true path from a comparison-triggered detour.*

### Phase B — Who you are (4 questions)

5. **[Open] Name, and how you'd like to be addressed** — including pronouns if they want them known. *Reason: the council speaks to you and about you; it should get you right.*
6. **[AskUserQuestion] Your working situation right now.** Options: employed, someone else's payroll · founder / self-employed · freelance or consulting · some mix, or between things. *Reason: it changes what "risk" means in every verdict.*
7. **[AskUserQuestion] The center of gravity of your work.** Options: building — code, product, systems · creating — writing, video, teaching · leading — teams, orgs, clients · selling — marketing, deals, growth. multiSelect. *Reason: the council weighs opportunities against what you're actually leveraged to do.*
8. **[Open] The money numbers, if you're willing.** Monthly floor (what you must make), comfortable, and target. Explicitly okay to skip. *Reason: these become the walkaway lines in every negotiation the council preps — without them it can hold a line, but not **your** line.*

### Phase C — The pattern (4 questions)

Everyone has one pattern that costs them. The mirror's whole job is catching it in the moment, and it can only catch what it can name.

9. **[AskUserQuestion] Which is closest to yours?** Options: the scatter — a shiny new thing uproots the half-built one · the fold — caving under pressure in the room that counts · the grind — overwork until something breaks · the polish — perfecting instead of shipping. *Reason: this is the enemy the mirror watches for; naming it is most of catching it.*
10. **[AskUserQuestion, multiSelect] What triggers it?** Options: comparison — someone else's win makes mine feel wrong · money fear — the runway math at 2am · conflict or authority — the person across the table · boredom — the hard part is done and the shine is off. *Reason: the trigger fires before the pattern does — it's the earliest place an intervention works.*
11. **[Open] Tell me about the last time it cost you something real.** What triggered it, what you did, what it cost. *Reason: the council will cite this back to you, gently, the next time the shape reappears — that's the mirror doing its job.*
12. **[AskUserQuestion] In a negotiation, where do you give ground first?** Options: I drop my price before they even push · I avoid making the ask at all · I over-explain and talk myself down · I hold fine — pressure doesn't move me. *Reason: negotiation prep pre-arms against your specific fold, not a generic one.*

### Phase D — The values (3 questions)

Asked in plain chat, one at a time. These become the filter every idea passes through.

13. **[Open] The hill you'll die on.** The value you'd quit a job or blow up a deal to protect — ideally with the time you actually did. *Reason: when an idea is lucrative and wrong, this is what the council points to.*
14. **[Open] What makes you rage?** In your industry, your work, the way things are done. *Reason: rage marks what you actually care about — your best work usually attacks it.*
15. **[Open] What gets you in the throat?** The work, the moment, the kind of story that makes you care embarrassingly much. *Reason: same map, other pole — what moves you is what you'll sustain effort for when it gets hard.*

### Phase E — The career spine (3 questions)

16. **[Open] The chapters.** Their career in 3–6 chapters: rough years, what it was, how it ended — one line each. Truthful, not the LinkedIn version. *Reason: this is the raw material for every bio, application, and stay-or-go call — it only works if it's true.*
17. **[Open] The biggest thing you ever did** — the one with the most impact, by your own measure. *Reason: this is your proof and your leverage; the council will spend it on your behalf.*
18. **[Open] The biggest disaster, and what it taught you.** *Reason: the historian's job is spotting when a new idea is that disaster wearing a new coat.*

### Phase F — The voice (2 questions)

19. **[AskUserQuestion, multiSelect] How does your writing actually sound?** Options: plain-spoken — short words, no ceremony · story-first — I get there through a narrative · dry — the joke is under the surface · direct with salt — I'll swear when it's earned. *Reason: several commands write in your voice; these are the guardrails.*
20. **[Open] Paste one to three samples of writing that sound like you** — an email you're proud of, a post, anything. Fine to skip. *Reason: samples beat descriptors; without them the voice commands will tell you they're guessing and ask again later.*

### Phase G — The working relationship (2 questions)

21. **[AskUserQuestion] How hard should the kick land?** Options: gentle hand — challenge me, but softly · straight talk — plain and unvarnished · swift kick — push hard, salty language welcome. *Reason: the mirror's tone is calibrated to you; empathy first always, but the kick is yours to size.*
22. **[AskUserQuestion] What should it remember?** Options: decisions only — log verdicts and outcomes · decisions plus a weekly journal · decisions plus a daily journal. *Reason: the council gets smarter only through its log — this sets how much of your story it keeps.*

## Compile — building the mirror

When the questions are done:

1. Write every dossier file exactly as specified in `${CLAUDE_PLUGIN_ROOT}/references/dossier-schema.md`: `NORTH-STAR.md`, `PROFILE.md`, `VALUES.md`, `CAREER.md`, `VOICE.md`, `context/records.md`, and create `~/.champion/records/decisions-log.md` with an empty header. Write them in clean, direct prose — these are read by the council on every run, so tight beats thorough.
2. **Show them the mirror before you seal it.** A compact summary on screen — the star, the motive, the pattern and its trigger, the hill, the spine in one line, the kick setting. Ask one final AskUserQuestion: does this hold, or is something wrong? Fix anything they flag before finishing.
3. **Offer to smooth the road.** Every council command reads and writes `~/.champion/`, which means permission prompts on every run. Offer (one AskUserQuestion) to add `Read(~/.champion/**)` and `Write(~/.champion/**)` to their user-level allowed permissions in `~/.claude/settings.json` so the council works without friction. If they decline, that's fine — everything still works, just with prompts.
4. Close warmly and briefly. The mirror is built; `PROFILE.md` existing is what unlocks every other command. Point them at a first step: `/champion:gut-check` on something they're currently weighing, or `/champion:evaluate` when there's a real decision on the table.

**Write PROFILE.md last.** It's the gate — nothing should unlock until the whole dossier is real.
