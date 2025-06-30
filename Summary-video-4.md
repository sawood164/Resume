**Video-4**

---

## Session Summary

This lecture covered two groundbreaking research papers:

1. **ReAct**: Introduces a framework that interleaves **reasoning (thoughts)** and **actions** in LLMs.
2. **MEGPT**: Adds structured **memory management** to LLMs, allowing long-term personalized interaction.

Together, these approaches shift LLMs from simple prompt-response engines to **agentic systems** capable of reasoning, interacting with environments, and remembering context.

---

## 📜 Paper 1: ReAct — Synergizing Reasoning and Acting

### Core Idea

ReAct enables language models to:

- **Reason** using internal thoughts (called "reasoning traces")
- **Act** using tools like web search or navigation
- Combine these in an **interleaved manner** for better decision-making

### Motivation

| Approach         | Limitation                                |
| ---------------- | ----------------------------------------- |
| Chain of Thought | Lacks grounding, prone to hallucinations  |
| Tool-Only        | Blind actions without context             |
| Plain LLM        | Flat output, no environmental interaction |

### Key Insight

ReAct treats **thoughts** as valid actions in the language space. These thoughts don't affect the external world but influence the LLM's next steps.

> "Reasoning trace = action in language that affects future context"

---

## The Agentic Loop: Observe → Think → Act

ReAct operationalizes the agent loop:

```
Observe → Think → Act → Observe → Think → Act ...
```

- Thoughts are inserted as internal planning steps
- Actions invoke tools
- Observations update state

---

## Case Study 1: Apple Remote (HotpotQA)

**Question:** "Aside from the Apple Remote, what other device can control the program Apple Remote was originally designed to interact with?"

### Old Approaches Fail:

- Standard LLM hallucination: "iPod"
- CoT hallucination: "Apple TV"
- Act-only search: retrieves but fails to reason, answers "Yes"

### ReAct Solves:

1. **Thought**: I need to search Apple Remote
2. **Act**: Search[Apple Remote]
3. **Obs**: It controls Front Row
4. **Thought**: What else controls Front Row?
5. **Act**: Search[Front Row]
6. **Thought**: It can be controlled via keyboard
7. **Act**: Answer = "keyboard function keys"

![alt text](Screenshot-1.png) — Side-by-side comparison of Standard vs CoT vs Act-Only vs ReAct

---

## Case Study 2: Pepper Shaker (AlfWorld)

**Task:** "Put pepper shaker in drawer."

### Pure Action-Only Agent:

- Randomly moves, opens drawers, no clear goal, fails.

### ReAct Agent:

1. **Thought**: Pepper likely on counter or cabinet
2. **Act**: Visit counters
3. **Obs**: Found shaker on Counter 3
4. **Thought**: I must place this in drawer
5. **Act**: Go to drawer → open → insert

**Loop:** Reason → Act → Observe → Reason again

---

## ReAct Theory: Augmented Action Space

### Equation:

\(\tilde{a}\_t \in \mathcal{A} \cup \mathcal{L}\) Where:

- \(\mathcal{A}\) = tool actions
- \(\mathcal{L}\) = language actions (thoughts)

Thoughts:

- Are actions in the LLM's internal reasoning space
- Have no effect on external world
- Update internal context for next steps

\*\*![alt text](<Screenshot -2.png>) — Equation + hand-drawn observe-think-act loop from paper

---

## 📜 Paper 2: MEGPT — Memory-Augmented LLMs

### Motivation

LLMs suffer from **finite context windows**. Important past information is lost across sessions.

MEGPT solves this by introducing:

- **Working Context**: Current memory
- **Archival Storage**: Long-term memory
- **Recall Storage**: Memory fetch mechanism

---

## Case Study: Conversational Memory

### Chat 1 (Feb 7)

- User: "My bf James baked me a birthday cake"
- System saves:
  - `Birthday = Feb 7`
  - `Boyfriend = James`

### Chat 2 (Later)

- User: "We went to Six Flags"
- Memory Recall:
  - Recovers "James and I met at Six Flags"
- System responds: "Did you go with James?"

\*\*![alt text](<Screenshot -3.png>) — Chat + memory pressure + recall from MemGPT diagram

## Memory Flow in Action

a) When memory is full → System triggers memory pressure

b) Relevant facts are pushed to archival storage

c) On future queries → Recall storage pulls those back

d) Memory is reintroduced through function calls, enabling continuity and state

Example from earlier:

Chat: “My BF James baked me a cake” →
Saved as: Birthday = Feb 7, Boyfriend = James

Later:

Query: “Did you go to Six Flags?” →
Recall triggers James and I met at Six Flags from past memory

---

## MEGPT Memory Architecture

\*\*![alt text](<Screenshot -4.png>) — Full MEGPT architecture block diagram

**Why MEGPT Was Needed**

Traditional LLMs are limited by their finite context window (e.g., 8k–100k tokens). For long conversations, multi-session tasks, or stateful reasoning, this becomes a bottleneck.

**MEGPT solves this by treating LLMs like operating systems, using:**

a) Main memory (working context)

b) Long-term memory (archival + recall storage)

c) Functions to read/write, schedule memory movement, and maintain continuity

### 🔍 Memory Components

| Part                | Role                          |
| ------------------- | ----------------------------- |
| System Instructions | Static rules                  |
| Working Context     | Active short-term memory      |
| FIFO Queue          | Token overflow buffer         |
| Output Buffer       | Final model output            |
| Archival Storage    | Persistent long-term memory   |
| Recall Storage      | On-demand memory fetch        |
| Function Executor   | Runs memory calls and logic   |
| Queue Manager       | Manages write-read-token flow |

---

## Why It All Matters

| Component | Contribution                        |
| --------- | ----------------------------------- |
| ReAct     | Brings agentic reasoning to LLMs    |
| MEGPT     | Adds memory continuity across turns |

Together, they make LLMs:

- Reason like humans
- Act with goals
- Remember long-term context

---
