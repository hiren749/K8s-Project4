\# Kubernetes Project 4 — Production GPU Scheduling \& Observability



\## Final Architecture



AWS EKS Cluster

│

├── CPU Node Group

│   ├── t3.large

│   └── t3.large

│

└── GPU Node Group

&#x20;   └── g4dn.xlarge

&#x20;       └── NVIDIA Tesla T4

&#x20;           ├── NVIDIA Device Plugin

&#x20;           │   └── exposes nvidia.com/gpu

&#x20;           │

&#x20;           ├── GPU Feature Discovery

&#x20;           │   ├── gpu.product=Tesla-T4-SHARED

&#x20;           │   ├── gpu.family=turing

&#x20;           │   ├── gpu.memory=15360

&#x20;           │   └── gpu.sharing-strategy=time-slicing

&#x20;           │

&#x20;           └── DCGM Exporter

&#x20;               ↓

&#x20;            Prometheus

&#x20;               ↓

&#x20;             Grafana

&#x20;               ↓

&#x20;          Alertmanager



\## GPU Scheduling



The GPU node is isolated using:



\- GPU node labels

\- nodeSelector

\- taints and tolerations

\- NVIDIA extended resource requests

\- GPU Feature Discovery labels

\- logical GPU pool labels



Applications request GPUs using:



```yaml

resources:

&#x20; limits:

&#x20;   nvidia.com/gpu: 1

