# Optional export: JSON Resume

Export only when the person asks for renderer input. The evidence base remains the source of
truth; exports are generated and can be overwritten.

[JSON Resume](https://jsonresume.org/schema) is an open standard read by many renderers,
including Typst templates (for example `@preview/altacv` via `alta-from-json`) and the JSON
Resume theme ecosystem.

## Selection

- One file per track and language: `exports/resume.<track>.<lang>.json` inside the evidence
  directory.
- Use only text approved in that language (its `review` list does not contain the language).
  If the person explicitly wants a draft, include unapproved text, set `meta.version` to
  `"draft"` (a standard field, so strict validators accept it), and say so when handing it over.
- Bullets: those tagged with the track, ordered as in `roles.yaml`. Apply the recency rule
  from method.md (current role 4–6, previous 3–4, older roles compressed) and lead each role
  with the bullet that best serves the storyline. Show the selection to the person before
  writing.
- Never export anything from `stories.yaml`, positioning `arc`, `signature_themes` or
  `red_flags`.

## Field mapping

| JSON Resume | Evidence base |
|---|---|
| `basics.name` | `profile.name.first` + `profile.name.last` |
| `basics.label` | `positioning.pitches[track].headline` |
| `basics.summary` | `positioning.pitches[track].summary` |
| `basics.email`, `basics.phone` | `profile.email`, `profile.phone` |
| `basics.location.city` / `.region` / `.countryCode` | split `profile.location`; keep the free text in `city` if it does not split cleanly |
| `basics.profiles[]` | `profile.links`: `{network, username, url}` (network from the host, e.g. LinkedIn, GitHub) |
| `work[].name` / `.position` / `.location` | role `company` / `title` / `location` |
| `work[].startDate` / `.endDate` | role `start` / `end`; omit `endDate` when `present` |
| `work[].summary` | role `scope` |
| `work[].highlights[]` | selected bullet `text` |
| `education[]` | `{institution, studyType: title, startDate, endDate}`; `details` → `courses` only if they are courses, else drop |
| `certificates[]` | active certifications: `{name, issuer, date}` |
| `languages[]` | `{language, fluency}` |
| `publications[]` | talks entries with `kind: article`: `{name: title, publisher: venue, releaseDate: date, url}` |
| `projects[]` | other talks entries: `{name: title, entity: venue, type: kind, startDate: date, url}` |

Translatable values resolve to the export language. Dates stay `YYYY-MM` / `YYYY`.

## Before handing over

- Valid JSON (parse it).
- No story `secret` string appears anywhere in the file (literal, case-insensitive search).
- No highlight contradicts its story's `do_not_claim` list.
- Tell the person which renderer-specific fields were dropped or approximated (talks have no
  native JSON Resume section).
