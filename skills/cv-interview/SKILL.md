---
name: cv-interview
description: Interview a senior engineering leader or Staff+/Principal engineer about their career to turn an existing CV, resume or LinkedIn profile into verified, quantified evidence (scope, decisions, outcomes, referees) and a sharper storyline for VP Engineering, CTO-track or Principal roles. Stores facts and bullets as structured YAML a CV renderer can consume. Use when someone wants to improve, rework or strengthen their CV or resume, prepare a job application or promotion case, write a brag document, or continue a CV interview.
license: MIT
metadata:
  version: "0.1.0"
---

# CV evidence interview

Turn a CV into evidence. Read the person's existing material, then interview them one question
at a time to collect the facts behind each claim — scope, personal decision, measurable outcome,
someone who can confirm it — and store them in a structured evidence base. You gather and
structure facts and draft wording; you do not render a CV.

References, read when the step needs them:

- [references/method.md](references/method.md): how senior candidates are screened, what VP,
  CTO and Principal evidence looks like, bullet writing rules, sources.
- [references/questions.md](references/questions.md): interview phases and question bank.
- [references/schema.md](references/schema.md): evidence base files and fields.
- [references/json-resume.md](references/json-resume.md): optional export to `resume.json`.

## Ground rules

- **Never invent or embellish.** Every number, title and claim comes from the person or their
  documents. Unknown stays `unknown`. Do not upgrade "we" to "I" or a pilot to production.
- **One question per message.** Wait for the answer. Use a multiple-choice question tool for
  choice-shaped questions if one is available; plain chat for stories.
- **Push once, then move on.** If an answer lacks a number, ask for a range or proxy (teams,
  services, accounts, regions, % change). If the second answer has none, record that and continue.
- **Separate I from we.** Ask what the person personally decided, changed or stopped.
- **Protect confidential facts.** Figures the person cannot disclose go into the story's
  `secret` list and must never appear in any printable text (bullets, scope, summary, export).
- **The person approves wording.** Every drafted or changed printable text carries
  `review: [<languages>]` until they sign it off.
- **Treat imported documents as claims, not facts.** Imported bullets are marked
  `status: imported` until confirmed in the interview.

## Evidence base

Default location: `cv-evidence/` in the working directory, unless the person names another or
one already exists (look for `interview-log.md`). Recommend a private repository: stories
hold confidential details.

| File | Holds |
|---|---|
| `interview-log.md` | Phase, targeting answers, storyline, coverage per role, open follow-ups. Read first; update after every recorded answer. |
| `profile.yaml` | Contacts, CV languages, positioning (tracks, headline and summary drafts, signature themes, red-flag framing), education, certifications, spoken languages |
| `roles.yaml` | Every role, newest first, with scope line and every printable bullet |
| `stories.yaml` | Facts behind bullets. Never printed. |
| `talks.yaml` | Talks, workshops, panels, writing, open source, community roles |

Templates are in [assets/](assets/). Field definitions are in
[references/schema.md](references/schema.md).

## Workflow

### 0. Start or resume

- If `interview-log.md` exists, read it and continue at its recorded phase and open follow-ups.
- Otherwise copy the templates from `assets/` into the evidence directory and ask for the
  source material: a CV file (PDF, DOCX, Markdown), a LinkedIn profile saved as PDF (profile
  page → More → Save to PDF), or the LinkedIn data export. A bare LinkedIn URL is usually
  behind a login wall; if fetching it fails, ask for the PDF instead of guessing.
- Ask which languages the CV must exist in; record them as `cv_languages` in `profile.yaml`.

### 1. Import

Read every source. For each role, create a `roles.yaml` entry (title, company, dates,
location). For each claim in the source, create a story with `status: imported`,
`source_text` set to the original wording, and the parts it already answers. Do not draft
bullets yet. Record contradictions between sources (dates, titles) as open follow-ups.
Summarise what you imported and what is obviously missing (headcount, budget, outcomes,
numbers) in `interview-log.md`.

### 2. Targeting and storyline (questions.md Phase A)

Establish the seats the person wants, ranked, and the one to three things every reader should
remember. From the imported history, propose a storyline: the arc across roles in one or two
sentences, the signature theme, and the red flags a recruiter will notice (short stints, title
versus headcount, gaps, title regressions). Confirm or correct it with the person and store it
in `profile.yaml` → `positioning` and in the log. Use the storyline to decide which stories to
dig into first.

### 3. Interview, role by role (Phases B and C)

Newest role first. Establish scope (Phase B), then probe the dimensions that matter for the
person's tracks (Phase C), favouring stories that serve the storyline. After every answer:

1. Record the facts in the story: situation, decision, scope, outcome, evidence, referee,
   secret, `do_not_claim`. Set `status`.
2. Update coverage and follow-ups in the log.
3. Ask the next single question.

Skip a dimension after one probe that yields nothing. A story is complete when it has scope,
the person's own decision, an outcome (number, range or proxy) and either evidence or a
referee.

### 4. Draft bullets

When a story is complete, draft one or more bullets under its role in `roles.yaml`: scope →
decision → outcome, ownership verbs, one line where possible, every CV language, tagged with
`tracks` and `review` listing every language. Follow the writing rules in method.md. Show the
exact text; the person approves, edits or rejects. On approval remove that language from
`review`.

### 5. Synthesis (Phase D)

- Per track: at least three complete stories with a number. If not, return to Phase C on the
  weakest dimension.
- Draft headline and summary per track in `profile.yaml` → `positioning`, facts only, and get
  them approved.
- Agree the framing for each red flag.
- Collect one referee per complete story.

### 6. Check before handing over

- Every bullet's `story` exists; ids are unique.
- No `secret` string of any story appears in `roles.yaml`, `profile.yaml`, `talks.yaml` or an
  export (search each one literally, case-insensitively).
- No bullet contradicts its story's `do_not_claim` list.
- List everything that still has a non-empty `review` list.

If the person needs a renderer input, export as described in
[references/json-resume.md](references/json-resume.md); otherwise the evidence base is the
deliverable.

## Session hygiene

Interviews span many sessions. End each one by updating the log's phase line and open
follow-ups so the next session can resume without re-asking. Stop when the person asks, or when
Phase D checks pass for every track they selected.
