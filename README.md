# 🌐 Kubernetes Monitoring & 3-Tier Application — Prometheus & Grafana on AKS
This project demonstrates how to build a **complete cloud-native monitoring solution** on **Azure Kubernetes Service (AKS)** using **Terraform**, **Helm**, **Prometheus**, and **Grafana** — including the deployment of a **3-tier application** (frontend, backend, database) to visualize real-time metrics and cluster performance.

---

## 🚀 Overview
This setup provides **end-to-end observability** into:
- Cluster health (nodes, pods, workloads)
- Application performance (CPU, memory, network)
- Dashboards and visual metrics through Grafana

---

## ⚙️ Stack Components
- **Terraform** — Provision Azure AKS cluster  
- **Helm** — Deploy Prometheus & Grafana  
- **Prometheus** — Scrape and collect Kubernetes metrics  
- **Grafana** — Visualize data in dashboards  
- **3-Tier App** — Node.js frontend, backend API, and PostgreSQL database  

---

## 🧩 Project Structure
```
k8s-monitoring-stack-prometheus-grafana/
│
├── infra/                     # Terraform + Helm + Monitoring stack
│   ├── aks.tf
│   ├── providers.tf
│   ├── variables.tf
│   ├── output.tf
│   └── terraform.tfvars
│
└── app/                       # 3-tier application
    ├── namespace.yml
    ├── db-secret.yml
    ├── db-deploy.yml
    ├── db-svc.yml
    ├── api-deploy.yml
    ├── api-svc-lb.yml
    ├── ui-configmap.yml
    ├── ui-deploy.yml
    └── ui-svc-lb.yml
```

---

## 📊 Deployment Steps

### 🏗️ 1. Provision AKS via Terraform
```bash
terraform init
terraform plan
terraform apply --auto-approve
```

### 📈 2. Deploy Prometheus & Grafana using Helm
```bash
kubectl create namespace monitoring
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo add grafana https://grafana.github.io/helm-charts
helm repo update
helm install prometheus prometheus-community/prometheus --namespace monitoring
helm install grafana grafana/grafana --namespace monitoring
```

### 🌐 3. Expose both monitoring tools
```bash
kubectl expose service prometheus-server --namespace monitoring --type=LoadBalancer --target-port=9090 --name=prometheus-server-ext
kubectl expose service grafana --namespace monitoring --type=LoadBalancer --target-port=3000 --name=grafana-ext
```

### 🔗 4. Connect Grafana to Prometheus
Go to **Connections → Add data source → Prometheus**

**URL:** `http://prometheus-server.monitoring.svc.cluster.local:80`

Click **Save & Test**

---

### 🧱 5. Deploy 3-Tier Application
```bash
kubectl apply -f app/
```

---

### 📈 6. Import Dashboards (Kubernetes Cluster template)
File: `k8s_cluster_monitoring.json`

View live metrics for pods, nodes, and workloads 🎯

---

## 📘 Example URLs
| Component      | URL |
|----------------|-----|
| Prometheus     | http://<prometheus-external-ip>:9090 |
| Grafana        | http://<grafana-external-ip> |
| Frontend App   | http://<frontend-external-ip> |
| Backend API    | http://<backend-external-ip> |

---

## 🧠 Key Learnings
✅ Infrastructure as Code using Terraform  
✅ Kubernetes Monitoring with Prometheus & Grafana  
✅ Application Deployment using YAML manifests  
✅ Observability & performance insights via Grafana  
✅ Integration of automation and monitoring in cloud-native environments  

---

## 💡 Future Enhancements
- Configure **AlertManager** for real-time alerts  
- Add **Custom Dashboards** for API metrics  
- Integrate with **Azure Monitor + Log Analytics**

---

## 👩‍💻 Author
**Teaf Almalki**
