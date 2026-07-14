---
description: Run a job listing through the gauntlet, opportunity vs. the user's path, past, experience, and money. On GO, draft a tailored resume + cover letter in markdown, scrubbed clean and approved by the user before any PDF is built. On PASS, the honest reasoning.
argument-hint: <job listing URL, or pasted listing text>
---

> **Plugin note:** this command ships in the `champion` plugin, so every council agent it names is a plugin agent. When spawning any agent mentioned below, use the `champion:` prefix for the agent type (e.g. `champion:historian`, `champion:north-star`, `champion:viewer`).
>
> **Setup gate:** before doing anything else, check that `~/.champion/dossier/PROFILE.md` exists. If it does not, stop immediately and tell the user, politely, that the council cannot work without knowing who it fights for: run `/champion:setup` first (a 20–30 minute interview). Do not proceed in any form until setup is complete.

# apply, should the user go for this job?

The listing:

$ARGUMENTS

This is the decision engine pointed at a **job**. The output is one of two things and nothing in between: a **tailored application package** (resume + cover letter, drafted in markdown and run through the writing gauntlet, then rendered to PDF *only after the user approves the words*), or a **PASS with the real reason**. We do not write a resume for a job the user shouldn't take, and we never hand them a finished PDF they haven't approved in markdown first.

Two truths must stay separate the whole way through:
1. **Is the job any good?** (money, role, company, trajectory)
2. **Should *the user* do this, and can they?**: and this one matters more.

A job can be a high-stakes deviation for this user specifically: their stance on working for others, any active contract they've committed to protect, and any wound a past employer left are all in `~/.champion/dossier/PROFILE.md` and `~/.champion/dossier/CAREER.md`. Taking a job is not neutral, it's potentially the sabotage pattern firing, potentially a brave move, or potentially a contract breach. The gauntlet's job is to tell which.

## 0, Get the real listing

If `$ARGUMENTS` is a URL, **fetch it** (WebFetch). If it's pasted text, use it. Extract and pin down before debating: **company, role/title, seniority, comp/equity if stated, location/remote, key requirements, who they want.** If comp isn't stated, the researcher estimates the band.

## 1, Read the user's side

Load these so the council debates the real person, not a generic candidate:

- `~/.champion/dossier/PROFILE.md`: the money numbers, the contract (if any), the sabotage pattern, the fold, and how they feel about working for others.
- `~/.champion/dossier/CAREER.md`: the real timeline and **the truth under each line** (this is their leverage; most people undersell it, the application must NOT undersell it).
- `~/.champion/dossier/VALUES.md`: the non-negotiables and any lines already drawn in the sand.

## 2, Run the gauntlet (job-framed)

Conduct via the **`orchestrator`** agent against the canonical spec in `${CLAUDE_PLUGIN_ROOT}/gauntlets/README.md`. The user's **`champion`** is present throughout as their advocate. Frame the conversion: **customer = the hiring manager AND the user-as-candidate.** Keep the on-screen transcript tight; reasoning goes to the log.

**Seed (parallel):**
- **`researcher`** → the company (funding, runway, layoffs, news, Glassdoor/sentiment), the role, and the **salary band**. Is there a liquidation event in play?
- **`historian`** → the user's pattern with jobs and this kind of move. Past returns to employment and how they ended; exits and what drove them; whether this is a brave values-walk or the sabotage pattern firing (e.g. a panicked uproot). Reads the decisions log at `~/.champion/records/decisions-log.md` (location per `~/.champion/dossier/context/records.md`) + `~/.champion/dossier/CAREER.md`.

**Round 1, Diverge.** `expansionist` + `opportunist`: the biggest version of this opportunity, the career thesis, where the money and the trajectory go.

**Round 2, Stress.** `prosecutor`, `protectionist`, `operator`, `north-star`, `opportunist`, `customer`, given the briefs + R1 synthesis. The job-specific pressure points to force:
- **`operator`**: does this starve the user's current work / break the contract recorded in `PROFILE.md` (if any)? What do they stop doing if they take it?
- **`north-star`**: does this serve the path in `~/.champion/dossier/NORTH-STAR.md` or is it a salaried detour that *looks* safe? Non-negotiables intact, or a line from `VALUES.md` about to be crossed again?
- **`opportunist`**: real comp vs. the money numbers in `PROFILE.md`, equity/liquidation, is the money actually better than the path they're already on?
- **`customer`** (hiring-manager hat), would they actually hire this candidate, as `CAREER.md` presents them, for this, and at their number? Top objection a hiring manager raises.
- **`prosecutor`**: the case that this is the sabotage pattern or the fold talking (per `PROFILE.md`), or fear dressed as opportunity.

