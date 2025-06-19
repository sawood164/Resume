<center>

<img src="https://supportvectors.ai/logo-poster-transparent.png" width="300px" style="opacity:0.7">

</center>

---

<span style="font-size: x-small">
© <b>SupportVectors. All rights reserved.</b>
This document is the intellectual property of SupportVectors, and part of its training material. Only the participants in SupportVectors workshops are allowed to study the document for educational purposes currently, but is prohibited from copying or using it for any other purposes without written permission.
These documents are chapters and sections from Asif Qamar's textbook that he is writing on Data Science. So we request you to not circulate the material to others.
</span>

---

# Prompt Engineering

 A prompt is the initial input $x$ given to an LLM, which functions as a mathematical process where
  $$\hat{y} = f(x)$$
   
  It serves as a trigger that guides the LLM’s output based on the input.
  

![prompt.png](./prompt.png)


## LLM Mechanics: From Input to Output

When a user provides an initial input, $X_0$ (e.g., "write a 200 token short essay on California"), this entire sentence is converted into an embedding vectors.

The LLM's fundamental task is to produce the probability distribution for every word in its vocabulary given this input.

The word with the highest probability is then selected (and sampled) as the first output token, $Y_0$ (e.g., "goat"). If you feed the same $X_0$, we will get the same probabilities again.

So, to generate the next word, the input is augmented by concatenating the original input $X_0$ with the previously produced $Y_0$ (e.g., $X_0$ concatenated with "goat").

![Vocabulary.png](./Vocabulary.png)

This new, longer input is fed back into the LLM, forcing it to produce a different subsequent word $Y_1$.
This iterative process continues, generating one word (or token) at a time, until a special "stop" word is produced, indicating the completion of the response. This is why LLMs are often referred to as "next token prediction engines".

LLMs internally plan out entire responses (e.g., grasping a 200-token essay completely) before producing tokens sequentially. This indicates they operate with a conceptual understanding, similar to how humans might conceive an essay before writing it word-by-word.

A significant discovery, made at Anthropic, after bisecting the LLM, revealed that LLMs contain tens of thousands of *interpretable "concepts", each represented by **neural subcircuits*.

For instance, a subcircuit might represent the concept of "Golden Gate". When this subcircuit is deliberately amplified, the LLM will integrate the concept into its responses, even for unrelated queries, suggesting a deep internal representation of concepts that can influence outputs in a targeted way. Like if you ask - What is a bicycle, it will try to include "Golden Gate" somehow in the response.

## Building Effective Prompts for Agents

To build effective agents -especially for tasks that are not strictly logical (e.g., offering social advice), understanding LLM behaviour is crucial. 
From an agent design perspective, a prompt typically has two main components:

1. **System Prompt: This defines the agent’s personality, role, behavioral guidelines, and task boundaries. It serves as the foundational instruction that shapes how the LLM behaves—similar to assigning a role or expertise (e.g., "act as a therapist" or "speak like a historian").
2. **User Prompt: This is the specific input/question/query provided by the user. It initiates the task or conversation and is interpreted by the LLM in the context set by the system prompt.

#### A well-crafted system prompt should include:

1. **Role: Clearly define the agent’s area of expertise or identity (e.g., "You are an expert web researcher").
2. **(Detailed) Background: Provide specific context and information about the role. Provide relevant context or situational details about the role, that help the model understand its environment or purpose.
3. **Audience: Specify the intended recipients of the output (e.g., "Children aged 8 to 15 years"), which helps tailor language and complexity.
4. **Guardrails: Clear behavioral rules—both do’s and don’ts—to ensure safe, accurate, and ethical responses (e.g., "Do not fabricate information", "Only show age-appropriate/safe content").
5. **Tone: Define the desired communication style or emotional register (e.g., "positive", "humorous", "formal and scientifically precise").
6. **Preferences: Include any operational or stylistic preferences (e.g., "use bullet points when listing", "avoid jargon").
7. **Output Format: Specify how the response should be structured or constrained (e.g., "provide a summary followed by detailed sections", "response must be at least 3500 tokens").

#### System Prompt Example: "The Data Scientist"

