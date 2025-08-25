# Natural Language to BigQuery via Slack based on Vertex AI Agent Engine 

## 📌 Overview  
This project enables users to query and visualize data from **Google BigQuery** using **natural language questions** directly within **Slack**.  

The workflow leverages **Google Cloud Run**, **Google Vertex AI Agent Engine**, and a custom **Slack App**, creating an AI-driven interface for seamless interaction with data.  

---

## 🏗️ Architecture  
<img width="4320" height="1596" alt="structure1" src="https://github.com/user-attachments/assets/594936fd-1213-44b1-b3d5-7389ddeec3fa" />



### Components  
- **User (Slack)**  
  - Users ask questions in plain English through Slack.  
  - Answers(data, analysis summary, and visualized chart) are returned directly in the Slack channel.    

- **Slack Calling AI Agents Layer (App)**  
  - Slack app that routes user queries to the backend.  

- **Google Cloud Run**  
  - Acts as the middleware service.  
  - Receives user questions from Slack.  
  - Sends queries to Vertex AI for processing.  
  - Returns responses back to Slack.  

- **AI Agents Layer (Vertex AI)**  
  - Uses **Google Vertex AI** LLMs to interpret natural language.  
  - Converts user queries into **SQL queries**.  
  - Executes queries against BigQuery.  

- **Data Layer (BigQuery)**  
  - Stores the datasets.  
  - Executes the AI-generated SQL queries.  
  - Sends query results back to Vertex AI.  

---

## 🔄 Workflow  
1. **User asks a question** in Slack (e.g., *“What were the total sales last month?”*).  
2. **Slack App** forwards the question to **Google Cloud Run**.  
3. **Cloud Run** passes the request to **Vertex AI**.  
4. **Vertex AI** interprets the question → generates a **BigQuery SQL query**.  
5. The query is executed on **BigQuery**.  
6. **Results are sent back** through Vertex AI → Cloud Run → Slack.  
7. The **user receives the answer** in Slack.  

---

## 🚀 Technologies Used  
- [Slack API](https://api.slack.com/)  
- [Google Cloud Run](https://cloud.google.com/run)  
- [Google Vertex AI](https://cloud.google.com/vertex-ai)  
- [Google BigQuery](https://cloud.google.com/bigquery)  

---

## 📂 Project Structure  
```bash
├── README.md          # Project documentation  
├── slack_app/         # Slack bot integration code  
├── google_cloud_run_service/slack_calling_AI_agents_app # Cloud Run middleware code  
├── google_vertex_ai/agent_engine   # Vertex AI query processing logic  
├── bigquery/          # Example SQL queries / schema  
└── docs/              # Architecture diagrams & docs  
```

---

## ✅ Features  
- Query BigQuery using **natural language**.  
- Get **instant answers** inside Slack.  
- Scalable & serverless using **Cloud Run**.  
- Powered by **Vertex AI** for query translation.  

---

## 🔮 Future Enhancements  
- Add **role-based access control** for sensitive queries.  
- Support for **multi-turn conversations** in Slack.  
- Integration with other data warehouses beyond BigQuery.  

---

## 📖 How to Use Step by Step (High-Level)  
Step 1: **Build data warehouse**
(1) Setup your Google Cloud Account, build a data lake(Google Cloud Storage) and a data warehouse(Google Bigquery). Suppose this step is all completed.

Step 2: **Build data science AI agent**   
(1) Build a data science agent using **Agent Development Kit (ADK)**. And then deploy the agent to **Google Vertex AI** as an Agent Engine.

Step 3: **Build Slack APP and Slack Calling AI Agents App** 
(1) Create a Slack app and configure it with your workspace.
(2) Build a **Slack Calling AI Agents App**. And then deploy the APP to **Cloud Run Service** with proper IAM permissions. 

Step 4: **Query data and plot chart in Slack** 
(1) Start asking questions in Slack! 🎉  
