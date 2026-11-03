# AI-Assisted End-to-End Home SOC & Log Triage Lab

![Wazuh](https://img.shields.io/badge/Wazuh-Endpoint%20Security-blue?style=for-the-badge&logo=wazuh)
![Grafana](https://img.shields.io/badge/Grafana-Visualization-orange?style=for-the-badge&logo=grafana)
![NetAlertX](https://img.shields.io/badge/NetAlertX-Network%20Monitoring-green?style=for-the-badge)
![Docker](https://img.shields.io/badge/Docker-Containerization-2496ED?style=for-the-badge&logo=docker)
![AI-Powered](https://img.shields.io/badge/AI-Log%20Triage-purple?style=for-the-badge)

A fully functional, end-to-end **Home Security Operations Center (SOC)** lab designed to monitor endpoint activity, track network devices, visualize security telemetry, and leverage **AI-driven log analysis** for automated threat triage. 

## Architecture & Component Overview

This lab is built using a centralized virtualized environment running on an Ubuntu host, integrating open-source security tools to replicate enterprise-grade SOC workflows on a home network.

### Core Components:
1. **Host & Virtualization:** Ubuntu Virtual Machine configured with a bridged network setup to bridge physical and virtualized traffic seamlessly.
2. **Endpoint Detection & Response (EDR):** **Wazuh** (Manager & Agent) deployed for File Integrity Monitoring (FIM), registry modification tracking, and security policy enforcement.
3. **Network Visibility:** **NetAlertX** deployed via Docker to discover, track, and alert on all active devices connected to the home network.
4. **Centralized Dashboards:** **Grafana** acting as the single pane of glass, ingesting logs from OpenSearch (Wazuh backend) and NetAlertX (via the Infinity plugin).
5. **AI-Assisted Threat Triage:** **AIRIA AI** integration using an Ubuntu-based AI forwarder to pass system alerts to an LLM for automated summarization, contextual analysis, and push notifications back to Grafana.

---

## 📸 Lab Walkthrough & Dashboards

### 1. Host & Virtualization Setup
The central management node running on an Ubuntu desktop environment with virtualized resource allocation and bridged networking.
![Ubuntu Desktop Environment](assets/Ubuntu.png)

### 2. Endpoint Monitoring & File Integrity Monitoring (Wazuh)
Tracking suspicious file modifications, registry updates, and system alerts (`syscheck`) across monitored endpoints.
![Wazuh FIM Dashboard](assets/Wazuh.png)

### 3. Network Device Discovery (NetAlertX)
Real-time network visibility tracking connected devices, new additions, ARP scans, and active IP allocations.
![NetAlertX Network Overview](assets/NetAlertX.png)

### 4. Unified Security Dashboard (Grafana)
Configuring data sources (`OpenSearch`, `Wazuh-AIRIA-forwarder`, and `Infinity`) to centralize SOC metrics and AI-generated threat insights.
![Grafana Data Sources and Dashboards](assets/Grafana.png)

---

## ⚙️ Quick Setup Guide

### Step 1: Environment Preparation
* Set up a host machine or server (e.g., Zima Cube or a spare laptop with 8–16GB RAM).
* Spin up an **Ubuntu Virtual Machine** and configure network adapters to **Bridged Mode** to allow communication with local endpoints.

### Step 2: Deploying Endpoint Monitoring (Wazuh)
1. Install the Wazuh server/manager stack on your central host.
2. Install the Wazuh agent on target machines (e.g., Windows laptop/VM).
3. Configure `ossec.conf` to enable File Integrity Monitoring (FIM) on sensitive directories.

### Step 3: Deploying Network Monitoring (NetAlertX)
Deploy NetAlertX via Docker to continuously monitor local subnet device presence.

### Step 4: Configuring Grafana & Data Sources
1. Install Grafana and log in to the web interface.
2. Add **OpenSearch** as a data source pointing to your Wazuh backend logs.
3. Install the **Infinity Plugin** in Grafana to ingest JSON/API endpoints from NetAlertX and your AI forwarder.

### Step 5: Setting Up AI Triage (AIRIA AI)
* Deploy the AIRIA AI forwarder script on the Ubuntu VM to capture incoming Wazuh alerts.
* Forward structured alert payloads to the LLM API endpoint for automated risk scoring and plain-English incident summaries.

---

## Skills & Competencies Demonstrated
* **Security Information & Event Management (SIEM):** Log pipelines, ingestion sources, and dashboard visualization.
* **Endpoint Security:** FIM rules and host-based telemetry analysis.
* **Network Monitoring:** Containerized tools for asset discovery and network topology mapping.
* **AI Integration in SecOps:** Automated log triage and summarization workflows to accelerate incident response times.
