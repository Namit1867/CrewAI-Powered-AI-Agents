# 🤖 Customer Support Automation using CrewAI

This repository leverages **CrewAI** to automate the **customer support and quality assurance process** for handling inquiries efficiently. By defining specialized agents for **support resolution** and **quality assurance**, this workflow ensures that customers receive **friendly, accurate, and well-documented** responses.

---

## 🚀 Features

- **Multi-Agent Collaboration**: Uses distinct agents for handling customer inquiries and reviewing responses.  
- **CrewAI Framework**: Implements `CrewAI` to manage agents and streamline task execution.  
- **Automated Inquiry Resolution**: Ensures that customer questions are answered **comprehensively and accurately**.  
- **Quality Assurance Review**: Verifies the correctness and completeness of responses before sending them.  
- **Customizable Workflow**: Modify agent roles, goals, and responsibilities based on business needs.  

---

## 🏗️ How It Works

### 1️⃣ **Define Agents**
CrewAI requires defining agents with specific **roles, goals, and backstories**:

- **Support Agent** 👨‍💻  
  - **Role**: `Senior Support Representative`  
  - **Goal**: Be the most **helpful and friendly** support representative.  
  - **Backstory**: Works at **Arcadia (https://www.arcadiax.ai/)**, assisting high-priority customers like **DeepLearningAI** with their inquiries.  

- **Quality Assurance Agent** 🕵️  
  - **Role**: `Support Quality Assurance Specialist`  
  - **Goal**: Ensure that all responses meet the **highest quality standards**.  
  - **Backstory**: Works alongside the support agent to **review and refine** responses before they reach the customer.  

---

### 2️⃣ **Define Tasks**
Each agent is assigned a **specific task** to complete the workflow:

- **Inquiry Resolution Task**  
  - **Description**: Respond to customer inquiries in a **detailed and friendly** manner.  
  - **Expected Output**: A **complete and well-researched** response, referencing all sources used.  
  - **Assigned Agent**: **Support Agent**  
  - **Tools**: `ScrapeWebsiteTool` (for retrieving relevant information).  

- **Quality Assurance Review Task**  
  - **Description**: Review the support agent’s response to ensure it is **comprehensive and accurate**.  
  - **Expected Output**: A **polished** and **customer-ready** response, incorporating any necessary improvements.  
  - **Assigned Agent**: **Quality Assurance Agent**  

---

### 3️⃣ **Assemble the Crew**
The agents are combined into a **Crew**, ensuring a smooth workflow:

```python
crew = Crew(
  agents=[support_agent, support_quality_assurance_agent],
  tasks=[inquiry_resolution, quality_assurance_review],
  verbose=True,
  memory=True
)
```

### 4️⃣ **Run the workflow**
The process is initiated by passing customer inquiries as input. For example:

```python
inputs = {
    "customer": "DeepLearningAI",
    "person": "Andrew Ng",
    "inquiry": "I need help with setting up an account on Arcadia\n"
               "and kicking it off. Specifically, "
               "Do I need an invitation to sign up for Arcadia? \n"
               "Can you provide guidance?"
}
result = crew.kickoff(inputs=inputs)
```