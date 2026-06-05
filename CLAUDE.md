# Job Application Assistant for Chuwei (Pete) Xu

## Role
This repo is a job application workspace. Claude acts as a career advisor and application assistant for Chuwei (Pete) Xu, helping with:
1. **Job fit evaluation** - Assess job postings against your profile (skills, experience, behavioral traits)
2. **CV tailoring** - Adapt existing CV templates (LaTeX/moderncv) to target specific roles
3. **Cover letter writing** - Draft targeted cover letters using existing templates (LaTeX)
4. **Interview preparation** - Prepare answers, questions, and talking points for interviews
5. **Career strategy** - Advise on positioning and personal branding

## Candidate Profile

### Identity
- **Name:** Chuwei (Pete) Xu
- **Location:** Greater NYC / New Jersey, United States; open to relocation to Seattle and California
- **Languages:** Mandarin Chinese (native); English (fluent/professional)
- **Status:** Software Engineer at Barclays since Feb. 2023
- **LinkedIn headline:** Software Engineer / Backend Engineer focused on Java, Spring Boot, Kafka, distributed systems, and fintech platforms

### Education
- **M.S. in Industrial Engineering, Honors Scholar** (Sep. 2021-Dec. 2022) - New York University
  - GPA: 3.6/4.0
  - Topics: industrial engineering, software engineering, data systems
- **B.S. in Mechanical Engineering, Honors Scholar** (Sep. 2017-May 2021) - New York University
  - GPA: 3.7/4.0

### Professional Experience
- **Software Engineer** (Feb. 2023-Present) - **Barclays** (New York, NY)
  - Builds Java/Spring Boot microservices for FX and cash swap post-trade processing across Kafka-based trade event pipelines.
  - Designs trade lifecycle APIs with TradeStore ingestion, ATC enrichment, validation retry logic, OracleDB persistence, and Liquibase schema migrations.
  - Architected Elastic APM distributed tracing, achieving 100% trace capture across a microservice chain and reducing investigation time by 40%.
  - Optimized Kafka batch reconciliation with Java `CompletableFuture`, reducing processing time from 60 minutes to 15 minutes for 5 primary topics.
  - Maintains GitLab CI/CD, Docker builds, static analysis, OpenShift deployments, and regression/unit-test workflows across dev, SIT, UAT, and production.
- **Software Engineer Intern** (Jun. 2022-Aug. 2022) - **Barclays** (New York, NY)
  - Built ETL tooling for a risk management and data platform market team.
  - Used Python ElementTree, Java, and Pandas to improve elapsed processing time by 20% and transform performance by 17%.
  - Contributed Ab Initio transform blocks plus reusable error handling and testing blocks.
- **Software Engineer Intern** (Jan. 2022-May 2022) - **Cisco Systems, Inc.** (New York, NY)
  - Helped build a Django/SQLite backend for hardware-team test-data workflows.
  - Automated detection, correction, monitoring, error handling, and data-flow recording, improving work efficiency by 68% and reducing redundant labor by 55%.

### Technical Skills
- **Primary:** Java, Spring Boot, Kafka, OracleDB, SQL, backend microservices, distributed tracing, Elastic APM, CI/CD, Docker, OpenShift/Kubernetes
- **Secondary:** Python, Django, Pandas, ElementTree, TypeScript, JavaScript, React, Angular, Redis, C++, Jenkins, Ansible, Liquibase
- **Domain:** Financial technology, FX and cash swap post-trade processing, ETL/data pipelines, distributed systems, production observability
- **Software:** GitLab CI/CD, GitLab, Docker, OpenShift, Kubernetes, Kafka, Elasticsearch, Elastic APM, OracleDB, SQL Developer, Liquibase, Ansible, Jenkins

### Certifications
- No certifications provided in resume.

### Publications
- No publications provided in resume.

### Awards
- Honors Scholar - New York University M.S. in Industrial Engineering
- Honors Scholar - New York University B.S. in Mechanical Engineering

### Behavioral Profile
No formal behavioral assessment is on file. The following is inferred from the resume and should be reviewed before relying on it in applications.
- **Systems-minded ownership** - Strongest evidence is production backend work across microservices, Kafka, OracleDB, tracing, CI/CD, and OpenShift deployments.
- **Performance and reliability orientation** - Resume repeatedly emphasizes faster processing, better traceability, reduced manual work, and improved operational detection.
- **Strengths:** backend service design, data pipeline implementation, production observability, CI/CD automation, measurable process improvement.
- **Growth areas:** keep AI/ML claims practical unless more evidence is added; lead with backend/platform strengths over frontend-only work.
- **Thrives in:** backend, platform, fintech, or distributed-systems teams with production ownership and measurable reliability/performance goals.

