Kubernetes GitOps Platform (EKS + ArgoCD + Monitoring)
🚀 Project Overview

This project demonstrates a production-style Kubernetes GitOps platform built on AWS EKS. It includes automated deployments using ArgoCD, multiple microservices, autoscaling, and full monitoring with Prometheus and Grafana.

🏗️ Architecture
AWS EKS Cluster
Terraform (Infrastructure provisioning)
ArgoCD (GitOps continuous deployment)
Helm Charts (Microservices deployment)
Prometheus (Metrics collection)
Grafana (Visualization dashboards)
HPA (Horizontal Pod Autoscaler)
📦 Components
🔹 Microservices
service1 → NGINX app
service2 → Node.js app
service3 → Python Flask app
🔹 GitOps (ArgoCD)
Automatically syncs Kubernetes manifests from GitHub
Ensures desired state is always maintained
Self-healing deployments enabled
🔹 Monitoring Stack

Installed using Helm:

helm install monitoring prometheus-community/kube-prometheus-stack -n monitoring

Includes:

Prometheus
Grafana
Alertmanager
Node Exporter
kube-state-metrics
🔹 Autoscaling (HPA)

CPU-based autoscaling enabled:

kubectl autoscale deployment service1 -n staging --cpu-percent=50 --min=1 --max=5
kubectl autoscale deployment service2 -n staging --cpu-percent=50 --min=1 --max=5
kubectl autoscale deployment service3 -n staging --cpu-percent=50 --min=1 --max=5
📊 Access Services
Services (LoadBalancer)
service1 → http://<ELB-URL>
service2 → http://<ELB-URL>
service3 → http://<ELB-URL>
Grafana
http://<grafana-elb-url>

Default login:

Username: admin
Password:
kubectl get secret -n monitoring monitoring-grafana \
-o jsonpath="{.data.admin-password}" | base64 --decode
Prometheus
kubectl port-forward -n monitoring svc/monitoring-kube-prometheus-prometheus 9090:9090

Open:

http://localhost:9090
📈 Features Implemented

✔ EKS Cluster via Terraform
✔ GitOps CI/CD using ArgoCD
✔ Helm-based deployments
✔ 3 Microservices deployed
✔ LoadBalancer services
✔ Horizontal Pod Autoscaler (HPA)
✔ Prometheus monitoring
✔ Grafana dashboards
✔ Alertmanager setup

🚀 Deployment Flow
GitHub Repo
   ↓
ArgoCD Sync
   ↓
Kubernetes Cluster (EKS)
   ↓
Pods + Services + HPA
   ↓
Prometheus Metrics
   ↓
Grafana Dashboards
📂 Project Structure
k8s-gitops-config/
│
├── helm-charts/
│   ├── service1/
│   ├── service2/
│   └── service3/
│
├── argocd-apps/
├── monitoring/
├── terraform/
└── README.md
