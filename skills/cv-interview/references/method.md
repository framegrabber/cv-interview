# Method: evidence for VP+, CTO-track and Principal engineering roles

How senior engineering candidates are found and screened, what evidence each track needs,
and how to write it. Research baseline October 2026. `[INFERENCE]` marks synthesis that is
not directly sourced.

## 1. How senior candidates are found and screened

| Finding | Implication for the CV | Source |
|---|---|---|
| Most executive roles are never posted. Pipeline: internal → CEO network → internal exec recruiter → investors → retained search firm. | The CV is read **after** someone found the candidate through network, LinkedIn, talks or their current company. It must confirm, not discover. LinkedIn and CV must tell the same story. | Larson, *Getting a job as an engineering executive* |
| Executive recruiters filter on previously managed headcount. | State headcount and org shape explicitly, even if it feels crude. | Larson, *Executive LinkedIn profile* |
| Titles are ambiguous ("Head of X" can be a senior EM). | Every leadership role needs a one-line scope statement: reports to whom, leads what, how big. | Larson, *Executive LinkedIn profile* |
| Keyword stuffing is low-impact for executive roles. | Optimise for a human skimmer and backchannel references, not ATS. A parser-safe single-column layout still matters for portals. | Larson, *Executive LinkedIn profile* |
| Initial human screen ≈ 7.4 s; simple layout, clear headings, bold titles and bulleted accomplishments hold attention; long sentences hurt. | Lead each role with its strongest bullet; keep bullets to one line where possible. | Ladders eye-tracking study 2018 (via HR Dive) |
| Executive interviewers are often non-engineers (CEO, peers); decisions weigh fit, prestige, team size previously managed, communication. | Write outcomes in business language a CEO understands: cost, speed, risk, revenue enablement. | Larson, *Getting a job…* |
| Executive evaluation areas: executive skills (operating to a financial plan, hiring and performance processes), role-specific problems, functional expertise, historical performance via backchannel. | The CV should pre-answer all four. Every claim must survive a backchannel reference. | Larson, *Interviewing engineering executives* |
| Search briefs list org size (e.g. 7 EMs / 50 people), company scale, domain, cloud migration, build vs buy, M&A integration, cross-functional work with Product/Sales, nearshoring, KPIs, career stability. | These are the dimensions a retained recruiter scores against. The interview probes each. | Renovata, VP Engineering position profile |
| VPE is internally oriented (team, delivery, process, scaling); CTO is externally oriented (vision, architecture, board, customers). | Decide which orientation a given application targets; summary and first bullets differ. | Riviera Partners, *CTO vs. VP of Engineering* |
| VPE hiring probes: built and scaled a team (before/after), processes that made teams faster, product-vs-tech-health conflicts handled, an org approach that stopped working and what changed. | Each is a story to extract. | Riviera Partners, same |
| 2026 AI-transformation searches test: production not pilots, a number attached to the outcome, build-vs-buy calls including wrong ones, AI team hiring and retention, governance literacy (EU AI Act in Europe). | Personal AI tool use is table stakes. Show an org-level AI outcome with a metric. | Olofsson & Company, *Hiring a CTO or VPE with AI-transformation experience* |
| LLM screeners preferred LLM-written resumes (67–82 % self-preference in a controlled study). | Tension: AI-polished text may score better with AI screeners and worse with sceptical humans. Keep facts human-sourced and phrasing tight. `[INFERENCE]` | Xu et al., arXiv 2509.00462 |

## 2. Tracks

Stories and bullets are tagged with the tracks they serve.

| Track | Seats | Orientation |
|---|---|---|
| `vp` | VP / Head of Engineering, Head of Platform or Infrastructure | Internal: org, delivery, process, scaling |
| `cto` | CTO, CTO-track VP | External: vision, architecture, board, customers, business model |
| `principal` | Principal, Staff+, Distinguished engineer | Decision rights and cross-team adoption, no line management required |

### What VP-level evidence looks like

Ordered by how often the signals appear in briefs and recruiter guidance:

1. **Org scope**: total headcount, managers reporting in, teams, locations, contractors and vendors.
2. **Reporting line and seat**: reports to CTO/CEO/MD; member of which leadership team.
3. **Budget ownership**: opex/capex, cloud spend, vendor contracts; operated to a financial plan.
4. **Org building**: hires, teams built from zero, reorgs and why, attrition and retention.
5. **Delivery system**: processes introduced (planning, incident review, on-call, DORA-style metrics) and measured effect.
6. **Strategy**: multi-year direction set and the decisions it forced (build vs buy, sunset, migrate).
7. **Business outcome**: cost saved, time to market reduced, risk removed, revenue or launches enabled.
8. **Cross-functional and executive influence**: Product, Security, Finance, Legal, works council, board reporting.
9. **Transformation**: cloud migration, operating-model change, AI adoption across the org.
10. **Talent development**: managers grown, promotions, succession, hiring bar.

CTO-track adds external evidence: technical vision communicated to board or customers,
architecture bets with business consequences, due diligence, partnerships, public visibility.

