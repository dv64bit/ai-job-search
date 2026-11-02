# Search Queries for Job Scraper

<!-- SETUP: Customize these queries based on your skills, target roles, and location -->

## Installed portal CLIs (primary for `/scrape`)

`/scrape` discovers every portal skill under `.agents/skills/*/SKILL.md` and runs its CLI first. Shipped country-agnostic CLIs include `linkedin-search` and `freehire-search`; Danish demos and any skill you add with `/add-portal` are included the same way. You do **not** need a matching `site:` line below for those CLIs to run.

The `site:` query templates in this file are the **WebSearch fallback** — for portals without a CLI, company career pages, or when a CLI fails.

**Language scope:** write every query category in every language listed in your CLAUDE.md Languages table (typically 1-2, sometimes more). A posting requiring a language you have *not* declared, as a job condition, is excluded before scoring; a posting requiring a *higher level* than you declared in a language you *do* work in is flagged for your own judgment, not excluded — see `04-job-evaluation.md`'s Language Gate, the single source of truth for this rule. Translate each category's keywords rather than machine-translating word-for-word (e.g. "Frontend Developer" -> "Desarrollador Frontend", not a literal word-for-word translation) if you work in more than one language.

## Search Sites

The built-in Danish portal tools (Jobindex, Jobbank, Jobdanmark, Jobnet) don't apply - candidate is India-based. Using instead:
- **linkedin.com/jobs** - primary source, filter by India / Hyderabad; also covered by `linkedin-search` CLI
- Google `site:` searches against LinkedIn and company career pages

## Query Categories

Queries are grouped by priority. Combine with location terms ("Hyderabad", "India", or a specific target city) as needed.

**Organize by function, not job title.** The same underlying work carries different titles across companies and markets (a "Data Scientist" role at one employer may be posted as "Insights Analyst" or "Data Consultant" at another). Name each priority category after the function it covers, and list several plausible job titles as query variants within that category rather than betting an entire priority tier on one exact title string.

### Priority 1: Product/UX Designer (primary direction)

These match the strongest and most desired career direction.

```
site:linkedin.com/jobs "Product Designer" Hyderabad
site:linkedin.com/jobs "UX Designer" India
site:linkedin.com/jobs "Product Designer" "design systems" India
```

### Priority 2: Enterprise/AI B2B SaaS UX (domain expertise)

These match domain expertise: enterprise, AI-driven, approval-heavy B2B workflows.

```
site:linkedin.com/jobs "Product Designer" "B2B SaaS" India
site:linkedin.com/jobs "UX Designer" "AI product" India
site:linkedin.com/jobs "Design Systems" Designer India
```

### Priority 3: Design + Code hybrid (adjacent roles)

Roles that value the React/Tailwind/shadcn coding edge alongside design.

```
site:linkedin.com/jobs "Product Designer" React India
site:linkedin.com/jobs "UX Engineer" India
```

### Priority 4: Broader Design / Consulting

Wider net.

```
site:linkedin.com/jobs "UI/UX Designer" Hyderabad
site:linkedin.com/jobs "Design Consultant" India
```

## Location Filter

Candidate is Hyderabad-based, open to relocation within India. Deal-breaker: roles outside UX/Product Design scope entirely (not a location constraint).
- Hyderabad and remote roles: PASS
- Other major Indian cities (relocation): PASS, note relocation required
- Outside India (no remote option): FLAG (discuss with user)

## Language Filter

Your working languages and levels are in CLAUDE.md's Languages table. When filtering scraped results, apply `04-job-evaluation.md`'s Language Gate: a posting requiring a language you haven't declared at all is excluded; a posting requiring a higher level than you declared in a language you do work in is not excluded, flag it clearly instead (see `job-scraper/SKILL.md`'s Step 3 "Quick Fit Assessment" for how the flag surfaces in `/scrape` output). Postings simply *written* in a language you don't work in, that don't require it on the job, are fine.

## Date Filter

Only include jobs posted within the last 14 days, or with an application deadline that has not yet passed. If a posting date cannot be determined, include it but flag as "date unknown".

## Adapting Queries

If the user specifies a focus area, select queries from the matching category and also generate 2-3 custom queries for that focus. For example:
- "/scrape [focus_area]" -> relevant category queries + custom focus-specific queries
