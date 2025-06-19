# Final Session on AI-Driven Software Engineering & Cursor Rules

## 🎯 Session Focus (00:01)
In this session, we explored how to go beyond basic prompting to designing our own cursor rules. We applied Bloom’s Taxonomy to shift toward higher-level skills like evaluating and creating.

---

## 🧠 Core Activities & Format (00:41)
- ✅ **Cursor rule sharing** – Teams showed the rules they developed and got feedback from peers and instructors.
- ✅ **Debate & Evaluation** – The group discussed and refined each other's rules to make them stronger.
- ✅ **Mini Project Demos** – Small but impactful projects were shared that applied cursor rules in action.
- 🎁 **Bonus Reveal** – Unlocked based on how thoughtful and complete the demos and rules were.

---

## 📜 Deep Dive: Highlights from the team’s cursor rules

### 1. Dependency Management  
📍 *Screenshot at 02:34 – 04:34*  
![Screenshot](screenshots/01.png)

- Pin exact versions to avoid breaking changes.
- Use **UV** and the **UV lock file** to ensure consistent environments across systems.

### 2. Code Style & Security Best Practices  
📍 *Screenshot at 06:05 – 07:07*  
![Screenshot](screenshots/02.png)

- Follow OOP principles and prioritize clean, accessible code.
- Avoid hardcoded secrets and global state mutation.
- Always include alt text for meaningful images.

### 3. Refining Rules with AI  
📍 *Screenshot at 09:07 – 15:13*  
![Screenshot](screenshots/03.png)

- Used ChatGPT to improve rule clarity and specificity.
- Refined prompts iteratively to match the coder's intent.

### 4. Modularity & Metrics  
📍 *Screenshot at 20:25 – 23:04*  
![Screenshot](screenshots/04.png)

- Keep rules modular and split across small files.
- Define measurable thresholds for complexity, test coverage, etc.

### 5. Architecture Principles  
📍 *Screenshot at 26:48*  
![Screenshot](screenshots/05.png)

- Promote clean, maintainable architecture using idiomatic code patterns.

---

## 🚀 Showcase: Loan Management System (27:37)  
![Screenshot](screenshots/06.png)

Snail shared a working loan system built using Cursor.

- **Reduced development from months to ~2.5 hours**
- Key features:
  - Credit scoring using FICO
  - Validation of input
  - Business rules defined via cursor prompts

---

## 🧩 Understanding MCP & AI Agent Integration  
📍 *Screenshot at 46:06*  
![Screenshot](screenshots/07.png)

- MCP (Model Context Protocol) helps connect tools like GitHub or API scanners to Cursor agents.
- Agents use MCP tools to observe, reason, and act more intelligently.

---

## 💡 Foundational Takeaways on Cursor Rule Philosophy  
📍 *Screenshot at 51:00*  
![Screenshot](screenshots/08.png)

- **Always > Manual > Ask** – be intentional about when rules apply.
- Good rules:
  - Are simple but thoughtful
  - Are built iteratively
  - Use numbers (e.g., no more than 2 levels nesting)
  - Live in small, clear files

---

## 🔐 Closing Thoughts: How Not to Fail at AI Projects (01:20:00+)

### 1. "Failure is Not an Option"  
📍 *Screenshot at 01:22:08*  
![Screenshot](screenshots/09.png)

- NASA’s “seven minutes of terror” was used as a metaphor: critical software must be dependable.

### 2. Survival Curve of AI Projects  
📍 *Screenshot at 01:23:44*  
![Screenshot](screenshots/10.png)

- Fewer than 5% of AI projects make it to production. Most fail due to lack of direction, design, or persistence.

### 3. Principles for Sustainable Success

- ❓ **Quo Vadis?** – Align everything with a meaningful business goal.  
- 🐢 **Festina Lente** – Go fast, but never skip quality.  
  📍 *Screenshot at 01:29:58*  
  ![Screenshot](screenshots/11.png)
- 📊 **Tyranny of Data** – Most AI work is cleaning, labeling, and preparing data.  
- 🧪 **No Free Lunch** – Don’t assume one model or design will always work. Test options.  
- 🧭 **Explore the Unknown** – Take a discovery mindset.  
- 🌍 **Collective Intelligence** – Diverse teams solve better than top-down decision-making.  
- 📈 **Measure What Matters** – Use clear metrics: code quality, latency, performance.

---
