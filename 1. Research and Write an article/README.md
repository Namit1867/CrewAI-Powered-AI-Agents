# Research and Write an Article using CrewAI

This Jupyter Notebook leverages **CrewAI** to automate the research, writing, and editing process for generating well-structured articles on a given topic. The notebook defines specialized agents for **planning**, **writing**, and **editing** articles by utilizing **LLMs (Large Language Models)**.

---

## 🚀 Features
- **Multi-Agent Collaboration**: Uses different agents for content planning, writing, and editing.
- **CrewAI Framework**: Leverages `crewai` for organizing and managing agents and tasks.
- **Automated Workflow**: The agents work together to generate high-quality content from scratch.
- **Customization**: Allows modification of agents’ roles, goals, and workflows based on specific needs.


## 🏗️ How It Works

### 1️⃣ **Define Agents**
CrewAI requires defining agents with specific **roles, goals, and backstories**:

- **Planner**: Researches and outlines the content.
- **Writer**: Writes a factually accurate and insightful article based on the research.
- **Editor**: Reviews and refines the content for clarity and correctness.

### 2️⃣ **Define Tasks**
Each agent is assigned a task:

- **Plan Task**: Collects and structures relevant information.
- **Write Task**: Uses the planned outline to generate the main content.
- **Edit Task**: Proofreads and refines the article.

### 3️⃣ **Assemble the Crew**
The agents are combined into a **Crew**, which sequentially completes the tasks, ensuring a structured workflow.

### 4️⃣ **Run the Pipeline**
Once the Crew is set up, the process runs automatically, generating a polished article.

