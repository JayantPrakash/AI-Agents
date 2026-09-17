# Exploring AI Agents

This repository contains hands-on notebooks and supporting utilities for learning how AI agents are prompted, deployed, made resilient, and extended with planning and memory. The examples are inspired by *30 Agents Every AI Engineer Must Build* and are designed to run either with OpenAI or, where supported, in a deterministic simulation mode.

## What is included

| Area | Entry point | Topics | Status |
|---|---|---|---|
| Agent prompting | [`01-Agent-Prompting/agent_prompting.ipynb`](./01-Agent-Prompting/agent_prompting.ipynb) | Agent constitutions, system and user prompts, PTCF, decomposition, few-shot learning, Chain-of-Thought, Tree-of-Thoughts, and multi-agent communication | Ready |
| Deployment and responsible development | [`02-Agent-Deployment-Responsible-Development/agent_deployment.ipynb`](./02-Agent-Deployment-Responsible-Development/agent_deployment.ipynb) | Cost tracking, budget enforcement, circuit breaking, input validation, security, fairness, and graceful degradation | Ready |
| Autonomous decision-making | [`Agents/autonomous_decision_making_agent.ipynb`](./Agents/autonomous_decision_making_agent.ipynb) | Perception, strategy selection, safety checks, escalation, dependency-aware action execution, and learning | Ready |
| Planning agent | [`Agents/planning_agent.ipynb`](./Agents/planning_agent.ipynb) | Hierarchical task decomposition, dependency resolution, execution monitoring, feedback, and plan revision | Ready |
| Memory-augmented agent | [`Agents/memory_augmented_agent.ipynb`](./Agents/memory_augmented_agent.ipynb) | Working, episodic, and semantic memory; contextual retrieval; prompt enrichment; and a multi-turn healthcare example | Ready |

The runnable notebooks include defensive fallbacks so demonstrations can continue when a live model call fails. The deployment and cognitive-agent examples also include local mock implementations for repeatable, API-free experimentation.

## Quick start

The project targets Python 3.12.

1. Clone the repository and enter it.
2. Create and activate a virtual environment:

   ```bash
   python3.12 -m venv .venv
   source .venv/bin/activate
   ```

3. Install the dependencies:

   ```bash
   python -m pip install --upgrade pip
   python -m pip install -r requirements.txt
   ```

4. Start Jupyter:

   ```bash
   jupyter notebook
   ```

5. Begin with [`01-Agent-Prompting/agent_prompting.ipynb`](./01-Agent-Prompting/agent_prompting.ipynb), then work through the other ready notebooks in the order shown above.

## Live and simulation modes

To use live OpenAI calls, create a `.env` file in the repository root:

```text
OPENAI_API_KEY=your_api_key_here
```

Do not commit this file. API usage may incur charges from the configured provider.

If no key is available, notebooks with simulation support use `MockLLM` and mock data instead. The autonomous decision-making, planning, and memory-augmented notebooks also fall back to the shared mock client when a live OpenAI request fails.

## Project structure

```text
.
├── 01-Agent-Prompting/
│   ├── agent_prompting.ipynb
│   └── utils.py
├── 02-Agent-Deployment-Responsible-Development/
│   ├── agent_deployment.ipynb
│   ├── agent_utils.py
│   └── mock_llm.py
├── Agents/
│   ├── autonomous_decision_making_agent.ipynb # Autonomous decision-making agent
│   ├── planning_agent.ipynb                    # Planning agent
│   └── memory_augmented_agent.ipynb            # Memory-augmented agent
├── supporting/                  # Provider and environment-management helpers
├── color_logger.py              # Shared helper
├── mock_llm.py                  # Shared helper
├── resilience.py                # Shared helper
├── pyproject.toml
└── requirements.txt
```

### Agent notebooks

These three notebooks implement different types of agents:

- [`Agents/autonomous_decision_making_agent.ipynb`](./Agents/autonomous_decision_making_agent.ipynb) implements an autonomous decision-making agent.
- [`Agents/planning_agent.ipynb`](./Agents/planning_agent.ipynb) implements a planning agent.
- [`Agents/memory_augmented_agent.ipynb`](./Agents/memory_augmented_agent.ipynb) implements a memory-augmented agent.

### Shared helper modules

The three agent notebooks share these helper modules from the repository root:

- `color_logger.py` provides readable, color-coded notebook output.
- `mock_llm.py` supplies structured mock responses and an in-memory vector database.
- `resilience.py` provides `@fail_gracefully`, including retries, exponential backoff, and fallback values.

## Optional environment tooling

The [`supporting/`](./supporting/) directory contains Ubuntu setup, verification, chapter-environment switching, and provider-detection utilities intended for the broader book workflow. See [`supporting/ENVIRONMENT_WORKFLOW_GUIDE.md`](./supporting/ENVIRONMENT_WORKFLOW_GUIDE.md) before using those scripts; the root virtual-environment setup above is sufficient for the notebooks currently included in this repository.

## Credit

The learning path and examples in this repository are inspired by Imran Ahmad's book *30 Agents Every AI Engineer Must Build*.
