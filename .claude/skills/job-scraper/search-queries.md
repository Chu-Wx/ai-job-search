# Search Queries for Job Scraper

## Search Sites

Primary (authentic US sources):
- **linkedin.com/jobs** — LinkedIn job listings filtered for Greater NYC / New Jersey first, with Seattle and California as secondary markets.
- **job-boards.greenhouse.io** and **boards.greenhouse.io** — Greenhouse-hosted job boards (many tech companies and startups).
- **jobs.lever.co** — Lever-hosted job boards.
- **jobs.ashbyhq.com** — Ashby-hosted job boards.
- **\*.myworkdayjobs.com** and **\*.wd5.myworkdaysite.com** — Workday career pages (large enterprises, banks).
- **Company career pages** — Direct career pages for banks, fintech companies, trading platforms, and enterprise software companies.

Secondary (aggregators — only for discovery; always follow back to authentic source):
- **indeed.com** — broad U.S. software engineering listings. Only present if the original employer posting URL can be confirmed.
- **builtin.com** — startup and tech-company listings. Follow through to the company ATS.
- **wellfound.com** — startup roles. Follow through to the company career page or ATS.

## Query Categories

Queries are grouped by priority. Combine with Chuwei's location terms (e.g. "New York", "New Jersey", "NYC", "Seattle", "California", "Bay Area", "San Francisco") where the site supports it.

### Priority 1: Backend Software Engineer

These match Chuwei's strongest and most desired career direction.

```
site:linkedin.com/jobs "Software Engineer" "Java" "Spring Boot" "New York"
site:linkedin.com/jobs "Backend Engineer" "Kafka" "New York"
site:linkedin.com/jobs "Java Developer" "Spring Boot" "New Jersey"
site:linkedin.com/jobs "Backend Engineer" "Java" "Seattle"
site:linkedin.com/jobs "Software Engineer" "Spring Boot" "California"
site:linkedin.com/jobs "Backend Engineer" "distributed systems" "New York"
site:linkedin.com/jobs "Software Engineer" "CI/CD" "Docker" "Kubernetes" "New York"
site:greenhouse.io/jobs "Backend Engineer" "Java"
site:greenhouse.io/jobs "Software Engineer" "Kafka"
site:jobs.lever.co "Backend Engineer" "Java" "Spring Boot"
site:jobs.ashbyhq.com "Backend Engineer" "New York"
site:myworkdayjobs.com "Software Engineer" "Java" "New York"
```

### Priority 2: Fintech / Trading Systems

These match Chuwei's domain expertise in financial technology.

```
site:linkedin.com/jobs "Software Engineer" "trade processing" "New York"
site:linkedin.com/jobs "Software Engineer" "capital markets" "New York"
site:linkedin.com/jobs "Software Engineer" "FX" "Kafka" "New York"
site:linkedin.com/jobs "fintech" "Java" "Seattle"
site:linkedin.com/jobs "fintech" "Java" "California"
site:linkedin.com/jobs "Software Engineer" "payment" "platform" "New York"
site:linkedin.com/jobs "Backend Engineer" "fintech" "Spring Boot" "New York"
site:greenhouse.io/jobs "fintech" "engineer" "Java"
site:jobs.lever.co "fintech" "backend" "New York"
```

### Priority 3: Platform / Distributed Systems

Adjacent roles Chuwei could pivot into.

```
site:linkedin.com/jobs "Platform Engineer" "Kafka" "New York"
site:linkedin.com/jobs "Distributed Systems Engineer" "Java" "New York"
site:linkedin.com/jobs "Infrastructure Software Engineer" "Kubernetes" "New York"
site:linkedin.com/jobs "Platform Engineer" "Kafka" "Seattle"
site:linkedin.com/jobs "Distributed Systems Engineer" "Java" "California"
site:linkedin.com/jobs "Site Reliability Engineer" "Java" "New York"
site:linkedin.com/jobs "Data Pipeline Engineer" "Kafka" "New York"
site:greenhouse.io/jobs "Platform Engineer" "distributed systems"
site:jobs.ashbyhq.com "Infrastructure Engineer" "backend"
```