### What Principal IC evidence looks like

Principal requisitions weight decision rights and cross-team adoption over stack lists. Will
Larson's archetypes give the vocabulary; pick one or two per person.

| Archetype | Owns | CV proof |
|---|---|---|
| Tech Lead | Approach and execution of one team or cluster | Delivered a multi-team project; technical vision; delegation |
| Architect | Direction and quality of a critical technical domain | Standards authored, platform decisions others build on, long-lived architecture |
| Solver | Knotty, high-risk problems leadership routes to them | Problem severity, what was stuck, how it got unstuck |
| Right Hand | Borrowed executive authority across a large org | Org-wide initiatives at the business, technology and people intersection |

Source: Larson, *Staff archetypes*.

Principal bullets (HireFlow, *Principal engineer resume bullets that show scope*):

- The first bullet names **org-wide scope** (teams, services, regions in blast radius), the
  **decision owned** (standard, platform API, review gate, incident authority) and an
  **outcome** (adoption count, deploy safety, latency, cost).
- Skills listed only where a bullet proves them.
- No title inflation; clarify scope in prose if the title undersells it.
- Under NDA, use defensible proxies: team count, service count, engineers on the platform, regions.
- Depth for Staff, org-wide adoption for Principal.

## 3. Storyline

A senior CV is read as an argument, not a list. `[INFERENCE]` from the sources above: the
reader should be able to say, after seven seconds, which seat the person is for, at what
scale, and what they are known for.

- **Arc**: one or two sentences connecting the roles ("from payments backend engineer to
  running the engineering org that took a fintech from one product to three"). Roles that do
  not serve the arc get compressed.
- **Signature theme**: the one to three things every reader should remember. Each needs at
  least two stories that demonstrate it in different roles.
- **Red flags**: short stints, title regressions, consulting or career gaps, a VP title with
  small headcount, a cancelled flagship project. Explain them with facts; do not hide them.
- **Consistency**: LinkedIn and CV tell the same story with the same numbers.

## 4. Writing rules

- **Formula**: "Accomplished [X] as measured by [Y] by doing [Z]" (Laszlo Bock). Senior
  variant: **scope → decision → outcome**.
- **Ownership verbs**: set, decided, built, cut, grew, consolidated, migrated, negotiated.
  Avoid duty verbs: *responsible for, ensuring, overseeing, supporting, involved in*.
- **Numbers**: absolute, before/after, or ranges ("€2–3 M annual cloud spend"). Ranges are
  acceptable when exact figures are confidential; every number must survive a reference check.
- **Credit**: when a team built it, say what the person decided or enabled ("won funding",
  "set the constraint", "led the team to…"). A referee will be asked.
- **Recency weighting**: current role 4–6 bullets, previous 3–4, roles older than ~8–10 years
  one line or dropped (Larson; Karriereakademie).
- **Summary**: one or two lines, facts only, per track: seat, scope, signature outcome.
- **Prestige markers**: talks, publications, open source, notable employers; summarise, link out.
- **Languages**: every printable text exists in every CV language with the same facts.
  Regional note for German-speaking markets: German guidance stresses KPI definition, budget
  responsibility, reporting to management, change management and strategy derivation
  (Karriereakademie).

## Sources

- Will Larson, *Getting a job as an engineering executive*: https://lethain.com/getting-engineering-executive-job/
- Will Larson, *Make an effective executive LinkedIn profile*: https://lethain.com/executive-linkedin-profile/
- Will Larson, *Interviewing engineering executives*: https://lethain.com/interviewing-eng-executives/
- Will Larson, *Staff archetypes*: https://staffeng.com/guides/staff-archetypes/
- Renovata, *Vice President of Engineering position profile* (2021): https://global-uploads.webflow.com/5eab1b1f62e1a9a680a32d26/613b9dafca584950a55410b5_d2a4afb1-b381-4e67-819f-0c51424eb1dd.pdf
- Riviera Partners, *CTO vs. VP of Engineering* (Jul 2026): https://www.rivierapartners.com/insights/cto-vs-vp-of-engineering-understanding-the-difference/
- Olofsson & Company, *Hiring a CTO or VP of Engineering with AI-transformation experience* (Aug 2026): https://olofsson.ai/insights/hiring-a-cto-or-vp-of-engineering-with-ai-transformation
- HireFlow, *Principal engineer resume bullets that show scope* (Sep 2026): https://hireflow.net/blog/principal-engineer-resume-bullets-that-show-scope-us
- HR Dive on the Ladders 2018 eye-tracking study: https://www.hrdive.com/news/eye-tracking-study-shows-recruiters-look-at-resumes-for-7-seconds/541582/
- Business Insider, Laszlo Bock's XYZ formula: https://www.businessinsider.com/google-exec-gives-key-to-perfect-resume-2014-9
- Karriereakademie, *Bereichsleiter Bewerbung*: https://www.karriereakademie.de/bereichsleiter-bewerbung
- Xu, Li, Jiang, *AI Self-preferencing in Algorithmic Hiring*: https://arxiv.org/abs/2509.00462
