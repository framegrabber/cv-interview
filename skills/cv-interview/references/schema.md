# Evidence base schema

Five files in one directory (default `cv-evidence/`). YAML, UTF-8. Quote any string that
contains `: ` or starts with a special character.

**Conventions**

- **Translatable value**: a plain string (same in every CV language) or a map keyed by
  language code, e.g. `{en: "Vienna", de: "Wien"}`. Every printable text needs one entry
  per language in `profile.yaml` → `cv_languages`.
- **Dates**: `"YYYY-MM"` or `"YYYY"`, always quoted; `present` for ongoing.
- **ids**: lowercase kebab-case, unique within their file; referenced across files.
- **`review`**: list of languages whose wording the person has not approved yet. New or
  changed printable text gets every CV language; remove a language when they approve it; omit
  the key when empty.
- **Printable vs. internal**: bullets, role `scope`, positioning `headline`/`summary`,
  education, certifications and talks are printable. Everything in `stories.yaml`,
  `interview-log.md` and positioning `arc`, `signature_themes` and `red_flags` is internal.

## profile.yaml

```yaml
name: {first: Jane, last: Doe}
email: jane@example.com
phone: "+44 20 7946 0000"          # optional
location: {en: "London, remote", de: "London, remote"}
links: [linkedin.com/in/janedoe, github.com/janedoe]
cv_languages: [en]                  # languages every printable text must exist in

positioning:
  tracks: [vp, principal]           # ranked; vp | cto | principal
  arc: "Internal, one or two sentences connecting the roles"
  signature_themes:
    - "Internal: what every reader should remember"
  red_flags:
    - flag: "18-month stint at Acme"
      facts: "Acme acquired; team dissolved"
      framing: "Agreed wording or approach, or 'open'"
  pitches:                          # printable, one per track
    - track: vp
      headline: {en: "VP Engineering"}
      summary: {en: "One or two lines: seat, scope, signature outcome."}
      review: [en]

education:
  - id: msc-cs
    title: {en: "MSc Computer Science"}
    institution: "University of Example"
    start: "2008-10"
    end: "2010-09"
    details: [{en: "Thesis: …"}]    # optional

certifications:
  - id: cka
    name: "Certified Kubernetes Administrator"
    issuer: CNCF
    date: "2023-05"
    status: active                  # active | expired

languages:                          # spoken languages
  - {language: {en: English}, fluency: {en: Native}}
```

## roles.yaml

Every role, newest first, with every bullet that could appear on any CV. A renderer or
tailoring step selects from it.

```yaml
- id: acme-vp-eng
  title: "VP Engineering"
  company: "Acme Payments Ltd"
  location: {en: London}
  start: "2022-03"
  end: present
  kind: job                         # job | consulting | freelance | internship | other
  scope:                            # printable one-liner: reports to, leads what, how big
    en: "Reporting to the CEO; 6 teams, 45 engineers in London and Lisbon."
  review: [en]                      # covers scope
  bullets:
    - id: acme-platform-consolidation
      story: acme-platform          # → stories.yaml id; required unless the bullet is purely factual
      tracks: [vp, principal]
      skills: [platform-engineering, kubernetes]   # free tags; optional
      text:
        en: "Consolidated three deployment stacks into one platform, cutting lead time from 9 days to 1"
      review: [en]
```

## stories.yaml

The facts behind bullets. Never printable. One story may back several bullets and roles.

```yaml
- id: acme-platform
  roles: [acme-vp-eng]
  period: "2022–2023"
  tracks: [vp, principal]
  status: complete                  # imported | in-progress | complete
  source_text: "Led platform consolidation"   # original wording when imported; else omit
  situation: "Context and problem before the person acted."
  decision: "What the person personally decided, changed or stopped."
  scope: "Teams, people, systems, money involved."
  outcome: "Measured result: numbers, ranges or proxies; before → after."
  evidence: "Public links, documents, metrics sources."
  referee: "Name, relation (e.g. former CTO)."
  secret: ["£4.2M"]                 # literal strings that must never appear in printable text
  do_not_claim:
    - "The migration of the legacy monolith was not completed"
  unknowns: ["exact team size in 2022"]
  notes: "Anything else: credit split, caveats, how numbers were estimated."
```

`status`:

- `imported`: claim taken from a document, not yet confirmed in the interview.
- `in-progress`: confirmed but missing scope, decision, outcome, or evidence/referee.
- `complete`: has scope, the person's own decision, an outcome, and evidence or a referee.

## talks.yaml

Talks, workshops, panels, writing, podcasts, open source, community roles. Printable.

```yaml
- id: kubecon-2024
  kind: talk                        # talk | workshop | panel | article | podcast | open-source | community
  title: "Paved roads for 40 teams"
  venue: "KubeCon Europe, Paris"
  date: "2024-03"
  url: https://example.com/talk
  audience: "~300"                  # internal, optional
  tracks: [principal]
  review: [en]                      # when title or venue was translated or reworded
```

## interview-log.md

Human-readable state, see the template. Sections: phase line, sources imported, targeting,
storyline, coverage per role (facts not yet in a story, decisions about framing), open
follow-ups. Update after every recorded answer.