### Priority 4: AI Infrastructure / Data Pipelines

Emerging roles at the intersection of infrastructure and AI.

```
site:linkedin.com/jobs "AI Infrastructure Engineer" "New York"
site:linkedin.com/jobs "Data Platform Engineer" "Kafka" "New York"
site:linkedin.com/jobs "ML Infrastructure" "Software Engineer" "New York"
site:linkedin.com/jobs "Data Engineer" "Kafka" "Java" "New York"
site:linkedin.com/jobs "Observability Engineer" "backend" "New York"
site:greenhouse.io/jobs "AI Infrastructure" "backend"
site:jobs.lever.co "Data Platform" "engineer" "Kafka"
site:jobs.ashbyhq.com "Data Engineer" "distributed systems" "New York"
```

### Priority 5: Broader Technical

Wider net for general backend/platform roles.

```
site:linkedin.com/jobs "Full Stack Engineer" "Java" "React" "New York"
site:linkedin.com/jobs "Data Engineer" "Python" "Kafka" "New York"
site:linkedin.com/jobs "Software Engineer" "Docker" "CI/CD" "New Jersey"
site:linkedin.com/jobs "Backend Engineer" "Observability" "New York"
site:linkedin.com/jobs "Cloud Engineer" "Kubernetes" "New York"
site:greenhouse.io/jobs "Software Engineer" "backend" "New York"
site:jobs.lever.co "Software Engineer" "distributed systems"
```

---

## Location Filter

When evaluating results, verify the job location is within Chuwei's acceptable areas:

- **Primary (no relocation needed):** Greater NYC and New Jersey. Includes New York City, Jersey City, Hoboken, Newark, and nearby North/Central New Jersey locations.
- **Relocation accepted:** Seattle and California (Bay Area, Los Angeles, San Diego, and other strong California software markets).
- **Borderline:** Connecticut, Philadelphia, and farther Northeast locations — ask Chuwei before applying.
- **Reject:** Any role requiring relocation outside Greater NYC/NJ, Seattle, or California unless Chuwei explicitly confirms interest.

## Compensation and Sponsorship Filter

### Compensation
- **Minimum compensation:** $165,000 USD.
- If salary/range is missing from the posting, skip the job unless the posting clearly states compensation will be discussed AND all other hard-filter requirements are excellent. Even then, flag as "salary unconfirmed."
- If the posting lists a range, the top of the range must be ≥ $165k (assuming Chuwei can negotiate toward the top).

### Sponsorship (HARD REQUIREMENT)
- **H-1B transfer sponsorship is REQUIRED.** Chuwei needs a new employer to sponsor an H-1B visa transfer.
- **If the posting does not explicitly mention visa sponsorship, H-1B transfer, immigration support, or include an application field confirming sponsorship handling, SKIP IT.**
- **Search for sponsorship signals in job descriptions:** "visa sponsorship", "H-1B", "immigration support", "work visa", "sponsorship available", "will sponsor", "employment visa", or application-form fields like "Will you now or in the future require sponsorship?"
- **Green card preference:** PERM / green card processing support is a strong positive signal. Note it when found, but do not skip jobs solely for lacking PERM support if H-1B transfer is confirmed.

### Work Mode
- All modes accepted: onsite, hybrid, remote — as long as the role is within the preferred locations.

---

## Date Filter

Only include jobs posted within the last 14 days, or with an application deadline that has not yet passed. If a posting date cannot be determined, include it but flag as "date unknown."

---

## Adapting Queries

If the user specifies a focus area, select queries from the matching category and also generate 2–3 custom queries for that focus. For example:
- "/scrape fintech" → Priority 2 queries + custom fintech-specific queries
- "/scrape platform" → Priority 3 queries + custom platform-specific queries
- "/scrape ai" → Priority 4 queries + custom AI infrastructure queries
- "/scrape broad" → run all categories
