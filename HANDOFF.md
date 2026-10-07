# HANDOFF — cwanglab-v2 (read this first)

Written 2026-10-07 from the repository state, not from memory. Every claim below
was checked against `git log`, the working tree, or a live HTTP request on that date.
If `git log -1` no longer shows `9f8938e`, re-verify before trusting this file.

## 1. What this repo is

Hugo site for the Heterogeneous & Terminal Intelligence Lab (Dr Chengjia Wang,
Heriot-Watt). **Preview deployment** at `https://cwanglab.github.io/cwanglab-v2/`
(`hugo.toml` `preview = true` → `noindex` + footer notice). The **production** site
is the separate repo `cwanglab.github.io`, served at the domain root. Both live
(HTTP 200 on 2026-10-07). Decision on record (Group/CLAUDE.md v1.8): keep both;
v2 stays on the subpath.

Authoritative sources, in order: the PI in chat → `../CV/c_cv2.tex` and
`../CV/citations.bib` → Crossref/doi.org. Never the site itself, never memory.

## 2. State at handoff

- HEAD `9f8938e` (2026-09-03), `main` in sync with `origin/main`, working tree clean.
- Build: `hugo --gc` exits 0, **64 pages** (checked 2026-10-07). Alumni are a roster list, not pages.
- People: 34 profiles (1 PI, 12 doctoral incl. Amir Javadi Rad / Lukas Jurcaga /
  Luyando Mbozi, 2 collaborators, 20 taught/intern alumni as a roster list, no
  individual pages). Consent statement + removal contact present in
  `content/people/_index.md`. **0 photographs set**; `static/images/people/` empty.
- Tian Xia and Agisilaos Chartsias were REMOVED (9f8938e): PI confirmed they were
  co-advised at Edinburgh, not his PhD students. Do not re-add them as alumni.
- Figures: homepage and research pages lead with real paper figures (6fa78e8);
  four direction diagrams redrawn 1:1 (a1e91fb). `static/avatars/` deleted (82fd901).
- Publications: 2026 papers added (ISBI, Curr. Osteoporos. Rep., AISC, Ocean Eng.,
  ICASSP 2024) — each DOI Crossref-verified (f09dc16, 4f1b2a4).

## 3. Hard constraints the PI has stated (do not relitigate)

1. **Colour scheme and visual style do not change.** Site tokens only
   (`--claret #7a1732`, Georgia headings / Arial body). No new typefaces.
2. **Information organisation does not change** (section order, per-member fields).
3. **Nothing on the site may be stated that cannot be pointed at a line in the CV
   or a DOI.** This project previously shipped fabricated statistics; the standard
   is primary-source evidence for every number and every role.
4. Member photos: **photo + monogram fallback** (approved). Monograms stay until
   real photographs arrive — do not remove them, fill them.
5. See `DESIGN_AUDIT_2026-07.md` → "Not to be done" for refuted changes
   (e.g. the homepage participant figure, the 760px cap, the typeface).

## 4. Open work — all blocked on the PI unless marked otherwise

| # | Item | Blocked on |
|---|---|---|
| A | **Consent + photographs.** `CONSENT_EMAIL.md` is drafted; reply table is empty. Send, record replies, add `photo:` paths. | PI sends email |
| B | One group photograph on `/people/` (DESIGN_AUDIT P3 #24 — the one standard every surveyed lab meets and this site scores zero on) | PI supplies image |
| C | Sourced record block on `/about/` — patent, OPTIMAT Co-I, trial roles, **CV-verbatim only** (P3 #29) | PI approves wording |
| D | Concrete recruiting statement on `/opportunities/` if true (P3 #31) | PI confirms |
| E | Alumni destinations for the taught/intern roster; year range for Yuchen Mao (P3 #32) | consent replies |
| F | `hintelligence.online` on the PI card: DNS resolves, HTTPS timed out 2×30s on 2026-07-26 — recheck, then fix or drop | PI decision |
| G | `oa_url` for the three paywalled entries (P3 #30) | repository access |
| H | News backfill to ~quarterly (P3 #28) | partly PI |
| I | CV errors found while verifying the site (not site work): placeholder arXiv IDs `2411.12345`/`2301.12345` in CV_full.pdf (ScaleNet is 2411.08758); IEEE TMI title/year (P3 #33) | PI edits CV |

Nothing in the repo itself is known-broken as of HEAD.

## 5. How to work here

- Before any edit: `git pull`, then `hugo --gc --destination <scratch> --cleanDestinationDir`
  and record the page count; diff it after. Hugo silently drops future-dated content.
- Verify the **live** URL after a push, not just the local build (a one-commit lag
  once left the production site 404ing for ten days).
- Adding a person: copy `content/people/_template-member.md`; it is `draft: true`
  and underscore-prefixed so it never publishes. Every field is also editable in
  Pages CMS (`.pages.yml`, People collection).
- Session archives live under `~/.claude/projects/<cwd-encoded>/`; `claude --resume <id>`
  only finds a session when run from the directory it was *started* in.
- Related memory: `../CLAUDE.md` (Group-level; lessons 26–28 are about this site)
  and `~/.claude/CLAUDE.md` (workflow rules: verify first, surgical changes, report
  adjacent findings instead of fixing them).
