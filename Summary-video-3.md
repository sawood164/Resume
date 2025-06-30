Summary– Video-3
AI Foundations – Summer 2025

🌐 MCP Server Deployment Design: Options & Reasoning
The discussion begins by posing a core deployment dilemma:

“Should I run multiple MCP servers in one Docker or isolate each MCP server in its own container?”

This opens the exploration of deployment strategies and isolation tradeoffs:

- On Cloud, your unit is a VM (Compute Node).
- On Premise, your unit is a Dedicated Server.
- Regardless of environment, Dockerization is mandatory.

🌐 Why Dockerization is Non-Negotiable
Docker (or any container tech) provides namespace isolation for:

- File systems
- Libraries
- Dependencies

Compared to VMs:

- VM virtualizes hardware.
- Containers share host but isolate execution context.

Containers are built using Linux's cgroups, making Linux essential for production deployments.

🌐 Recommended MCP + Docker Strategy
“Have one Docker instance that runs your MCP.”

- Use Kubernetes to elastically scale MCP instances as needed.
- Group MCPs by domain (Finance, Medical) to avoid:
  - Security overhead
  - Access control complications

![alt text](<Screenshot -1.png>)

🌐 Domain-Specific Isolation Strategy
“Domain-specific MCP servers make logical and secure sense.”

Tools should be bundled per-domain:

- Avoid exposing irrelevant tools to unrelated clients.
- Reduces surface area for misconfigurations.

Within a domain:

- Do not overload a single MCP with hundreds of tools.
- Optimal range: ~5–15 tools per domain MCP.

🌐 Simple Architecture – Unified MCP Server

- Tools are lightweight and run within the MCP Docker.
- MCP acts as a facade, calling local implementation classes.

Architecture:

- Compile tool code into .whl files.
- Bundle into a single Docker image.
- Deploy as a unified service.

![alt text](<Screenshot -2.png>)

🌐 Intermediate Architecture – Delegated Implementations

- MCP facade calls external services for heavy tools.
- Each tool runs in its own Docker, possibly with its own GPU or memory environment.
- Communication via REST endpoints.

Benefits:

- Better fault isolation.
- Tailored hardware for each tool.

![alt text](<Screenshot -3.png>)

🌐 Scalable Architecture – Ray Inference Server
When tool traffic is high or compute-intensive:

- Use Ray for distributed inference.
- MCP delegates tool execution to Ray-managed workers.

Ray handles:

- Load balancing
- GPU distribution
- Endpoint exposure

“Even your tool doesn’t know which instance executed the call.”

![alt text](<Screenshot -4.png>)

🚦 Deployment Escalation Strategy
| Stage | Description | When to Use |
|-------|------------------------------------|----------------------------|
| v0.1 | All tools in MCP (simple) | Low traffic, dev phase |
| v1 | REST-based tool delegation | Moderate load, some complexity |
| v2 | Distributed inference via Ray | High traffic, LLMs, GPUs |

“Release 1 should be simple, release 2 intermediate, release 3 should scale.”

🔗 Caching – Performance Enhancer

- Use caching wherever possible (weather, past results).
- Avoid caching real-time changing data (e.g. sports scores).
- Technologies: Redis, Quadrant

| Context             | Cache Use | Why                       |
| ------------------- | --------- | ------------------------- |
| Static weather data | Yes       | Data doesn’t change often |
| Live game scores    | No        | Needs real-time accuracy  |
| Post-game analysis  | Yes       | Read-only, high demand    |

🔗 Mixed Model Robustness Pattern
“Never embed heavy logic in the MCP server.”

- Use mixed process-thread models:

  - Each worker can have multiple threads.
  - Avoid crashing entire server due to one bad thread.

- Use speculative execution:
  - Run tasks on multiple workers.
  - Use result from fastest correct one.

🔗 Session Management in MCP Protocol

- MCP client-server communication is session-based.

Best practices:

- Auto-expire session after client disconnect.
- Offload session management to the framework.

“Good server architecture = good riddance to clients.”

🔗 Memory Persistence in Agentic Systems

- Use memory frameworks (e.g., Redis, Quadrant).
- Store full conversation logs tied to namespaces.
- Agent memory design = critical system layer.

“ChatGPT retains chat history – that’s the standard.”

🔗 Communication Protocols: SSE, Streaming

- SSE (Server-Sent Events) being replaced by HTTP2 Streaming.
- MCP frameworks should abstract these details.
- Let libraries like fast-mcp handle underlying transport.

🔗 Security & Sessions

- Role-based access control & session tokens matter but are peripheral.
- Focus is on AI & agentic systems, not auth flows.
- Leave session, token, and streaming protocol management to frameworks.

🔗 MCP Tools – GitHub Integration
GitHub itself is now a registered MCP tool.

“Agents can pull, review, fix, and push code autonomously.”

Example:

- Agent opens a GitHub repo.
- Reviews documentation.
- Explores modules.
- Scores repo quality.
- Suggests improvements.

🌐 Key Takeaways

- Always dockerize MCPs; use Kubernetes for orchestration.
- Start small → delegate → scale via Ray.
- Isolate tools per domain for clarity & security.
- Use caching, speculative execution, and distributed inference.
- Agent memory & session state handling are critical.
- Let frameworks handle protocol and session abstraction.
- Leverage the MCP ecosystem (like GitHub) for agentic actions.