**Round 3, Converge.** Synthesize what survived. **`customer`** returns the 1–5 verdict. Preserve the strongest dissent verbatim.

> Spawn each voice read-only (text only, no file writes). Validate each returned its contract; re-run once if not, then run inline. Parallel within a round, synthesize between.

## 3, The gate

The verdict decides what gets produced:

- **5 / 4 → GO.** Worth it (4 = once named conditions hold). **Produce the application package** (§4).
- **3 → PARK.** Real ambiguity. **No package.** State the one piece of information that flips it to GO or kills it.
- **2 / 1 → PASS.** **No package.** Give the honest reason, and if it's the user's named pattern (the fold, the sabotage pattern, a contract breach) dressed as opportunity, **name that plainly.** This is the champion's job, not a courtesy.

## 4, On GO: draft the package in markdown (writing first, PDFs last)

The package is **writing before it is design**, and all writing goes through the writing gauntlet (`${CLAUDE_PLUGIN_ROOT}/commands/write.md` + `${CLAUDE_PLUGIN_ROOT}/references/voice-scrub.md`). Markdown gets written, cleaned, and approved by the user *before* anything is rendered. We do not hand them a PDF to react to. We hand them words to own.

Create `~/.champion/work/applications/<company-slug>/` (create the folders on demand) and produce, in this order:

**a) Resume content → `resume.md`.** Pull from `~/.champion/dossier/CAREER.md` and **map the user's real experience to this listing's requirements**: lead with the lines that hit their needs, surface the undersold truth (don't let them undersell, and treat dossier silence as "unknown, confirm" not as absence). Write it as clean markdown.

**b) Cover letter → `cover-letter.md`.** A real opinion, stated and earned, tailored to *this* company and role using the researcher's findings. Where you held an opinion the user might want to soften, hold it, and tell them not to hedge it.

**c) Run both through the scrub.** Voice-check against `~/.champion/dossier/VOICE.md`, then strip every AI tell per `${CLAUDE_PLUGIN_ROOT}/references/voice-scrub.md` (em-dash sweep and punchy-fragment sweep first), then an **adversarial verify** pass whose only job is to find remaining tells. Repeat until clean.

**d) Hand the markdown to the user and STOP.** They edit and approve. Their version is the source of truth; if they rewrite a line, keep their words. Do not proceed to design until they say go.

## 4b, On approval: render the PDFs (the final step)

Only after the user approves the markdown:

- Design through the **`high-end-visual-design`** skill (load it), adapted for **print**: **Editorial Luxury** or **Soft Structuralism** (light background), premium fonts, generous whitespace, none of the banned defaults. Letter/A4, real page-break control, one or two pages max.
- Write `resume.html` and `cover-letter.html` from the **approved** markdown (do not re-edit the words), then render: `"/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" --headless --print-to-pdf=<name>.pdf --no-pdf-header-footer <name>.html` (fall back to `wkhtmltopdf` or Playwright if Chrome is absent; say which you used). Send the PDFs.

## 5, Log it (always, GO, PARK, or PASS)

Append the full verdict to the decisions log at `~/.champion/records/decisions-log.md` in the Gauntlet entry format (newest at the top; the log's location is configurable via `~/.champion/dossier/context/records.md`, follow whatever it says). The `historian` reads it next time; the log only compounds if it's written.

## Output (tight, verdict first)

```
VERDICT: <1–5> → <GO / PARK / PASS>
WHY: <2–4 load-bearing bullets, opportunity vs. path/contract/money>
DISSENT: <strongest minority view, one line>
```
- On **GO**: hand over `resume.md` + `cover-letter.md` (scrubbed clean) and the one-line angle they lead with. Then wait for the user's edits and approval. **Build and send the PDFs only after they approve** (§4b).
- On **PARK**: the single fact that would move it.
- On **PASS**: the real reason, and, if it's the fold or the sabotage pattern, the named line ("this is the old wound talking, not an opportunity").
