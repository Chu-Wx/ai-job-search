# Interview Preparation Guide

<!-- SETUP: STAR examples are personalized by running /setup based on your actual experience -->

## STAR Format

Structure answers as: **Situation** (context), **Task** (your responsibility), **Action** (what you did), **Result** (outcome).

Keep answers to 1-2 minutes. Be specific. End with what you learned or would do differently.

## Ready-Made STAR Examples

### 1. Kafka batch reconciliation optimization (performance optimization)
**S:** Barclays' end-of-day batch reconciliation depended on sequential Kafka topic processing across primary topics.
**T:** Improve batch processing throughput without sacrificing correctness or thread safety.
**A:** Re-architected sequential Kafka processing into parallel execution using Java `CompletableFuture`; maintained thread safety while processing millions of trade events concurrently.
**R:** Reduced critical path processing time from 60 minutes to 15 minutes for 5 primary topics.
**Use for:** "Tell me about a performance optimization", "Describe a time you improved a production process", "How do you approach concurrency?"

### 2. Elastic APM distributed tracing rollout (observability and production ownership)
**S:** A post-trade microservice chain had cross-service trace-continuity gaps that made production investigation slower.
**T:** Improve service traceability and reduce investigation time across the chain.
**A:** Architected a distributed tracing solution using Elastic APM, coordinated trace context propagation across services, and collaborated with the observability team on infrastructure and alerting support.
**R:** Achieved 100% trace capture across the microservice chain and reduced cross-service investigation time by 40%.
**Use for:** "Tell me about debugging a distributed system", "How do you improve production reliability?", "Describe cross-team collaboration."

### 3. Barclays ETL caching and transform improvement (data pipeline engineering)
**S:** The risk management and data platform team had an ETL processing tool with avoidable repeated parsing and transformation overhead.
**T:** Improve processing efficiency and data transform performance during an internship project.
**A:** Implemented in-memory caching of parsed source data; used Python `ElementTree`, Java, and Anaconda Pandas to improve XML extraction and transformation flow.
**R:** Improved elapsed processing time by 20% and improved data transform performance by 17%.
**Use for:** "Tell me about an internship project", "How do you improve data pipeline performance?", "Describe a time you learned a stack quickly."

### 4. Cisco Django automation project (automation and backend development)
**S:** A hardware team had a manual test-data detection and correction process that created redundant labor.
**T:** Automate parts of the workflow and improve backend data recording and monitoring.
**A:** Helped construct a Django backend using SQLite; applied watchdog and supervisor modules for automatic background monitoring, error handling, and data-flow recording.
**R:** Increased work efficiency by 68% and reduced redundant labor by 55%.
**Use for:** "Tell me about automating a manual process", "Describe backend work outside your current domain", "How do you handle error monitoring?"

## Common Tough Questions

### "Why are you looking for a new role?"
> I have built strong backend and production-system experience at Barclays, especially around microservices, Kafka processing, CI/CD, and observability. I am looking for a role where I can keep growing technically, take on deeper ownership of distributed systems, and work on products where reliability and performance have visible impact.

### "You don't have [specific skill/experience]."
> I would be transparent about the gap, then connect it to adjacent experience. For example, if the gap is a specific cloud service, I would point to my Docker/OpenShift, CI/CD, Kafka, and production deployment experience, then explain how I would ramp up quickly through documentation, small scoped changes, and pairing with teammates.

### "Where do you see yourself in 5 years?"
> I want to grow into a senior backend/platform engineer who can own service design, reliability, observability, and delivery for important production systems. I am especially interested in systems where correctness, throughput, and operational quality matter.

### "What's your biggest weakness?"
> Need Chuwei's input for an authentic answer. Avoid inventing a weakness. A possible direction, if true, is balancing depth with communication: "I can go deep into implementation details, so I make a deliberate effort to summarize tradeoffs clearly for stakeholders before going too far into the technical weeds."

### "Why this company specifically?"
> Customize per company. Must reference: specific projects, company values, market position, or team structure. Never give a generic answer.

## Questions You Should Ask Interviewers

### About the Role
- "What does a typical week look like in this role?"
- "What would success look like in the first 6 months?"
- "What's the biggest challenge the team is facing right now?"

### About the Team
- "How big is the team, and how do you divide work?"
- "What does the development/project lifecycle look like, from idea to production?"
- "How do you onboard new team members?"

### About Tech & Growth
- "What's your current tech stack for [relevant area]?"
- "Is there room to grow into more architectural or strategic decisions?"
- "How does the team stay current with new tools and methods?"

### About Culture (use these to prevent disappointment)
- "How would you describe the team culture?"
- "What does professional development look like here?"
- "Is there flexibility for remote/hybrid work?"
- "What's the balance between development/new projects and maintenance work?"
- "How would you describe the leadership style in this team?"
- "What do people who thrive here have in common?"

## Phone/Video Interview Tips
- Have STAR examples written out (use this file)
- Keep a glass of water nearby
- Smile when speaking (it changes your tone)
- Ask for clarification if a question is vague
- It's OK to take 5 seconds to think before answering
- End with: "Is there anything else you'd like to know about my background?"

## After the Application (Best Practice)

### Follow-Up Etiquette
- **Don't call to "stand out"** or to learn more about the role post-submission - this risks a negative impression
- If the employer specified a timeline, respect it and wait
- If no timeline was given and significant time has passed (2+ weeks), a brief call to ask about status is acceptable
- If you have genuinely new, relevant information to share, a short follow-up is fine

### Thank-You Notes
- When you receive any update (interview invitation, rejection, or status update), send a brief thank-you message
- Express appreciation for their time and the process
- Keep it short (2-3 sentences)

## Roleplay Guidelines
When the user asks for interview practice:
1. Ask which role/company to simulate
2. Start with easy warm-up questions ("Tell me about yourself")
3. Progress to role-specific technical questions
4. Include 1-2 behavioral questions using the competencies from the job posting
5. End with a tough question or curveball
6. After each answer, give brief feedback: what worked, what to sharpen
7. Suggest which STAR example would work best for each question
