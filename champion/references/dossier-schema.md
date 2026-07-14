# The dossier schema — what setup writes, what the council reads

The dossier is one person's filled-in truth. It lives at `~/.champion/dossier/` on the user's machine, is created by `/champion:setup`, and is never shipped, synced, or read by anything but this plugin's council. Every agent reads from these files instead of carrying any identity of its own.

**The gate:** `~/.champion/dossier/PROFILE.md` existing is the signal that setup is complete. Every command checks it before doing anything.

## Files

| File | Contents | Written by |
|------|----------|-----------|
| `~/.champion/dossier/NORTH-STAR.md` | The one goal everything aligns to: the concrete target (a number, a role, a body of work, a freedom), the timeline and whether it's hard or directional, and the real motive underneath. The alignment lens the council applies to everything. Read first, always. | setup, Phase A |
| `~/.champion/dossier/PROFILE.md` | Who the user is: name, role, work situation, the money numbers (monthly need / comfort / target), the sabotage pattern (trigger → mechanism → result), the fold (what makes them cave in a negotiation), and the contract (what they've committed to protect until when). | setup, Phases B–C |
| `~/.champion/dossier/VALUES.md` | The hill they'll die on, what makes them rage, what makes them care enough to cry. The filter for judging any idea. | setup, Phase D |
| `~/.champion/dossier/CAREER.md` | The truthful career spine: the chapters, what worked, what blew up, where the real leverage is. Used to represent them in applications, negotiations, and the stay-or-go call. | setup, Phase E |
| `~/.champion/dossier/VOICE.md` | How they write and what they can't stand: voice descriptors, pasted writing samples, taste. Read before writing anything in their voice. If samples are thin, voice-led commands say so and ask for more rather than guessing. | setup, Phase F |
| `~/.champion/dossier/context/records.md` | Where the records live. Default: local files under `~/.champion/records/`. Users can point this at another system later; the council follows whatever this file says. | setup, Phase G |
| `~/.champion/dossier/interview-log.md` | The running record of what the interview surfaced, appended answer by answer as setup runs. Also the resume point if setup is interrupted. | setup, continuously |

## Records (written over time, read by the historian)

| Path | Contents |
|------|----------|
| `~/.champion/records/decisions-log.md` | Every gauntlet verdict: score, reasoning, preserved dissent, and, via `/champion:log-outcome`, what reality said afterward. |
| `~/.champion/records/journal/` | Optional journal entries, if the user opted in during setup. |

## Rules for agents

- Never assume a fact about the user that isn't in the dossier. If a file is missing or thin, say so and degrade gracefully; don't invent.
- The user's name and pronouns come from `PROFILE.md`.
- Personal details from the dossier are described in shape, not detail, in anything that could leave the machine.
- `/champion:setup` may be re-run at any time to revise a section; agents should treat the dossier as the current truth, not the original interview.
