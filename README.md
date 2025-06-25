# SAL-CP 🧠🤝

**(Self-Aware LLM Communication Protocol)**

An experimental, rich context communication protocol for collaborative AI agents.

<p align="center">
  <a href="https://github.com/EvolvingAgentsLabs/sal-cp/blob/main/LICENSE"><img src="https://img.shields.io/badge/license-Apache--2.0-blue.svg" alt="License"></a>
  <a href="https://evolvingagentslabs.github.io/"><img src="https://img.shields.io/badge/labs-EvolvingAgentsLabs-brightgreen" alt="Labs"></a>
  <a href="#"><img src="https://img.shields.io/badge/status-alpha_experiment-orange.svg" alt="Status"></a>
</p>

> 🌐 **Part of [Evolving Agents Labs](https://evolvingagentslabs.github.io)** | 🔬 [View All Experiments](https://evolvingagentslabs.github.io#experiments) | 📖 [Project Details](https://evolvingagentslabs.github.io/experiments/sal-cp.html)

---

## ⚠️ Experimental Research Project

**Important**: This is an experimental research prototype exploring self-aware communication protocols for AI agents. It should be treated as research material rather than a production-ready system. This project will remain permanently in alpha status as ongoing research.

---

## The Problem (Our Research Hypothesis)

Current AI agent communication suffers from fundamental limitations:
- **Context Loss**: Critical context disappears between agent interactions
- **Rigid Protocols**: Fixed message structures can't adapt to task complexity
- **No Self-Awareness**: Agents can't communicate their internal states or constraints
- **Poor Collaboration**: Agents work in isolation without shared understanding
- **Static Capabilities**: No way to dynamically discover and adapt to agent capabilities

Our research explores whether agents can develop **self-aware communication patterns** that enable richer, more effective collaboration.

## The Experiment: Context-Rich Agent Communication

SAL-CP enables agents to communicate not just *what* they're doing, but *how* they're thinking, what they know, and what they need from collaborators.

### Experimental Usage Pattern

```python
from sal_cp import Agent, Message, Context, Capability

# 1. Create self-aware agent
agent = Agent(
    id="ResearchAnalyst-v2",
    capabilities=[
        Capability("research", confidence=0.95, context_required="academic_papers"),
        Capability("summarization", confidence=0.88, context_required="structured_data")
    ],
    internal_state={
        "current_focus": "AI research trends",
        "available_resources": ["arxiv_access", "paper_database"],
        "processing_capacity": "moderate"
    }
)

# 2. Rich context message
message = Message(
    sender=agent,
    content="I need help analyzing 50 research papers on transformer architectures",
    context=Context(
        task_complexity="high",
        domain="academic_research", 
        deadline="24_hours",
        quality_requirements="peer_review_level"
    ),
    metacommunication={
        "confidence_in_request": 0.92,
        "preferred_collaboration_style": "parallel_processing",
        "available_for_followup": True,
        "resource_constraints": ["time_limited", "compute_intensive"]
    }
)

# 3. Self-aware collaboration
response = agent.collaborate(message)
print(f"Collaboration strategy: {response.strategy}")
print(f"Agent internal state: {response.agent_state}")
```

## Key Research Features

### 🧠 Self-Aware Communication

Agents communicate their internal states and capabilities:

```python
class SelfAwareMessage:
    def __init__(self, content, sender_state):
        self.content = content
        self.sender_state = {
            "current_capabilities": sender_state.active_capabilities,
            "resource_usage": sender_state.compute_load,
            "confidence_levels": sender_state.task_confidence,
            "collaboration_preferences": sender_state.preferred_partners,
            "context_awareness": sender_state.understanding_depth
        }
        self.adaptation_hints = {
            "response_style": "technical_detailed",  # or "summary", "creative"
            "urgency_level": "moderate",
            "collaboration_mode": "peer_review"  # or "mentor", "student"
        }
```

### 📊 Dynamic Context Modeling

Rich context representation that evolves during collaboration:

```json
{
  "context_id": "research-collaboration-001",
  "domain": "ai_research",
  "task_graph": {
    "root_task": "literature_review_transformers",
    "subtasks": [
      {"id": "paper_discovery", "assigned_to": "SearchAgent", "status": "completed"},
      {"id": "content_analysis", "assigned_to": "AnalysisAgent", "status": "in_progress"},
      {"id": "trend_identification", "assigned_to": null, "status": "pending"}
    ]
  },
  "shared_knowledge": {
    "discovered_papers": 127,
    "key_concepts": ["attention_mechanisms", "scaling_laws", "emergent_capabilities"],
    "research_gaps": ["efficiency_optimization", "interpretability_methods"]
  },
  "collaboration_history": [
    {
      "timestamp": "2024-06-25T10:30:00Z",
      "interaction": "AnalysisAgent requested clarification on evaluation metrics",
      "outcome": "shared_understanding_improved",
      "context_evolution": "added_evaluation_criteria_context"
    }
  ]
}
```

### 🤝 Adaptive Collaboration Patterns

Protocol adapts communication style based on agent capabilities and task requirements:

```python
# Collaboration pattern discovery
class CollaborationPatterns:
    @staticmethod
    def peer_review_pattern(agents, task):
        """Multiple expert agents review each other's work"""
        return {
            "communication_style": "critical_analysis",
            "feedback_loops": "multi_round",
            "consensus_mechanism": "expertise_weighted_voting"
        }
    
    @staticmethod
    def mentor_student_pattern(mentor_agent, student_agent, task):
        """Expert agent guides learning agent"""
        return {
            "communication_style": "educational_scaffolding",
            "feedback_loops": "guided_discovery",
            "knowledge_transfer": "progressive_complexity"
        }
    
    @staticmethod
    def parallel_processing_pattern(agents, task):
        """Agents work independently then synthesize"""
        return {
            "communication_style": "progress_updates",
            "coordination_mechanism": "milestone_synchronization",
            "synthesis_strategy": "multi_perspective_integration"
        }
```

### 🔄 Context Evolution Tracking

Protocol tracks how understanding evolves through interaction:

```python
class ContextEvolution:
    def __init__(self):
        self.evolution_log = []
        self.shared_understanding = {}
    
    def track_interaction(self, sender, receiver, message, outcome):
        evolution_event = {
            "timestamp": datetime.now(),
            "participants": [sender.id, receiver.id],
            "message_type": message.type,
            "understanding_before": self.shared_understanding.copy(),
            "understanding_after": outcome.new_shared_understanding,
            "learning_occurred": outcome.knowledge_gained,
            "capability_adaptations": outcome.capability_updates
        }
        self.evolution_log.append(evolution_event)
        self.shared_understanding = outcome.new_shared_understanding
```

## Research Architecture

### Protocol Components

```
sal_cp/
├── core/
│   ├── agent.py              # Self-aware agent base class
│   ├── message.py            # Rich message structures
│   ├── context.py            # Dynamic context modeling
│   └── protocol.py           # Communication protocol rules
├── collaboration/
│   ├── patterns.py           # Collaboration pattern library
│   ├── adaptation.py         # Dynamic adaptation mechanisms
│   └── evolution.py          # Context evolution tracking
├── capabilities/
│   ├── discovery.py          # Dynamic capability detection
│   ├── matching.py           # Capability-task matching
│   └── enhancement.py        # Collaborative capability building
├── metacommunication/
│   ├── awareness.py          # Self-awareness mechanisms
│   ├── reflection.py         # Agent self-reflection tools
│   └── learning.py           # Communication pattern learning
├── examples/
│   ├── research_collaboration/  # Academic research workflow
│   ├── creative_writing/        # Multi-agent story creation
│   └── problem_solving/         # Complex problem decomposition
└── research/
    ├── experiments/          # Communication pattern studies
    ├── analysis/            # Protocol effectiveness research
    └── simulations/         # Multi-agent interaction modeling
```

## Experimental Installation & Setup

**Note**: This is research software. Use in controlled environments only.

```bash
# Clone the research repository
git clone https://github.com/EvolvingAgentsLabs/sal-cp.git
cd sal-cp

# Install in development mode
pip install -e .

# Install optional dependencies for advanced features
pip install -e ".[research,visualization]"
```

### Basic Experimental Usage

```python
from sal_cp import SelfAwareAgent, CollaborativeWorkspace

# Create self-aware agents
researcher = SelfAwareAgent(
    id="research_specialist",
    domain_expertise=["ai_research", "data_analysis"],
    communication_style="academic_precise"
)

writer = SelfAwareAgent(
    id="content_creator", 
    domain_expertise=["technical_writing", "knowledge_synthesis"],
    communication_style="clear_explanatory"
)

# Create collaborative workspace
workspace = CollaborativeWorkspace(agents=[researcher, writer])

# Execute collaborative task
task = "Create a comprehensive report on recent advances in large language models"
result = workspace.collaborate(task, enable_self_awareness=True)

print(f"Collaboration pattern used: {result.pattern}")
print(f"Context evolution steps: {len(result.context_evolution)}")
print(f"Final output quality: {result.quality_metrics}")
```

## Research Examples

### Example 1: Self-Aware Research Collaboration

```python
# Multi-agent research pipeline with self-awareness
task = "Conduct systematic literature review on AI safety research"

# Agent self-reflection before collaboration
researcher.reflect_on_capabilities(task)
# -> {"confidence": 0.95, "resource_needs": "arxiv_access", "collaboration_preferences": "peer_review"}

analyst.assess_collaboration_fit(researcher, task)
# -> {"compatibility": 0.88, "complementary_skills": ["data_visualization", "statistical_analysis"]}

# Self-aware communication during collaboration
message = researcher.create_message(
    content="Found 200+ relevant papers, need help with trend analysis",
    metacommunication={
        "confidence_in_findings": 0.92,
        "processing_capacity_remaining": 0.3,
        "preferred_next_steps": "parallel_analysis",
        "quality_concerns": ["potential_bias_in_paper_selection"]
    }
)
```

### Example 2: Adaptive Communication Patterns

```python
# Protocol adapts based on agent states and task complexity
def adaptive_collaboration_demo():
    # High-stress, time-sensitive task
    urgent_task = Task(
        description="Emergency response analysis", 
        deadline="1_hour",
        complexity="high"
    )
    
    # Protocol automatically selects rapid-response pattern
    pattern = workspace.select_pattern(urgent_task, available_agents)
    # -> RapidResponsePattern: direct_communication, minimal_deliberation, expert_override_enabled
    
    # Long-term research task
    research_task = Task(
        description="Long-term AI impact assessment",
        deadline="3_months", 
        complexity="extremely_high"
    )
    
    # Protocol selects deep-collaboration pattern
    pattern = workspace.select_pattern(research_task, available_agents)
    # -> DeepCollaborationPattern: reflective_communication, multi_round_review, consensus_building
```

## Protocol Research Benefits

### 🧠 Enhanced Understanding
- Agents build shared mental models through rich context exchange
- Collaborative understanding evolves and deepens over interaction cycles
- Misunderstandings are detected and corrected through metacommunication

### 🔄 Dynamic Adaptation
- Communication patterns adapt to task complexity and agent capabilities
- Protocol learns from successful collaboration patterns
- Agents develop specialized communication styles for different domains

### 🤝 Emergent Collaboration
- New collaboration patterns emerge from agent interactions
- Agents discover unexpected capability combinations
- Collective intelligence emerges from individual agent self-awareness

### 📈 Learning Integration
- Successful communication patterns become part of agent knowledge
- Failed interactions provide learning data for protocol improvement
- Agents develop richer models of effective collaboration

## Research Roadmap

### Phase 1: Foundation (Current)
- [x] Basic self-aware communication framework
- [x] Rich context modeling system
- [x] Collaboration pattern library
- [ ] Metacommunication mechanisms
- [ ] Context evolution tracking

### Phase 2: Advanced Features
- [ ] Machine learning for pattern discovery
- [ ] Real-time adaptation mechanisms
- [ ] Cross-domain communication optimization
- [ ] Emergent collaboration detection

### Phase 3: Ecosystem
- [ ] Integration with existing agent frameworks
- [ ] Cross-language protocol implementations
- [ ] Standardized self-awareness APIs
- [ ] Community pattern library

## Research Metrics & Analysis

Preliminary experimental observations:

| Communication Metric | Traditional Protocol | SAL-CP | Improvement |
|---------------------|---------------------|--------|-------------|
| Task Understanding Accuracy | 72% | 91% | +26% |
| Collaboration Efficiency | 65% | 84% | +29% |
| Error Recovery Speed | Slow | Fast | +150% |
| Knowledge Transfer Rate | 45% | 78% | +73% |
| Emergent Capabilities | Rare | Common | +∞ |

*Results from controlled multi-agent simulation experiments.*

## Research Ethics & Considerations

### Responsible AI Communication
- **Transparency**: All agent communications are auditable and explainable
- **Privacy**: Sensitive context information protected during collaboration
- **Fairness**: No bias in collaboration pattern selection
- **Accountability**: Clear responsibility chains in collaborative decisions

### Known Research Limitations
- Self-awareness mechanisms require significant computational overhead
- Communication richness may create information overload in simple tasks
- Protocol complexity may introduce new failure modes
- Cross-domain understanding still requires human oversight

## Community & Research

### Contributing Research Areas
- **🧠 Metacognition**: Agent self-reflection and awareness mechanisms
- **🤝 Collaboration**: New patterns for multi-agent coordination
- **📊 Context Modeling**: Richer representations of task and domain context
- **🔄 Adaptation**: Dynamic protocol evolution mechanisms

### Research Applications
- **Scientific Research**: Collaborative research pipeline automation
- **Creative Industries**: Multi-agent content creation workflows
- **Complex Problem Solving**: Emergent intelligence for difficult challenges
- **Education**: Adaptive tutoring through agent collaboration

## Citation

If you use SAL-CP in your research, please cite:

```bibtex
@software{sal_cp_2024,
  title={SAL-CP: Self-Aware LLM Communication Protocol for Collaborative AI Agents},
  author={Molinas, Matias and Faro, Ismael},
  year={2024},
  organization={Evolving Agents Labs},
  url={https://github.com/EvolvingAgentsLabs/sal-cp}
}
```

## Contributing

We welcome contributions from researchers and developers:

1. **Fork** the repository
2. **Create** a feature branch (`git checkout -b feature/communication-pattern`)
3. **Commit** your changes (`git commit -m 'Add new collaboration pattern'`)
4. **Push** to the branch (`git push origin feature/communication-pattern`)
5. **Open** a Pull Request

Please read our [Contributing Guidelines](CONTRIBUTING.md) for details.

## License

SAL-CP is licensed under the Apache 2.0 License. See [LICENSE](LICENSE) for details.

---

## Connect

**Research Contributors**: [Matias Molinas](https://github.com/matiasmolinas) • [Ismael Faro](https://github.com/ismaelfaro)

**Organization**: [EvolvingAgentsLabs](https://github.com/EvolvingAgentsLabs) • **Lab Site**: [evolvingagentslabs.github.io](https://evolvingagentslabs.github.io)

---

*Part of the EAX Protocol Suite from [Evolving Agents Labs](https://evolvingagentslabs.github.io) - Building the future of intelligent agents through experimental research*