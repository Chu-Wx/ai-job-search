# Job Scraper

**name:** job-scraper
**description:** Scrapes US job sites for new positions matching Chuwei Xu's profile. Deduplicates across runs. Triggers on: job scrape, find jobs, search jobs, new jobs, job search, scrape jobs, /scrape
**allowed-tools:** Read, Write, Edit, Glob, Grep, WebFetch, WebSearch, Agent, AskUserQuestion

---

## How It Works

This skill searches authentic US job sources using targeted queries based on Chuwei Xu's profile, applies strict filter rules (location, compensation, sponsorship), deduplicates against previously seen jobs and the application tracker, and presents new matches with a quick fit assessment. Every returned job must include an authentic source URL from the employer career page or ATS page.

## Invocation

The user triggers this skill by saying things like:
- "Find new jobs"
- "Scrape for jobs"
- "Any new positions?"
- "/scrape"

Optional arguments:
- A focus area, e.g. "/scrape data science" or "/scrape fintech"
- "broad" to run all search categories, e.g. "/scrape broad"

---

## Authentic Source Strategy

Only search and fetch from these authentic US sources. Never use fake/scraped mirror listings as primary sources.

### Primary: Authentic Job Boards and ATS Pages

- **LinkedIn job pages/search URLs** — `linkedin.com/jobs`
- **Greenhouse-hosted job boards** — `job-boards.greenhouse.io`, `boards.greenhouse.io`
- **Lever-hosted job boards** — `jobs.lever.co`
- **Ashby-hosted job boards** — `jobs.ashbyhq.com`
- **Workday career pages** — `*.myworkdayjobs.com`, `*.wd5.myworkdaysite.com`

### Secondary: Company Career Pages

- Direct Google searches with `site:` filters for known target companies (banks, fintech companies, trading platforms, enterprise software companies)
- Use `WebFetch` on career pages found via WebSearch; prefer fetching the original ATS-hosted posting URL

### Aggregators (Use With Caution)

- **Indeed** and **Built In** are acceptable only as discovery tools — always follow the link back to the original employer career page or ATS posting. Only present jobs where the authentic source URL can be confirmed.
- **Wellfound (formerly AngelList)** — acceptable for startup roles if the posting links to the company's own ATS or career page.

### Disallowed Sources

- Do not use sites that scrape/repackage listings from other boards without linking to originals.
- Do not use aggregate sites that obscure the original employer posting URL.

---

## Strict Filter Rules for Chuwei Xu

Every job must pass ALL of these hard filters. If any filter cannot be evaluated due to missing information in the job description, skip the job and record the reason.

### 1. Location Filter

- **Primary (no relocation needed):** Greater NYC / New Jersey. Includes New York City, Jersey City, Hoboken, Newark, and nearby North/Central New Jersey locations.
- **Relocation accepted:** Seattle and California (Bay Area, Los Angeles, San Diego, and other strong California software markets).
- **Ask before applying:** Connecticut, Philadelphia, and farther Northeast locations.
- **Reject:** Any role requiring relocation outside Greater NYC/NJ, Seattle, or California unless Chuwei explicitly confirms interest.

### 2. Compensation Filter

- **Minimum compensation:** $165,000 USD.
- **If salary/range is missing:** Skip the job unless the original posting clearly states compensation will be discussed AND all other hard-filter requirements are excellent (strong match on skills, confirmed sponsorship, preferred location). Even then, flag as "salary unconfirmed."
- **If salary/range is below $165k:** Skip immediately.

### 3. Work Authorization Filter

- **H-1B transfer sponsorship is REQUIRED.** Chuwei needs a new employer to sponsor an H-1B visa transfer.
- **If the posting does not explicitly mention visa sponsorship, H-1B transfer, immigration support, or include an application field confirming sponsorship handling, skip it.**
- **Green card preference:** PERM / green card processing support is preferred. Note it as a positive signal when present, but do not skip jobs solely for lacking PERM support if H-1B transfer is confirmed.

### 4. Work Mode Filter

- **Accepted:** onsite, hybrid, remote — all are acceptable in preferred locations.

---

## Execution Steps

### Step 0: Load State

1. Read `job_scraper/seen_jobs.json` (create if missing — start with `{"seen": {}}`)
2. Read `job_search_tracker.csv` to extract already-applied companies+roles and previously skipped jobs
3. Read `search-queries.md` (this directory) for the search strategy

### Step 1: Search

Run **WebSearch** queries from `search-queries.md`. By default, run the top 3 priority categories. If the user said "broad", run all categories.

If the user specified a focus area (e.g. "fintech"), prioritize queries from that category.

For each search:
- Use `WebSearch` with site-specific queries (linkedin.com/jobs, greenhouse.io, lever.co, ashbyhq.com, myworkdayjobs.com, etc.)
- Target Chuwei's configured geographic areas (Greater NYC/NJ first, Seattle and California secondary)
- Look for postings from the last 14 days

