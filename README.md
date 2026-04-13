# Autonomous Client Research Agent

<video src="https://github.com/user-attachments/assets/bdee2400-959c-4531-b6d0-849f4e8b75a6" controls width="700"></video>

**The Problem**

B2B prospecting and client vetting are still far more manual than they should be. Assessing whether a target company aligns with specific strategic, commercial, or technical criteria often means spending hours searching websites, extracting relevant information, and piecing together a view from fragmented sources. That slows down decision-making and makes consistent evaluation difficult at scale.

**The Solution**

I built a fully autonomous, multi-agent web research system on LangGraph that automates this entire process. The system scrapes, analyses, and evaluates target companies against a strictly defined criteria matrix, allowing potential clients to be filtered quickly and consistently. Rather than relying on repetitive manual research, the agentic workflow breaks the task into structured stages, enabling faster prospect qualification, more reliable screening, and a far more scalable approach to client research. 

**Core Tech Stack**

- **AI/Agent Framework:** LangGraph, LangChain, OpenAI.
- **Search & Scraping:** Exa API, Firecrawl.
- **Data Structure:** Pydantic, Markdown (requirements.md).
- **Observability:** LangSmith.

**Key Features & Engineering Justifications**

- **Graph-Based Architecture:** Engineered a stateful workflow using LangGraph to manage the complex routing between search, scraping, and evaluation nodes.
- **Strategic Resource Management:** Intentionally separated the search and scrape phases. The agent uses Exa for rapid, low-cost semantic searching to find the right URLs, and only deploys Firecrawl (which is credit-heavy) for deep-scraping highly qualified targets.
- **Human-in-the-Loop (HITL):** Implemented a mandatory pause node. After the AI expands the user's initial query via a Prompt Optimiser node, execution suspends until a human approves the finalised search strategy, preventing runaway API costs.
- **Strict Adherence to Criteria:** The agent cross-references scraped company data against a strict requirements.md file. It leverages Pydantic structured outputs to guarantee the final evaluation is delivered in a strict, predictable JSON format.
- **Deep Tracing:** Integrated LangSmith to trace the exact path of the LangGraph execution, monitoring token usage per node and debugging routing logic.
