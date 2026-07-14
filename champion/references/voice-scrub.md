# Voice Scrub, the cleaning step

The de-AI pass. Every piece written in the user's voice runs through this before it reaches them. The goal is simple: nothing they send should read like a machine wrote it. If a sentence has the cadence of a LinkedIn post or a chatbot, it fails.

Pair this with `~/.champion/dossier/VOICE.md` (the positive target). This file is the list of what to remove; VOICE.md is what to aim for.

---

## Hard bans (these never appear in their writing)

**Punctuation and symbols**
- **Em-dashes (, )** and en-dashes used as punctuation. Replace with a comma, a period, parentheses, or restructure the sentence. This is the single most common tell.
- **Arrows** (→, ⇒, =>) and any symbol shorthand inside prose.
- **Emoji** in prose deliverables (resume, cover letter, newsletter, bio, talk).
- Excessive **bold** for mid-sentence emphasis, and Title Case Headers sprinkled for drama.

**Crutch phrases and openers**
- "Here's the thing", "Here's the kicker", "Here's why", "The thing is", "Look,", "Newsflash", "Spoiler".
- "Let's be honest", "Let's be real", "Make no mistake", "The truth is", "Truth is", "To be clear".
- "At the end of the day", "In today's world", "In a world where", "Needless to say", "Of course".

**The contrast tic (antithesis as a formula)**
- "It's not X. It's Y." / "This isn't just X, it's Y." / "Not X, but Y." / "Not only... but also."
- Any sentence whose whole job is to set up a tidy reversal. One real reversal in a piece can land. The formula repeated is a machine signing its name.

**Hype and filler vocabulary**
- Verbs: leverage, unlock, supercharge, elevate, empower, harness, delve, dive into, navigate (figurative), tap into.
- Adjectives: robust, seamless, powerful, game-changing, cutting-edge, world-class, next-level.
- Nouns: tapestry, testament, realm, landscape, ecosystem (as filler), journey (figurative), game-changer.

**Closers**
- "In conclusion", "Overall", "Ultimately,", "All in all". End on a real line, not a summary of the lines above.

**Hedging throat-clearing**
- "I think", "I believe", "arguably", "it's worth noting", "in my opinion". Cut unless the sentence genuinely needs the qualifier. (This one is double-important: the hedge is usually the writer softening the true thing so nobody is upset. Hold the opinion. Do not file the edge off.)

---

## The punchy-sentence problem (the rhythm tell)

This one is about cadence, not vocabulary, so it hides.

- No one-sentence paragraphs dropped in for drama.
- No two or three word fragments for emphasis. "Every time." "That's it." "Full stop." "Period." All out.
- No run of short declaratives fired in a row like a slide deck.

The target is the user's actual rubric in `~/.champion/dossier/VOICE.md`. Vary the length. Let a long sentence breathe and unspool, then land a shorter one with intent, not as a gimmick. Take your time and invite the reader in. When in doubt, read it aloud. If it sounds like a person talking, keep it. If it sounds like a feed, rewrite it.

---

## The positive target (from VOICE.md, so it stays in front of you)

Before scrubbing, pull the positive target from `~/.champion/dossier/VOICE.md`: the voice descriptors, the rhythm they aim for, the taste, what they can't stand. Keep it in front of you for the whole pass. The bans above only say what to remove; VOICE.md is what the writing moves *toward*, so the result is the user's voice, not a flattened neutral one. If VOICE.md is thin, say so and ask for more samples rather than guessing.

---

## How to run the scrub

1. **Draft** in voice (`~/.champion/dossier/VOICE.md`).
2. **Voice-check.** Read it whole. Does it sound like the user, or like "content"? Fix the places it drifts.
3. **Scrub.** Go line by line against the bans above. The em-dash sweep and the punchy-fragment sweep are the two that always catch something.
4. **Adversarial verify.** Hand it to a fresh read whose only job is to hunt remaining tells (ideally a separate pass or agent, so it is not the same mind that wrote it). Whatever it flags, fix, then run the verify again. Repeat until it comes back clean.
5. **Hand to the user in markdown.** Stop there. They edit and approve. Nothing gets rendered, published, or sent until they say go.

The rule under all of it: **the writing is the user's, and the user checks it.** The machine drafts and cleans. It does not get the last word.