### Step 2: Fetch & Parse

For each promising result from Step 1:
- Use `WebFetch` to retrieve the job posting page
- Extract: **job title**, **company**, **location**, **posting date** (or "recent"), **authentic source URL** (must be employer career page or ATS page), **salary range** (if listed), **visa sponsorship language** (exact text), **key requirements** (brief), **application deadline** (if listed)
- Skip if the URL or company+title combo already exists in `seen_jobs.json`
- Skip if the company+role already appears in `job_search_tracker.csv`

### Step 3: Apply Hard Filters

For each fetched job, evaluate against ALL strict filter rules in order:

1. **Location** — is it in Greater NYC/NJ, Seattle, or California?
2. **Compensation** — is salary ≥ $165k or at least listed/negotiable?
3. **Sponsorship** — does the posting explicitly mention visa sponsorship, H-1B transfer, or immigration support?
4. **Work mode** — is it onsite, hybrid, or remote?

**If a job fails any hard filter:** Record it in `seen_jobs.json` with `status: "skipped"` and a `skip_reason` field. Do NOT present it to the user.

**If a job is missing critical information needed to evaluate a filter:** Record it with `status: "skipped"` and `skip_reason: "missing <field>"`. Do NOT present it.

### Step 4: Quick Fit Assessment

For each job that passes all hard filters, do a rapid fit check (NOT the full evaluation from `04-job-evaluation.md` — just a quick signal):

- **High match**: Role directly involves Chuwei's core skills (Java, Spring Boot, Kafka, distributed systems, fintech) AND all hard filters pass cleanly
- **Medium match**: Role is adjacent to Chuwei's experience (platform engineering, data pipelines, backend with different stack) AND all hard filters pass
- **Low match**: Role requires significant skills Chuwei lacks, BUT all hard filters still pass

### Step 5: Deduplicate & Store

1. Add ALL fetched jobs (new, skipped, and passing) to `seen_jobs.json` with structure:
```json
{
  "seen": {
    "<url_or_company_title_key>": {
      "title": "...",
      "company": "...",
      "url": "...",
      "first_seen": "YYYY-MM-DD",
      "fit": "high/medium/low",
      "status": "new/skipped/evaluated",
      "skip_reason": "missing salary | missing sponsorship | wrong location | below 165k | ..."
    }
  }
}
```
2. Only present jobs with `status: "new"` that are NOT already in the seen list or tracker.

### Step 6: Present Results

Present new jobs in a table sorted by fit (high first):

```
## New Job Matches — YYYY-MM-DD

Found X new positions passing all filters (Y high, Z medium, W low match).
Skipped N jobs (reasons summarized below).

| # | Fit | Title | Company | Location | Salary | Sponsorship | Source |
|---|-----|-------|---------|----------|--------|-------------|--------|
| 1 | High | ... | ... | ... | ... | Confirmed | [Link](...) |

### Skipped Jobs Summary
| Company | Role | Reason |
|---------|------|--------|
| ... | ... | missing salary |
| ... | ... | no sponsorship language |

### High-Match Highlights
For each high-match job, add 2-3 bullet points:
- Why it matches Chuwei's profile
- Key requirements to check
- Any red flags (e.g., salary unconfirmed, relocation required)
```

After presenting, ask:
> "Want me to evaluate any of these in detail? Just give me the number(s)."

If the user picks a number, invoke the **job-application-assistant** skill workflow (fit evaluation first, then CV + cover letter if approved).

### Step 7: Update Tracker (Optional)

If the user decides to apply to any job, add a row to `job_search_tracker.csv`.

---

## Important Rules

1. **Never fabricate job postings.** Only present jobs found via actual WebSearch/WebFetch results.
2. **Every job must have an authentic source URL** from the employer career page or ATS page (Greenhouse, Lever, Ashby, Workday, or company career page). No scraped mirrors.
3. **Respect deduplication.** Always check seen_jobs.json AND job_search_tracker.csv before presenting.
4. **Apply all hard filters strictly.** Location, compensation, sponsorship, and work mode must all pass. Skip and record reason for any failure.
5. **Skip incomplete postings.** If a JD does not contain enough information to evaluate all hard filters, skip it and document which field(s) were missing.
6. **Only open positions.** Skip postings with expired deadlines or those marked as closed.
7. **Be efficient with WebFetch.** Don't fetch every search result — use titles and snippets to pre-filter before fetching.
8. **Parallel searches.** Use the Agent tool or parallel WebSearch calls to speed up the search phase.
9. **Track everything.** Both found (passing) and skipped jobs go into seen_jobs.json with distinct status values. Skipped jobs get a skip_reason.
