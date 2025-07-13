# **SAL-CP 🧠🤝**

**(Self-Aware LLM Communication Protocol)**

The native, context-aware messaging protocol of the **[LLMunix](https://github.com/EvolvingAgentsLabs/llmunix)** Operating System, enabling complex, multi-agent collaboration and emergent intelligence.

<p align="center">
  <a href="https://github.com/EvolvingAgentsLabs/llmunix/blob/main/LICENSE"><img src="https://img.shields.io/badge/license-Apache--2.0-blue.svg" alt="License"></a>
  <a href="https://evolvingagentslabs.github.io/"><img src="https://img.shields.io/badge/labs-EvolvingAgentsLabs-brightgreen" alt="Labs"></a>
  <a href="#"><img src="https://img.shields.io/badge/status-alpha_implementation-orange.svg" alt="Status"></a>
</p>

> 🌐 **Part of [Evolving Agents Labs](https://evolvingagentslabs.github.io)** | 🔬 [View All Experiments](https://evolvingagentslabs.github.io#experiments) | 📖 [Project Details](https://evolvingagentslabs.github.io/experiments/llmunix.html)

---

## **The `LLMunix` Communication Layer**

In complex tasks, a single agent is not enough. True autonomy requires a team of specialized agents that can collaborate, delegate, and share knowledge. SAL-CP is the protocol that makes this possible within the `LLMunix` framework.

It is **not a separate library**, but a core set of communication patterns and message structures implemented directly within `LLMunix`'s virtual tools. It enables agents to communicate their **cognitive state**, **resource constraints**, and **task context**, moving beyond simple text payloads to achieve a shared understanding.

## **How SAL-CP is Implemented in `LLMunix`**

SAL-CP is brought to life through a suite of virtual tools defined in the master `GEMINI.md` manifest. These tools form the "network stack" for the agents.

*   `send_message`: Sends a point-to-point, prioritized message to another agent.
*   `check_messages`: Allows an agent to check its inbox, filtering by priority.
*   `broadcast_message`: Posts a system-wide announcement to a topical bulletin board.

These tools don't just send text; they construct a rich, structured SAL-CP message.

### **The SAL-CP Message Standard**

Every message sent using the `send_message` tool is a Markdown file with structured YAML frontmatter, creating a self-describing communication packet.

**Example:** A message from the `CEOAgent` to the `MarketAnalystAgent`.

**File:** `workspace/messages/inbox/MarketAnalystAgent/msg_1720198200_CEOAgent.md`

```markdown
---
# SAL-CP/v1.0 Header
message_id: msg_1720198200_CEOAgent
from: CEOAgent
to: MarketAnalystAgent
timestamp: 1720198200
priority: high
thread_id: campaign_ecoflow_pro

# Contextual Payload
payload:
  type: TASK_REQUEST
  content: "Initiate full market analysis for the new 'EcoFlow Pro' product launch. Focus on sustainable water purification market."

# Sender's Self-Awareness Context
context:
  cognitive_state: "PLANNING_DELEGATION"
  confidence: 0.9
  constraints:
    - "max_budget: $500"
    - "deadline: 24_hours"

# Requirements for the Recipient
requirements:
  response_format: "structured_report"
  required_context:
    - "permanent:SustainableWaterMarket_Trends_2025_07_05" # Instructs analyst to check memory first
---

**Directive Details:**

Please provide a report including:
1.  Top 3 competitors with market share.
2.  Key consumer trends in eco-friendly home appliances.
3.  Pricing strategy recommendations.

Leverage existing permanent memory before conducting new web research to save time and resources.
```

This single message demonstrates the power of SAL-CP:
*   It's a **clear task delegation** (`TASK_REQUEST`).
*   It carries **priority** and **deadlines**.
*   The sender shares its **cognitive state** ("I am currently delegating").
*   It tells the receiver what **knowledge to presuppose** (`required_context`), guiding it to use the `LLMunix` memory system efficiently.

## **Core Research Concepts Enabled by SAL-CP in `LLMunix`**

### 🧠 **Cognitive State Sharing**

The `SystemAgent` firmware in `GEMINI.md` instructs all agents to include their current state in their communications. This allows for intelligent routing and interruption handling. An agent receiving a message from another agent that is `BLOCKED` can decide to either help or re-prioritize its own work.

### 📊 **Context Preservation Across Handoffs**

When the `CEOAgent` delegates a writing task to the `ContentWriterAgent`, the SAL-CP message includes keys to relevant `task` and `permanent` memories. The writer agent doesn't start from a blank slate; it receives a "briefing packet" containing the market analysis and strategic decisions, ensuring consistency.

### 🤝 **Emergent Collaboration Patterns**

Because the agents and their communication tools are defined in editable Markdown, complex collaboration patterns can emerge.

**Example: A Peer Review Loop**

1.  **`ContentWriterAgent`** finishes a draft. It sends a SAL-CP message to the `QAReviewAgent`.
    *   `to: QAReviewAgent`
    *   `payload.type: REVIEW_REQUEST`
    *   `payload.content: "Draft of blog post is complete. Path: workspace/drafts/blog1.md"`
    *   `context.cognitive_state: AWAITING_FEEDBACK`

2.  **`QAReviewAgent`** runs its `check_messages` tool, sees the request, and reads the draft.
3.  It finds issues and sends a message back.
    *   `to: ContentWriterAgent`
    *   `payload.type: REVISION_REQUEST`
    *   `payload.content: "Review complete. Factual claim on line 32 needs a source. Please revise."`
    *   `context.cognitive_state: PROVIDING_FEEDBACK`

This entire feedback loop is orchestrated autonomously through the SAL-CP constructs implemented by the `LLMunix` virtual tools.

## **Running the System**

SAL-CP is not run separately; it is the **native communication protocol** you activate when running any multi-agent workflow in `LLMunix`.

1.  **Boot the System:**
    ```bash
    ./llmunix-boot
    ```
    This creates the `workspace/messages/` directory structure.

2.  **Launch Gemini CLI & Provide a Goal:**
    ```bash
    gemini
    > Create a comprehensive marketing campaign for "EcoFlow Pro".
    ```

3.  **Observe SAL-CP in Action (Using the Canvas UI):**
    *   The **Agent Graph** in the [LLMunix Canvas](https://github.com/EvolvingAgentsLabs/llmunix-canvas) will visually draw arrows between agents as `send_message` calls are made.
    *   The **Workspace Explorer** will show new message files appearing in agent inboxes.
    *   Clicking on a message file will reveal the full, structured SAL-CP Markdown content.

## **Research Implications & Future Direction**

SAL-CP, as implemented in `LLMunix`, proves that a rich, self-aware communication protocol is not just a theoretical concept but a practical tool for building more capable agentic systems. It transforms a collection of individual agents into a cohesive, intelligent, and self-coordinating team.

The future of this research lies in evolving the protocol to support even more complex interactions, such as:
*   **Capability Negotiation:** An agent broadcasting a task and other agents bidding on it based on their self-assessed `capability_match` and `confidence_level`.
*   **Automated Pattern Detection:** A `MemoryAnalysisAgent` that observes SAL-CP message flows to identify and learn effective vs. ineffective collaboration patterns, which it then stores in permanent memory to optimize future teamwork.

---

**This project is a core component of the `LLMunix` ecosystem and represents ongoing research by Evolving Agents Labs into the future of decentralized AI collaboration.**

---

## Connect

**Research Contributors**: [Matias Molinas](https://github.com/matiasmolinas) • [Ismael Faro](https://github.com/ismaelfaro)

**Organization**: [EvolvingAgentsLabs](https://github.com/EvolvingAgentsLabs) • **Lab Site**: [evolvingagentslabs.github.io](https://evolvingagentslabs.github.io)

---