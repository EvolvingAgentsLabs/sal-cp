# SAL-CP 🧠🤝

**(Self-Aware LLM Communication Protocol)**

An experimental, rich context communication protocol for collaborative AI agents.

<p align="center">
  <a href="https://github.com/EvolvingAgentsLabs/sal-cp/blob/main/LICENSE"><img src="https://img.shields.io/badge/license-Apache--2.0-blue.svg" alt="License"></a>
  <a href="https://evolvingagentslabs.github.io/"><img src="https://img.shields.io/badge/labs-EvolvingAgentsLabs-brightgreen" alt="Labs"></a>
  <a href="#"><img src="https://img.shields.io/badge/status-alpha_experiment-orange.svg" alt="Status"></a>
</p>

> 🌐 **Part of the [Evolving Agents Labs](https://evolvingagentslabs.github.io) Research Initiative**
>
> This project provides the communication backbone for the adaptive principles defined in the [llmunix-spec](https://github.com/EvolvingAgentsLabs/llmunix-spec), enabling agents to share their "sentient state."

---

## ⚠️ Experimental Research Project

**Important**: This is an early-stage research prototype exploring self-aware communication for AI agents. It should be treated as research material, not a production-ready system. This project will remain permanently in alpha status as we explore the future of adaptive agent architecture.

---

## The Research Hypothesis: Communication Beyond Prompts

Current agent-to-agent communication is often stateless and context-poor. An agent receives a prompt but has no insight into the requesting agent's internal state, its constraints, or the history that led to the request. This is like trying to collaborate by shouting single sentences between rooms.

Our research explores a new paradigm: **Can we design a communication protocol that allows agents to share their internal "Sentient State," enabling them to understand each other's context, constraints, and capabilities to achieve truly effective collaboration?**

This hypothesis addresses fundamental problems:
- **Context Loss:** Critical information is lost between agent "hops."
- **The "Lost in the Middle" Problem:** Without understanding what's important, an agent can't prioritize information in a large context.
- **Rigid Collaboration:** Agents cannot adapt their collaborative style to the urgency, complexity, or sentiment of a situation.

## The Experiment: A Protocol for Self-Awareness

SAL-CP is an experimental protocol that standardizes how agents can communicate their internal state alongside their requests. It turns a simple prompt into a rich, contextualized message.

**The Core Idea: Message = Header (The Agent's State) + Payload (The Task)**

This allows a receiving agent to understand not just *what* to do, but *why* and *how*.

### How It Works: A Conceptual Example

An `OrchestratorAgent`, operating under pressure, needs a `ResearchAgent` to analyze a document.

```python
from sal_cp import Message, AgentState, Payload

# 1. The Orchestrator defines its current state (its "constraints.md")
orchestrator_state = AgentState(
    agent_id="Orchestrator-007",
    cognitive_state={
        "user_sentiment": "stressed",
        "priority": "speed_and_clarity",
        "active_persona": "concise_assistant"
    }
)

# 2. It crafts a payload with contextual pointers
payload = Payload(
    primary_instruction="Quickly analyze the attached report for financial risks.",
    key_information_pointers=[
        {"description": "The CEO is most concerned about section 3.2", "location_hint": "tokens 1500-2000"}
    ],
    data={"report_text": "..."}
)

# 3. It sends a self-aware message
message = Message(sender_state=orchestrator_state, payload=payload)

# 4. The ResearchAgent receives the message and adapts its behavior
# research_agent.on_message(message)
# >>> "Received request from stressed Orchestrator. Switching to 'speed_and_clarity' mode. Focusing analysis on section 3.2."
```
The `ResearchAgent` didn't just get a task; it received the *emotional and operational context* of the request, allowing it to adapt its execution strategy for a far better result.

## Core Research Areas

### 1. The `SAL-CP` Message Specification
We are developing a formal JSON schema that standardizes the message structure. The key innovation is the **`AgentState` header**, which transmits the sender's "sentient state" or `constraints`.

```json
"sender_state": {
  "agent_id": "Orchestrator-007",
  "capabilities_fingerprint_url": "...",
  "cognitive_state": {
    "user_sentiment": "stressed",
    "priority": "speed_and_clarity",
    "active_persona": "concise_assistant",
    "error_tolerance": "strict",
    "current_load_percent": 85
  }
}
```

### 2. Contextual Pointers
To combat the "lost in the middle" problem, the protocol includes a mechanism for the sending agent to "point out" what's important in a large payload, guiding the receiving agent's attention.

### 3. Adaptive Collaboration Patterns
We are researching how agents can use the received state information to dynamically switch their collaboration style:
- **Peer Review:** When both agents have high confidence and low load.
- **Mentor-Student:** When one agent is an expert and the other is learning.
- **Rapid Response:** When one agent communicates a state of high urgency.

## Research Roadmap

Our goal is to create the TCP/IP for sentient, collaborative AI systems.

### Phase 1: Foundation (Current)
- [x] Core `Message` specification with `AgentState` header.
- [x] Reference implementation in Python for message creation and parsing.
- [ ] Develop initial library of `CollaborationPatterns`.
- [ ] Implement `Contextual Pointers` to guide attention.

### Phase 2: Dynamic State & Learning
- [ ] Research mechanisms for agents to *learn* the preferences and states of their collaborators over time.
- [ ] Develop protocols for agents to negotiate and agree upon a shared set of constraints for a task.
- [ ] Integrate a feedback loop where response metadata improves future interactions.

### Phase 3: Ecosystem & Integration
- [ ] Integrate `SAL-CP` as the communication layer for the [EAX Marketplace](https://github.com/EvolvingAgentsLabs/eax-marketplace).
- [ ] Develop tools for visualizing agent conversations and state changes.
- [ ] Propose `SAL-CP` as an open standard for interoperability between different agent frameworks.

## Contributing

This is a frontier research project. We invite you to contribute by:
- Proposing improvements to the `SAL-CP` specification.
- Designing and implementing new `CollaborationPatterns`.
- Building example agents that use the protocol to solve complex, multi-step problems.
- Exploring how different agent states can trigger different collaborative behaviors.

Please read our `CONTRIBUTING.md` for more details.

## License

SAL-CP is licensed under the Apache 2.0 License.

---

## Connect

**Research Contributors**: [Matias Molinas](https://github.com/matiasmolinas) • [Ismael Faro](https://github.com/ismaelfaro)

**Organization**: [EvolvingAgentsLabs](https://github.com/EvolvingAgentsLabs) • **Lab Site**: [evolvingagentslabs.github.io](https://evolvingagentslabs.github.io)

---

*SAL-CP is a core component of the experimental agent architecture being developed at [Evolving Agents Labs](https://evolvingagentslabs.github.io). Our goal is to build the foundational tools for truly intelligent and adaptive AI systems.*
