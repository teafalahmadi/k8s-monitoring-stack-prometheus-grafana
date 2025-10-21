# Kubernetes Monitoring Stack — Prometheus & Grafana

This project demonstrates how to set up a full monitoring solution inside a Kubernetes cluster using **Prometheus** and **Grafana**.  
It was implemented as part of the **DevOps Bootcamp (Ironhack × Saudi Digital Academy)**.

## 🚀 Overview
The setup provides real-time visibility into:
- Cluster health (nodes, pods, workloads)
- Application performance (CPU, memory, network)
- Metrics visualization with Grafana dashboards

## 🧩 Stack Components
- **Terraform** — provisions the AKS cluster on Azure  
- **Helm** — installs Prometheus and Grafana  
- **Prometheus** — collects and scrapes metrics  
- **Grafana** — visualizes metrics and dashboards  
- **Three-tier Application** — frontend, backend, and Postgres DB deployed in AKS  

## ⚙️ Setup Summary
1. Provision AKS using Terraform  
2. Deploy Prometheus & Grafana via Helm  
3. Expose Prometheus (LoadBalancer) and configure Grafana datasource  
4. Import dashboard template (`k8s_cluster_monitoring.json`)  
5. Deploy a 3-tier sample app and observe live metrics  

## 🌐 Access Points (example)
| Component   | Type | Example URL |
|--------------|------|-------------|
| Prometheus   | Monitoring | `http://<prometheus-external-ip>:9090` |
| Grafana      | Dashboard  | `http://<grafana-external-ip>` |
| Frontend App | User Interface | `http://<frontend-external-ip>` |

## 🧠 Learning Outcomes
- Set up Prometheus & Grafana inside AKS  
- Visualize cluster & app metrics  
- Automate deployments using Terraform & Helm  
- Understand observability in Kubernetes  

---

⭐ **Author:** [@teafalahmadi](https://github.com/teafalahmadi)  