1. *Role*: "You are an expert data scientist with a reputation for methodical and careful exploratory data analysis".
2. *Detailed Background*: "You do this by carefully studying the data, reasoning about it carefully, and step by step and performing each of the tasks in the order".
3. *Audience*: "your report is targeted towards scientists and engineers with professions from a STEM field".
4. *Guardrails*: "Do not use any external PL [plugins]. Be sure that everything you say is grounded in the facts of the data. Do not make things up simply because it is plausible sounding".
5. *Tone*: "formal scientific precise and meant for publication".
6. *Preferences*: Prioritize robust statistical methodologies and transparent reporting of analytical assumptions and limitations.
7. *Output Format*: "The response should be in depth and at least 3500 tokens".

*Meta-prompting* refers to the practice of writing prompts that *guide or generate other prompts*—essentially, prompting the LLM to become better at prompting itself or others.
e.g. **Prompt Refinement** - "Here’s a prompt: 'Write about climate change.' Improve it to be more specific and goal-oriented."

#### User Prompt Example:

In the pdf file at [https://supportvectors.io/mod/resource/view.php?id=2901](https://supportvectors.io/mod/resource/view.php?id=2901), please review the prompts in chapter "3.2-Old Faithful geyser", which contains the analysis on proper prompts for  dataset associated with the old faithful geyser, which includes its eruption time and the subsequent waiting time for the next eruption.


---

# Exploring AI Agents: The Art of Prompting and Effective Communication

## Why Engineers Struggle with Prompting

Engineers are often not ideal for writing system prompts due to challenges in natural language communication.

- *Technical Jargon*: Technical people tend to use very technical jargon, which makes comprehension difficult.
- *Poor Readability*: Engineering documentation and source code comments are often very poor in comprehensibility and readability, leading to misguidance.
- *Communication Gap*: While programming is a form of communication with machines using higher-level languages (like Java, C, Python), engineers often lack skills in natural language communication, which is equally, if not more, important.

## The Value of Prompt Engineering

The demand for skilled prompt engineers is high, with some roles, like at Anthropic, offering salaries up to $350,000. This high value stems from the difficulty and importance of effective communication with Large Language Models (LLMs).

## Theory of Mind and LLMs

- Human Communication: Humans use an implicit "theory of the mind" when communicating, inferring the other person's background, knowledge, and intentions for efficient exchange.
- LLMs and Theory of Mind: Surprisingly, LLMs have been found to develop a theory of the mind, enabling them to characterize users based on past conversations.
- Statelessness vs. Agentic Systems:
	- When making direct API calls to a barebone LLM model (e.g., via OpenAI’s or Anthropic’s API), the interaction is stateless and memoryless. The model has no built-in awareness of prior conversations, user identity, professional background, or preferred communication style—unless that context is explicitly provided within the prompt each time. 
	- *Agentic frameworks* (such as ChatGPT with memory enabled, LangChain agents, or AutoGPT), build a comprehensive application around the core model. These systems can manage *long-term memory, maintain **user-specific context, and develop an approximate **theory of mind* (e.g., remembering user preferences or intent), enabling more personalized and context-aware responses than raw API calls.

## Importance of Context in Prompting

Because bare LLMs lack inherent context or memory, the *system prompt* is crucial for setting the *entire context* of the conversation. This is akin to providing all necessary background information to a customer service agent before asking a question. Without proper context, communication with an LLM can be frustrating and lead to irrelevant responses.

## Effective Prompting Techniques

Effective prompting hinges on clear, transparent communication.

1. *CO-STAR Template*: A useful template for prompting that sets the goal, context, audience, and tone of the response.
	- *C – Context*: Provide the background or situation relevant to the task.
	- *O – Objective*: State the goal or purpose of the prompt or interaction.
	- *S – Style*: Define the tone, voice, or communication style to be used (e.g., formal, friendly, humorous).
	- *T – Task*: Specify the exact action the model should perform (e.g., summarize, explain, generate).
	- *A – Audience*: Identify who the response is intended for (e.g., kids, students, professionals).
	- *R – Response Format*: Indicate the desired output structure (e.g., paragraph, bullet points, table, JSON).
2. *Few-shot Prompting: Providing the LLM with **a few input-output examples* within the prompt to demonstrate the desired behavior or format. The model uses these examples to infer the pattern and generate appropriate responses for new inputs.
3. *Chain-of-Thought (CoT) Prompting*: 
	- *Definition: CoT prompting involves encouraging the LLM to break down its reasoning into **intermediate steps, rather than jumping directly to the answer. This helps improve **accuracy*, especially for tasks that involve logic, arithmetic, or multi-step reasoning.
	- *Effect on Traditional LLMs: CoT prompting is especially beneficial for **standard decoder-only LLMs* (like GPT-3, GPT-4, Claude, etc.), which are trained as *next-token predictors*. Therefore, these models inevitably become producers of plausible and likely answers rather than necessarily correct answers. This makes them susceptible to occasional hallucination. Explicitly prompting them to "think step by step" improves performance in many reasoning tasks.
	- *Advanced Reasoning Models: For some emerging **goal-directed models* (e.g., DeepSeek-V2, DeepSeek-R1, Gemini 1.5, or Claude Opus), CoT prompting may be *less necessary* or sometimes *counter-productive. Likewise, there is evidence that few shot learning does not quite work with reasoning models. These models often generate internally complex reasoning paths and then **summarize* them in simplified outputs. Over-constraining them with external reasoning formats may reduce their natural efficiency or lead to verbose and less optimal outputs.

## LLM Training and Alignment

The training process of traditional LLMs involves several stages (we will cover in more detail in a later week):
1. *Pre-training*: Feeding trillions of tokens (2–5T) from web-scraped text, books, and code. This builds general language understanding but also exposes the model to toxic content and misinformation, influencing behavior.
2. *Supervised Fine-tuning (SFT)*: Using curated, labeled data (e.g., Q&A or instruction–response pairs) to teach task-specific behavior and align the model with basic human expectations.
3. *Reinforcement Learning with Human Feedback (RLHF)*: Human evaluators rank model outputs to train a reward model. The LLM then learns to prioritize helpfulness, safety, and factuality.
	- **Cultural Nuances: Definitions of “correct” or “safe” vary by culture, so alignment may reflect biases based on who labels the data (e.g., views on sex education or historical events).

*Reasoning Model Training*: Reasoning-focused models are trained by giving tasks (e.g., math problems) and only rewarding correct final answers—no step-by-step supervision. These models learn to reason internally and may skip supervised fine-tuning or RLHF, focusing purely on problem-solving ability.

---
##  Three Pillars of Powerful AI Agents

1. *Prompt Quality*- This is fundamental for setting context and guiding the agent's behaviour.
2. *Tool Richness*- Agents need access to a rich ecosystem of tools to interact with the external world and perform complex tasks.
	- *Documentation*: The agent learns when and how to use a tool through its documentation. The MCP (Model Context Protocol) is a popular protocol for declaring and exposing tools.
	- *Examples*: Tools can include GitHub for code analysis, Jira for defect tracking, or web browsing capabilities.
3. *Fine-tuning*- This amplifies the agent's "IQ" and adapts it for specific tasks.
	- Types: Includes traditional supervised fine-tuning and reinforcement learning.
	- Importance: Fine-tuning, especially of multi-agent collaboration, is considered the backbone of effective agentic systems.
	- Agents can debug codebases, analyze, and learn using reinforcement feedback loops.
	- *Agentic reasoning* focuses on giving *goals, not **step-by-step instructions*.

##  *Agents*

![agents.png](./agents.png)
  

![agent_storm.png](./agent_storm.png)
  
#### *Types of agents*:

- *Research agents*
- *Shopping agents*
- *Code-generating agents* etc.

#### *Capabilities*:

- Browse the web, answer tough questions, write code, or SQL.
- Handle complex, multi-step problems.
- Use *memory* and *knowledge bases* to retain long-term context.
 
#### *Agents can*:

- *Break down tasks* into subtasks.
- *Spawn sub-agents* to parallelize work.
- Collaborate to find answers — like an intelligent team.

Specialized coding agents can be made for *Logistics, **HR, **Finance, **Research* etc. which can:
- Convert natural language into *SQL*.
- Perform *task decomposition*.
- Use *query generation* and *RAG* techniques.

*Retrieval Augmented Generation (RAG)*: This technique provides the agent with a knowledge base and memory, essential for performing tasks effectively by augmenting its generative capabilities with retrieved information.

---

# AI Agent Project Summary - Newsroom Simulation

## Project Overview

### Simulate a *newsroom* where AI agents act as:

- Researchers
- Prioritizers
- Editors
- Designers

Final deliverables:

- A *web newsletter portal*
- A *printable PDF* version
- Newsletter should contain *multiple well-researched articles* on a selected domain, excluding sensitive areas like *politics, **religion, or **celebrity news*.
### Key Requirements:
#### Tooling and Resources

- *Avoid: **SerpAPI* (noisy results)
- *Prefer: **Premium APIs* with curated news
- *Optionally use: **YouTube* or *RSS feeds*
- Start with *Streamlit, then enhance with **HTML + CSS*
####  Agent Framework & Architecture

- Use *BDI (Belief-Desire-Intention)* model loosely
- Structure:
	- *Coordinator agent* (central control)
	- *Specialist agents* (dedicated roles)
	- *Supervisors* for agent self-reflection
	- Team approach is crucial.

### 🗓 Timeline & Deliverables

- Project duration: *2 weeks*
- Additional deliverable: *Podcast or video* explaining:
	- Purpose
	- Value
	- Process  

## Prompt Engineering Guide

### Basics of Prompting

- A prompt = *instruction + context + examples*
- Better prompts = *better model output*

*Example:*

   ![Basic_of_prompt.jpeg](./Basic_of_prompt.jpeg)

### Prompting techniques:

1. *Zero-shot prompting*: Asking a question without providing examples or explanations.
2. *Few-shot prompting*: Giving a model a few examples but without detailed reasoning steps.
3. *Chain-of-thought*: This is a powerful technique where the examples provided to the LLM include step-by-step reasoning processes, enabling the model to "think" and arrive at correct answers for logical puzzles. This was a significant discovery that led to further developments like Tree of Thought and Graph of Thought.
	
    ![Chain_of_thought.png](./Chain_of_thought.png)

4. *Self-consistency*: To improve accuracy, especially for complex problems or those with multiple perspectives, run the LLM multiple times to generate diverse reasoning paths and solutions. Then, either take a majority vote on the answers or use another agent to synthesize a nuanced answer from the multiple perspectives. This is an "ensemble approach".

	![self-consistency.jpeg](./self-consistency.jpeg)

5. *Meta-prompting* (ask LLM to improve your prompt)

	![Meta_prompting.png](./Meta_prompting.png)

### Key characteristics of Meta-prompting:

1. Structure-oriented: Prioritizes the format and pattern of problems and solutions over specific content.
2. Syntax-focused: Uses syntax as a guiding template for the expected response or solution.
3. Abstract examples: Employs abstracted examples as frameworks, illustrating the structure of problems and solutions without focusing on specific details.
4. Versatile: Applicable across various domains, capable of providing structured responses to a wide range of problems.
5. Categorical approach: Draws from type theory to emphasize the categorization and logical arrangement of components in a prompt.  


---

# AI-Assisted Coding Best Practices Summary


## Cursor Rules: System Prompts for Coding Excellence

*Cursor Rules* are YAML- or Markdown-formatted files that define *custom coding standards, best practices, and constraints* for the [Cursor](https://www.cursor.sh) AI coding assistant.
Cursor *uses these rules to guide all completions, refactorings, and suggestions* — making your AI feel more like a wise collaborator than a generic copilot. Cursor rules are in essence, system prompts that modulate the behavior of the AI agent to align with specific coding standards and preferences.

*Creating cursor rules*:
Create a .mdc file in the following directory
your-project/.cursor/rules/
as your-rule-name.mdc

Example:


---
description: Disallow print statements; enforce use of logging
globs:
  - "**/*.py"
priority: 1
---

# Logging Only

- Disallow all `print()` statements.
- Use `loguru` or `logging` for all output.

## Enforce

- Flag any use of `print()`.
- Suggest replacing it with `logger.info()` or similar.


## Key Considerations while Crafting Cursor Rules
### Project Awareness

Always read the entire project codebase** before writing code to ensure consistency with existing patterns, utilities, and libraries.


![Rule_Type.png](./Rule_Type.png)

This prevents reinventing functionality (e.g., using a one-line utility for directory validation instead of writing new code).

### Role Definition

- Define Cursor as a *Python expert* with deep knowledge of best practices, idioms, and design patterns.
- Emphasize writing *idiomatic code* (following Python conventions) over quick, functional code.
- Prioritize *maintainability*, as code is a “transitional property” often handled by future maintainers.

![Role_Definition.png](./Role_Definition.png)

### Coding Standards

- Use *Python 3.12* for compatibility with AI libraries.
- Employ *UV* for dependency management, *Ruff* for formatting and linting - enforcing *PEP 8, and **Google-style docstrings* for documentation.
- Enforce *strict type annotations* for readability and error detection by tools like Ruff.
- Use *Loguru* for logging instead of print statements to support site reliability engineers in debugging.
- Limit *cyclomatic complexity (<10)* and *nesting depth (<2)* to adhere to the human brain’s channel capacity (7 ± 2 rule), reducing bugs in nested code.
- Favor *early returns* and *guard clauses* to simplify logic.

![Python_Styles.png](Python_Styles.png)

### Design by Contract

- Enforce *preconditions* (e.g., validating that a factorial input is a positive integer) and *postconditions* (e.g., ensuring a valid integer output).
- Implement *invariants* (e.g., a bank account balance cannot be negative).
- *Fail fast* to catch errors early, critical in high-stakes systems (e.g., NASA spacecraft).

### Modular Design

- Follow the *Single Responsibility Principle (SRP)*: each module, function, or class should handle one task.
- Prefer *composition over inheritance* to avoid overengineering.
- Use *absolute imports* to prevent brittle relative imports.
- Organize code in src/, tests in test/, and documentation in docs/.

### Documentation and Metadata

- Include *file headers* with a short description, author, and maintainers for traceability.
- Auto-generate documentation from docstrings.
- Keep headers updated with code changes via Cursor automation.

![File_Header_Rules.png](./File_Header_Rules.png)
### Performance and Concurrency

- Use **async/await** for I/O-bound tasks to handle blocking calls.
- Apply *LRU caching* for expensive, deterministic functions (e.g., factorial).

## Practical Application: PDF Downloader Module

We developed a production-ready PDF downloader module from a simple function, aligning with the goal of maximizing software development efficiency while maintaining quality standards using Cursor.

### Features

- *Retries* for network reliability to handle intermittent outages.
- *Custom exceptions* for robust error handling.
- Comprehensive *logging* with loguru for debugging.
- *Type annotations* and *Google-style docstrings* for clarity.
- *Modular, non-nested code* to minimize complexity.
### Process

- Initialize a project with *UV*, creating a structured directory (src/, test/, docs/).
- Use a setup script (ensure_config) to configure the environment and library naming (e.g., svlearn_fathers_day).
- Build and publish the library to *PyPI* using uv build and uv publish.

## Crafting Effective Cursor Rules

- *Personalization*: Rules should reflect individual coding philosophy, not blindly adopted from sources like "awesome cursor rules" online.
- *Modularity*: Organize rules into separate files for maintainability, avoiding monolithic files.
- *Iterative Refinement*: Continuously refine rules to resolve contradictions and align with project needs, using reasoning models to check for conflicts.
- *Strong Language*: Use “always,” “never,” and symbols (e.g., ✅, ❌) to signal strict requirements to the LLM.
- *Balance*: Avoid overengineering (e.g., excessive design patterns) while ensuring clarity, testability, and extensibility.

## Key Takeaways

- Effective AI-assisted coding with Cursor requires *detailed, personalized system prompts* as *cursor rules* to enforce idiomatic, maintainable, and robust code.
- Design modular cursor rules to:
	- include *project awareness, **strict type annotations, **design by contract, **modular design, and **comprehensive documentation*.
	- limit *complexity and nesting* to enhance readability and reduce bugs, respecting human cognitive limits.
- A production-ready module, the PDF downloader, demonstrates the impact of these rules, incorporating retries, logging, and clear documentation.
- Craft cursor rules *iteratively*, reflecting personal preferences and project requirements, to maximize code quality and longevity.
