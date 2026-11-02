# Search Queries for Job Scraper

<!-- SETUP: Customize these queries based on your skills, target roles, and location -->

## Search Sites

The built-in Danish portal tools (Jobindex, Jobbank, Jobdanmark, Jobnet) don't apply - candidate is India-based. Using instead:
- **linkedin.com/jobs** - primary source, filter by India / Hyderabad
- Google `site:` searches against LinkedIn and company career pages

## Query Categories

Queries are grouped by priority. Combine with location terms ("Hyderabad", "India", or a specific target city) as needed.

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

## Date Filter

Only include jobs posted within the last 14 days, or with an application deadline that has not yet passed. If a posting date cannot be determined, include it but flag as "date unknown".

## Adapting Queries

If the user specifies a focus area, select queries from the matching category and also generate 2-3 custom queries for that focus. For example:
- "/scrape [focus_area]" -> relevant category queries + custom focus-specific queries
