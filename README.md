# Exploring AI Agents

This repository documents my hands-on exploration of AI agents through practical notebooks and small experiments. The code starts with [`agent_prompting.ipynb`](./agent_prompting.ipynb), which explores how prompts define an agent's identity, constraints, reasoning approach, and output format.

## Start here

The `agent_prompting.ipynb` notebook covers topics including:

- system prompts and user prompts;
- prompts as persistent agent constitutions;
- the Persona, Task, Context, and Format (PTCF) framework;
- task decomposition and structured reasoning;
- Chain-of-Thought (CoT) prompting for working through a problem as a sequential reasoning process;
- Tree-of-Thoughts (ToT) prompting for exploring multiple reasoning branches and synthesizing their results;
- a Multi-Agent Communication Protocol for structured collaboration between specialized agents;
- production-oriented case studies covering SaaS support triage, financial compliance, and automated code review; and
- defensive handling of LLM calls.

## Setup

1. Clone the repository and enter the project directory.
2. Create and activate a Python virtual environment.
3. Install the dependencies:

   ```bash
   pip install -r requirements.txt
   ```

4. Add your OpenAI API key to a `.env` file:

   ```text
   OPENAI_API_KEY=your_api_key_here
   ```

5. Start Jupyter and open the first notebook:

   ```bash
   jupyter notebook agent_prompting.ipynb
   ```

API usage may incur charges from the configured model provider. Keep `.env` files and API keys out of version control.

## Project structure

```text
.
├── agent_prompting.ipynb  # Prompting, CoT/ToT, multi-agent protocol, and use cases
├── utils.py               # Logging, API-key loading, and fallback helpers
└── requirements.txt       # Python dependencies
```

## Credit

The learning path and examples in this repository are inspired by the book *30 Agents Every AI Engineer Must Build*.
