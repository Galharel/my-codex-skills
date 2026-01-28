# LangChain capability scan (reference)

> **Note:** Automated access to YouTube and some external sites may be blocked in the runtime. If you can access the videos, review them and update this reference with specific techniques demonstrated.
> - https://www.youtube.com/watch?v=S-T5OMEhQlA
> - https://www.youtube.com/watch?v=3daSUNpWErQ

## How to use this reference
When designing the agentic system, scan these capability areas and decide which should be included or proposed as options. For any choice that is unclear, ask a targeted question with 2–3 options and pros/cons.

## Capability areas to review in LangChain docs
Use these sections to find “cool stuff” or advanced features to propose:

1. **Agent orchestration patterns**
   - Multi-agent coordination, routing, and tool selection patterns.
   - Parallelism and retries in agent loops.

2. **Memory systems**
   - Conversation history vs. summary memory.
   - Long-term memory stores and retention strategies.

3. **Retrieval-Augmented Generation (RAG)**
   - Document loaders, text splitters, embeddings, vector stores.
   - Retrieval strategies: similarity, MMR, hybrid retrieval.
   - Reranking and citation workflows.

4. **Tooling and integrations**
   - Tool calling patterns and tool schemas.
   - External API/tool registry patterns.
   - MCP server usage (if required by the architecture).

5. **Prompt engineering & guardrails**
   - System vs. developer prompts; role separation.
   - Safety and policy enforcement layers.

6. **Evaluation and observability**
   - Tracing, debugging, and evaluation harnesses.
   - Automated checks for correctness and safety.

## Suggested “advanced feature” prompts to explore
- “What is the best multi-agent routing strategy for task type X?”
- “How do we do memory summarization without losing key facts?”
- “What are LangChain’s recommended RAG pipelines for large corpora?”
- “How do we implement tool permissions and sandboxing?”
- “What is the best evaluation workflow for prompt regressions?”

## Output integration guidance
When a capability area is selected:
- Describe the design choice in `docs/agentic.design.packet.json`.
- Note dependencies or impacts on backend APIs, data stores, or security controls.
- Flag any unresolved decision as TBD and request user confirmation.
