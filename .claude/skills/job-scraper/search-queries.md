# Search Queries for Job Scraper

## Search Sites

Primary:
- **linkedin.com/jobs** - LinkedIn job listings filtered for New York, NY / New Jersey / remote or hybrid.
- **indeed.com** - broad U.S. software engineering listings.
- **builtin.com** - startup and tech-company listings.
- **wellfound.com** - startup roles.
- **company career pages** - banks, fintech companies, trading platforms, and enterprise software companies.

Secondary (company career pages via Google):
- Direct Google searches with `site:` filters for known target companies

## Query Categories

Queries are grouped by priority. Each query should be combined with your location terms (e.g. "Copenhagen", "Sjælland", "Hovedstaden") where the site supports it.

### Priority 1: Backend Software Engineer

These match your strongest and most desired career direction.

```
site:linkedin.com/jobs "Software Engineer" "Java" "Spring Boot" "New York"
site:linkedin.com/jobs "Backend Engineer" "Kafka" "New York"
site:linkedin.com/jobs "Java Developer" "Spring Boot" "New Jersey"
site:indeed.com "Backend Software Engineer" "Java" "Kafka" "New York"
```

### Priority 2: Fintech / Trading Systems

These match your domain expertise.

```
site:linkedin.com/jobs "Software Engineer" "trade processing" "New York"
site:linkedin.com/jobs "Software Engineer" "capital markets" "New York"
site:linkedin.com/jobs "Software Engineer" "FX" "Kafka" "New York"
site:indeed.com "fintech" "Java" "Spring Boot" "New York"
```

### Priority 3: Platform / Distributed Systems

Adjacent roles you could pivot into.

```
site:linkedin.com/jobs "Platform Engineer" "Kafka" "New York"
site:linkedin.com/jobs "Distributed Systems Engineer" "Java" "New York"
site:linkedin.com/jobs "Infrastructure Software Engineer" "Kubernetes" "New York"
site:indeed.com "Platform Engineer" "OpenShift" "New Jersey"
```

### Priority 4: Broader Technical / Consulting

Wider net for general technical roles.

```
site:linkedin.com/jobs "Full Stack Engineer" "Java" "React" "New York"
site:linkedin.com/jobs "Data Engineer" "Python" "Kafka" "New York"
site:linkedin.com/jobs "Technical Consultant" "Java" "financial services" "New York"
site:indeed.com "Software Engineer" "Docker" "CI/CD" "New Jersey"
```

## Location Filter

When evaluating results, verify the job location is within reasonable commute distance from your home. Define acceptable areas:
- New Jersey and New York City roles should be considered first.
- Ideal: remote, hybrid, or onsite roles within reasonable commute from New Jersey to New York, NY.
- Acceptable: New York City, Jersey City, Hoboken, Newark, and nearby North/Central New Jersey locations.
- Borderline: Connecticut / Philadelphia / farther New Jersey locations; ask Chuwei before applying.
- Too far: roles requiring relocation outside the New York/New Jersey area unless Chuwei explicitly confirms interest.

## Date Filter

Only include jobs posted within the last 14 days, or with an application deadline that has not yet passed. If a posting date cannot be determined, include it but flag as "date unknown".

## Adapting Queries

If the user specifies a focus area, select queries from the matching category and also generate 2-3 custom queries for that focus. For example:
- "/scrape [focus_area]" -> relevant category queries + custom focus-specific queries
