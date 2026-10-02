\# Kubernetes Project 4 — Production GPU Scheduling \& Observability on AWS EKS



This project builds a production-style GPU Kubernetes environment on AWS EKS using a real NVIDIA Tesla T4 GPU.



\## What This Project Demonstrates



\- Real GPU scheduling with `nvidia.com/gpu`

\- NVIDIA Device Plugin

\- GPU node isolation using taints and tolerations

\- GPU-specific scheduling using node labels

\- GPU Feature Discovery

\- Tesla T4-specific scheduling

\- GPU time-slicing

\- 1 physical GPU exposed as 4 logical GPU resources

\- Shared GPU pool abstraction

\- NVIDIA DCGM Exporter

\- Prometheus GPU monitoring

\- Grafana GPU dashboards

\- GPU temperature, power, memory, and utilization monitoring

\- Prometheus GPU alert rules

\- Alertmanager routing and webhook delivery

\- MIG, MPS, and NVIDIA GPU Operator concepts



\## Infrastructure



```text

AWS EKS

│

├── 2 × t3.large CPU workers

│

└── 1 × g4dn.xlarge GPU worker

&#x20;     └── NVIDIA Tesla T4

