# Final Session on AI-Driven Software Engineering & Cursor Rules

##  Session Focus
In this session, we explored how to go beyond basic prompting to designing our own cursor rules. We applied Bloom’s Taxonomy to shift toward higher-level skills like evaluating and creating.

---

##  Deep Dive: Highlights from the team’s cursor rules

### 1. Dependency Management  
 
![Screenshot](screenshots/01.png)

- Pin exact versions to avoid breaking changes.
- Use **UV** and the **UV lock file** to ensure consistent environments across systems.

### 2. Code Style & Security Best Practices  
 
![Screenshot](screenshots/02.png)

- Follow OOP principles and prioritize clean, accessible code.
- Avoid hardcoded secrets and global state mutation.
- Always include alt text for meaningful images.

### 3. Refining Rules with AI  

![Screenshot](screenshots/03.png)

- Used ChatGPT to improve rule clarity and specificity.
- Refined prompts iteratively to match the coder's intent.

### 4. Modularity & Metrics  
  
![Screenshot](screenshots/04.png)

- Keep rules modular and split across small files.
- Define measurable thresholds for complexity, test coverage, etc.

### 5. Architecture Principles  

![Screenshot](screenshots/05.png)

- Promote clean, maintainable architecture using idiomatic code patterns.

---

##  Showcase: Loan Management System  
![Screenshot](screenshots/06.png)

Snail shared a working loan system built using Cursor.

- **Reduced development from months to ~2.5 hours**
- Key features:
  - Credit scoring using FICO
  - Validation of input
  - Business rules defined via cursor prompts

---

##  Understanding MCP & AI Agent Integration  
 

- MCP (Model Context Protocol) helps connect tools like GitHub or API scanners to Cursor agents.
- Agents use MCP tools to observe, reason, and act more intelligently.

---

##  Foundational Takeaways on Cursor Rule Philosophy  
  
![Screenshot](screenshots/07.png)

- **Always > Manual > Ask** – be intentional about when rules apply.
- Good rules:
  - Are simple but thoughtful
  - Are built iteratively
  - Use numbers (e.g., no more than 2 levels nesting)
  - Live in small, clear files

---

##  Closing Thoughts: How Not to Fail at AI Projects 

### 1. "Failure is Not an Option"  
 
![Screenshot](screenshots/08.png)

- NASA’s “seven minutes of terror” was used as a metaphor: critical software must be dependable.

### 2. Survival Curve of AI Projects  
 
![Screenshot](screenshots/9.png)

- Fewer than 5% of AI projects make it to production. Most fail due to lack of direction, design, or persistence.

### 3. Principles for Sustainable Success

- a) **Quo Vadis?** – Align everything with a meaningful business goal.  
- b) **Festina Lente** – Go fast, but never skip quality.  
    
  ![Screenshot](screenshots/10.png)
- c) **Tyranny of Data** – Most AI work is cleaning, labeling, and preparing data.
-  
  d) **No Free Lunch** – Don’t assume one model or design will always work. Test options.  
- e) **Explore the Unknown** – Take a discovery mindset.  
- f) **Collective Intelligence** – Diverse teams solve better than top-down decision-making.  
- g) **Measure What Matters** – Use clear metrics: code quality, latency, performance.

---
