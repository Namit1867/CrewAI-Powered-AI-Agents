# 🎉 Event Management Automation with CrewAI  

This repository leverages **CrewAI** to automate the **event planning and execution process**. By defining specialized agents for **venue coordination, logistics management, and marketing**, this workflow ensures that every event is executed seamlessly, increasing efficiency and participant engagement.  

---

## 🌟 Features  

- **Multi-Agent Event Management**: Uses different agents for venue booking, logistics coordination, and event promotion.  
- **CrewAI Framework**: Implements `CrewAI` to manage agents and optimize workflow execution.  
- **Automated Venue Selection**: Identifies and secures the best venue based on event requirements.  
- **Seamless Logistics Management**: Handles catering and equipment coordination efficiently.  
- **Effective Event Marketing**: Drives participant engagement with strategic communication.  

---

## 🏗️ How It Works  

### 1️⃣ **Define Agents**  

CrewAI requires defining agents with specific **roles, goals, and backstories**:  

- **Venue Coordinator** 🏛️  
  - **Role**: `Venue Coordinator`  
  - **Goal**: Identify and book an appropriate venue based on event requirements.  
  - **Backstory**: With a keen sense of space and understanding of event logistics, this agent ensures the selected venue aligns with the event’s theme, size, and budget constraints.  
  - **Tools**: `search_tool`, `scrape_tool` (for gathering venue information).  

- **Logistics Manager** 📦  
  - **Role**: `Logistics Manager`  
  - **Goal**: Manage all logistics, including catering and equipment, to ensure smooth event execution.  
  - **Backstory**: Detail-oriented and highly organized, this agent ensures all logistical aspects, from catering to equipment setup, are handled flawlessly.  
  - **Tools**: `search_tool`, `scrape_tool` (for vendor research and coordination).  

- **Marketing & Communications Agent** 📢  
  - **Role**: `Marketing and Communications Agent`  
  - **Goal**: Effectively market the event and communicate with participants to maximize attendance.  
  - **Backstory**: Creative and communicative, this agent crafts compelling messages and engages with potential attendees to boost event exposure and participation.  
  - **Tools**: `search_tool`, `scrape_tool` (for audience targeting and engagement tracking).  

---

### 2️⃣ **Define Tasks**  

Each agent is assigned a **specific task** to ensure a structured workflow:  

- **Venue Selection Task**  
  - **Description**: Find a venue in `{event_city}` that meets the criteria for `{event_topic}`.  
  - **Expected Output**: A detailed report on a specifically chosen venue that fits the event's needs.  
  - **Output Format**: JSON file (`venue_details.json`) with structured venue details.  
  - **Assigned Agent**: **Venue Coordinator**  

- **Logistics Management Task**  
  - **Description**: Coordinate catering and equipment for an event with `{expected_participants}` participants on `{tentative_date}`.  
  - **Expected Output**: Confirmation of all logistics arrangements, including catering and equipment setup.  
  - **Execution Mode**: **Asynchronous execution** to allow real-time coordination.  
  - **Assigned Agent**: **Logistics Manager**  

- **Event Marketing Task**  
  - **Description**: Promote the `{event_topic}` event, aiming to engage at least `{expected_participants}` potential attendees.  
  - **Expected Output**: A marketing report summarizing activities and attendee engagement.  
  - **Output Format**: Markdown file (`marketing_report.md`).  
  - **Assigned Agent**: **Marketing & Communications Agent**  

---

### 3️⃣ **Assemble the Crew**  

The agents are combined into a **Crew**, ensuring a seamless event planning and execution process:  

```python
event_management_crew = Crew(
    agents=[venue_coordinator, 
            logistics_manager, 
            marketing_communications_agent],
    
    tasks=[venue_task, 
           logistics_task, 
           marketing_task],
    
    verbose=True
)
