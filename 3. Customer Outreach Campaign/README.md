# 🚀 Sales Lead Generation & Outreach Automation using CrewAI

This repository leverages **CrewAI** to automate the **sales lead profiling and outreach process**. By defining specialized agents for **lead identification** and **personalized communication**, this workflow ensures that **high-value leads are nurtured effectively**, increasing conversion rates and driving business growth.

---

## 🌟 Features

- **Multi-Agent Sales Process**: Uses different agents for lead research and outreach.  
- **CrewAI Framework**: Implements `CrewAI` to manage agents and optimize workflow execution.  
- **Automated Lead Profiling**: Analyzes company data, decision-makers, and recent milestones.  
- **Personalized Outreach**: Crafts compelling messages tailored to each lead.  
- **Data-Driven Strategy**: Uses advanced tools to ensure accuracy and effectiveness.  

---

## 🏗️ How It Works

### 1️⃣ **Define Agents**
CrewAI requires defining agents with specific **roles, goals, and backstories**:

- **Sales Representative** 📊  
  - **Role**: `Sales Representative`  
  - **Goal**: Identify high-value leads matching the ideal customer profile.  
  - **Backstory**: Works at **Arcadia**, leveraging strategic insights and data analysis to uncover **hidden opportunities**.  

- **Lead Sales Representative** ✉️  
  - **Role**: `Lead Sales Representative`  
  - **Goal**: Nurture leads through **engaging, personalized communication**.  
  - **Backstory**: Acts as the **bridge between potential clients and Arcadia’s solutions**, ensuring leads feel understood and valued.  

---

### 2️⃣ **Define Tasks**
Each agent is assigned a **specific task** to ensure a structured workflow:

- **Lead Profiling Task**  
  - **Description**: Conduct a deep analysis of `{lead_name}` (industry: `{industry}`), compiling a detailed report on key decision-makers, company milestones, and pain points.  
  - **Expected Output**: A **comprehensive lead profile** highlighting potential needs and engagement strategies.  
  - **Assigned Agent**: **Sales Representative**  
  - **Tools**: `directory_read_tool`, `file_read_tool`, `search_tool` (for gathering relevant information).  

- **Personalized Outreach Task**  
  - **Description**: Using insights from the lead profiling report, create a **tailored outreach campaign** for `{key_decision_maker}`, `{position}` at `{lead_name}`. The campaign should highlight their `{milestone}` and how our solutions align with their business goals.  
  - **Expected Output**: A **series of compelling email drafts** addressing `{lead_name}`'s needs with a professional yet engaging tone.  
  - **Assigned Agent**: **Lead Sales Representative**  
  - **Tools**: `sentiment_analysis_tool`, `search_tool` (to refine messaging and align with the company’s communication style).  

---

### 3️⃣ **Assemble the Crew**
The agents are combined into a **Crew**, ensuring a seamless sales automation process:

```python
crew = Crew(
  agents=[sales_rep_agent, lead_sales_rep_agent],
  tasks=[lead_profiling_task, personalized_outreach_task],
  verbose=True,
  memory=True
)
```

### 4️⃣ **Run the workflow**
The process is initiated by passing lead information as input. For example:

```python
inputs = {
    "lead_name": "CrewAI",
    "industry": "AI Agent Framework",
    "key_decision_maker": "João (Joe) Moura",
    "position": "Founder",
    "milestone": "product launch"
}
result = crew.kickoff(inputs=inputs)
```