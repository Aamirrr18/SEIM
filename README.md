# NextGen SIEM & AI-Driven Threat Intelligence Pipeline
**Academic Capstone Project**

## 📌 Executive Summary
This project demonstrates a custom-built Security Information and Event Management (SIEM) pipeline. It was engineered to ingest simulated authentication logs, utilize an Isolation Forest machine learning algorithm to detect behavioral anomalies, and automate firewall responses using a simulated SOAR (Security Orchestration, Automation, and Response) workflow. 

The final output is a single-pane-of-glass Command Center built in Kibana, providing SOC analysts with real-time operational intelligence.

## 🛠️ Technologies Used
* **Languages:** Python (Pandas, Scikit-Learn, Requests)
* **Infrastructure:** Docker, Docker Compose
* **SIEM Stack:** Elasticsearch, Kibana
* **Threat Intelligence:** AbuseIPDB API

---

## 🏗️ Phase 1: Infrastructure & Data Ingestion
The ELK stack (Elasticsearch & Kibana) was containerized and deployed locally via Docker. A Python ingestion script was developed to securely pass raw JSON authentication logs (simulating SSH brute-force attempts) directly into the Elasticsearch backend.

> <img width="1920" height="1080" alt="Screenshot (44)" src="https://github.com/user-attachments/assets/ef447d93-b59b-4663-a0f7-3744034abbe7" />

> <img width="1920" height="1080" alt="Screenshot (46)" src="https://github.com/user-attachments/assets/320265e5-bb52-413e-aaf2-b7dfe45f500f" />


---

## 🧠 Phase 2: Machine Learning Detection Engine
To move beyond static rules, an anomaly detection engine was engineered using Python. 
1. **Baselining:** The script generates normal network traffic patterns in memory.
2. **Analysis:** The `Isolation Forest` algorithm evaluates the Elasticsearch data against the normal baseline.
3. **Verdict:** The mathematical model successfully flags the persistent Russian IP (`45.33.32.156`) as a `-1` (Severe Anomaly).

> <img width="1920" height="1080" alt="Screenshot (45)" src="https://github.com/user-attachments/assets/0ca41b5b-b91b-408c-a0bb-6a1d37d48a90" />


---

## ⚡ Phase 3: Automated SOAR Response
Once the machine learning model flagged the anomaly, the pipeline queried the AbuseIPDB API to verify the threat score. Upon verification of a malicious reputation, the Python script dynamically generated a local firewall `.txt` blocklist, effectively "killing" the connection without manual human intervention.

---

## 📊 Phase 4: Executive SOC Visualization
Raw JSON logs were parsed and mapped inside Kibana using the visual builder (Lens) to create an interactive, NextGen Command Center. The dashboard features:
* **Metric Cards:** Tracking total ingested attack volume.
* **Donut Charts:** Visualizing geographic and IP-based threat origins.
* **Data Ledgers:** Providing a raw, timestamped ledger of targeted usernames and attack outcomes for SOC analysts.

> <img width="1920" height="1080" alt="Screenshot (47)" src="https://github.com/user-attachments/assets/1a332a2c-667a-4bbb-ab72-34debf12e3d7" />


---
*This lab was completed as a comprehensive academic capstone to bridge the gap between infrastructure deployment, AI-driven behavioral detection, and automated threat mitigation.*
