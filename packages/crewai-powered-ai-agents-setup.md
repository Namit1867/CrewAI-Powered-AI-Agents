# CrewAI-Powered-AI-Agents — Setup & Usage

> Source: [github.com/Namit1867/CrewAI-Powered-AI-Agents](https://github.com/Namit1867/CrewAI-Powered-AI-Agents)

This guide covers getting the CrewAI example crews running locally. Each numbered
folder is a standalone Jupyter Notebook, so you set up the environment once and
then open whichever project you want to explore.

## Prerequisites

- **Python 3.10+**
- **pip** and (recommended) a virtual environment tool (`venv` or `conda`)
- **Jupyter** (Notebook or Lab) to run the `.ipynb` files
- **API keys** for the LLM and any tools a given project uses (see below)

## 1. Clone the repository

```bash
git clone https://github.com/Namit1867/CrewAI-Powered-AI-Agents.git
cd CrewAI-Powered-AI-Agents
```

> The default branch is `dev`.

## 2. Create and activate a virtual environment

```bash
python -m venv .venv
source .venv/bin/activate      # macOS / Linux
# .venv\Scripts\activate       # Windows (PowerShell)
```

## 3. Install dependencies

The repo ships a `requirements.txt`:

```text
crewai
crewai_tools
langchain_community
```

Install it, plus Jupyter:

```bash
pip install -r requirements.txt
pip install jupyter
```

## 4. Configure API keys

CrewAI agents call an LLM (commonly OpenAI) and several projects call external
tools. Set the relevant environment variables before launching Jupyter, e.g.:

```bash
export OPENAI_API_KEY="sk-..."          # LLM
export SERPER_API_KEY="..."             # web search (crewai_tools)
# Project 8 (Trello) additionally needs:
export TRELLO_API_KEY="..."
export TRELLO_API_TOKEN="..."
```

> Check the first cells of each notebook — they document exactly which keys and
> tools that specific crew expects. Never commit keys; keep them in your shell
> environment or a local `.env` (already covered by `.gitignore`).

## 5. Run a project

```bash
jupyter lab        # or: jupyter notebook
```

Open the folder for the project you want (e.g. `1. Research and Write an article/`),
open its notebook, and run the cells top to bottom.

## How a crew is structured

Each notebook follows the same CrewAI pattern:

1. **Define agents** — role, goal, backstory, tools, and LLM.
2. **Define tasks** — description + expected output, assigned to an agent.
3. **Assemble the crew** — group the agents and tasks and choose a process
   (sequential or hierarchical).
4. **Kick off** — call `crew.kickoff(inputs={...})` with the run-time inputs and
   read back the result.

```python
from crewai import Agent, Task, Crew

researcher = Agent(role="Researcher", goal="...", backstory="...")
task = Task(description="...", expected_output="...", agent=researcher)
crew = Crew(agents=[researcher], tasks=[task])
result = crew.kickoff(inputs={"topic": "AI agents"})
print(result)
```

## Troubleshooting

- **Authentication errors** — confirm the required API key env vars are set in the
  same shell that launched Jupyter.
- **Missing tool errors** — some projects need extra packages beyond
  `requirements.txt`; install whatever the notebook's first cell imports.
- **Rate limits / cost** — these crews make multiple LLM calls per run; start with
  small inputs while iterating.

See [crewai-powered-ai-agents-overview.md](crewai-powered-ai-agents-overview.md)
for the full project catalog and core concepts.