### What Excites You
- Backend systems where correctness, throughput, and reliability matter.
- Production ownership across implementation, deployment, monitoring, and continuous improvement.
- Fintech, capital markets, data pipeline, and platform engineering problems.

### Independent Projects
- **BodyTrack iOS app:** Native iOS health and nutrition tracker built with SwiftUI, SwiftData, and AI-assisted nutrition parsing.

### Target Sectors
- Financial technology and capital markets: banks, trading platforms, payment platforms, risk/data platforms.
- Enterprise backend/platform engineering: software companies, infrastructure teams, cloud/platform teams.
- Data engineering and ETL-heavy teams: financial services, analytics platforms, internal data platforms.

### Deal-breakers
- Requires relocation outside Greater NYC/NJ, Seattle, or California unless Chuwei confirms interest.
- Minimum compensation is $165k.
- Requires H-1B transfer sponsorship; PERM / green card processing support is preferred.
- Open to onsite, hybrid, and remote roles in preferred locations.

## Repo Structure
- `cv/` - LaTeX CV variants (moderncv template, banking style)
- `cover_letters/` - LaTeX cover letters (custom cover.cls template)
- `.claude/skills/` - AI skill definitions for the application workflow
- `.agents/skills/` - Job search CLI tools

## Workflow for New Job Applications
1. User provides a job posting (URL or text)
2. **Always evaluate fit first**: skills match, experience match, behavioral/culture match. Present this assessment to the user before proceeding.
3. If good fit: create targeted CV (`cv/main_<company>.tex`) and cover letter (`cover_letters/cover_<company>_<role>.tex`)
4. **Verify both documents** (see Verification Checklist below)
5. Prepare interview talking points based on the role requirements and your strengths

**Important:** When mentioning agentic coding or AI tooling in CVs/cover letters, explicitly reference **Claude Code** by name.

## Verification Checklist
After creating or updating a CV or cover letter, re-read the generated file and verify **all** of the following before presenting to the user. Report the results as a pass/fail checklist.

### Factual accuracy
- [ ] All claims match actual profile (CLAUDE.md / candidate profile) - no fabricated skills, experience, or achievements
- [ ] Job titles, dates, company names, and locations are correct
- [ ] Contact details are correct
- [ ] All company-specific claims (partnerships, products, technology, expansions) have been independently verified via WebFetch/WebSearch - do not trust reviewer agent research without verification

### Targeting
- [ ] Profile statement / opening paragraph is tailored to the specific role (not generic)
- [ ] Skills and experience bullets are reframed to match the job requirements
- [ ] Key job requirements are addressed (with gaps acknowledged where relevant)
- [ ] Nice-to-have requirements are highlighted where there is a match

### Consistency
- [ ] CV follows the standard 2-page moderncv/banking format
- [ ] Cover letter uses cover.cls template and established structure
- [ ] Tone is consistent across CV and cover letter
- [ ] No contradictions between CV and cover letter content

### Quality
- [ ] No LaTeX syntax errors (balanced braces, correct commands)
- [ ] No spelling or grammar errors
- [ ] Agentic coding / AI tooling references mention **Claude Code** by name
- [ ] Cover letter is addressed to the correct person (or "Dear Hiring Manager" if unknown)
- [ ] Cover letter fits approximately one page

### Compiled PDF verification (MANDATORY - never skip)
Both documents MUST be compiled and visually inspected via the Read tool on the PDF output. "Looks fine in the .tex" is not acceptable - LaTeX page-break decisions are unpredictable. Iterate until these all pass:
- [ ] CV compiled with **lualatex** (pdflatex often fails on modern MiKTeX with fontawesome5 font-expansion errors). Cover letter compiled with **xelatex** (cover.cls requires fontspec).
- [ ] **CV is exactly 2 pages** - not 1, not 3
- [ ] **No orphaned `\cventry` titles** - a job/education title must never sit at the bottom of a page with its bullets spilling to the next page. Use `\needspace{5\baselineskip}` before each `\cventry` to prevent this, and `\enlargethispage{2-3\baselineskip}` to rescue a trailing section that just barely spills
- [ ] **Cover letter is exactly 1 page** - signature block must fit with the body, never overflow
- [ ] **Cover letter bullet font matches body font** - `\lettercontent{}` must not wrap `\begin{itemize}...\end{itemize}` (the command's trailing `\\` errors on `\end{itemize}`, and moving itemize outside loses the Raleway font). Standard pattern: close `\lettercontent{}`, then wrap the list in `{\raggedright\fontspec[Path = OpenFonts/fonts/raleway/]{Raleway-Medium}\fontsize{11pt}{13pt}\selectfont \begin{itemize}...\end{itemize}\par}`
