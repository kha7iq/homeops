# 🏗️ HomeOps

This repository contains the infrastructure and Kubernetes cluster configuration for my homelab, managed using GitOps principles.  

The stack is powered by **[Talos](https://talos.dev)**, **[Kubernetes](https://kubernetes.io/)**, and **[Argo CD](https://argoproj.github.io/cd/)**, with automation assistance from **[Renovate](https://www.mend.io/renovate/)**. All of this is held together with a generous amount of **[YAML](https://yaml.org/)**—because why not?

---

## 📜 Overview  

This repository serves as the **Infrastructure as Code (IaC)** foundation for my homelab setup.  

Most workloads run on a **Talos-powered Kubernetes cluster**, while **storage services** are handled by a dedicated **[TrueNAS](https://www.truenas.com/)** VM.  

Configuration is structured using **Kustomized Helm**, with **[Argo CD](https://argoproj.github.io/cd/)** orchestrating application deployments.  

---

## 🛠️ Core Components  

Here’s a quick rundown of the key technologies in this setup:  

- **[Cilium](https://cilium.io/):** eBPF-based networking, observability, and security for Kubernetes.  
- **[Argo CD](https://argo-cd.readthedocs.io/en/stable/):** GitOps-driven continuous deployment for Kubernetes workloads.  
- **[Cert-manager](https://cert-manager.io/):** Automated certificate management for TLS security.  
- **[Authentik](https://goauthentik.io/):** Open-source identity and access management (IAM).  
- **[Gateway API](https://gateway-api.sigs.k8s.io/):** The next-gen Kubernetes Ingress for advanced traffic routing.  
- **[Technitium](https://github.com/TechnitiumSoftware/DnsServer):** DNS Server & ad-blocker.  
- **[Netbird](https://netbird.io/):** Secure, self-hosted VPN alternative with a mesh networking approach.  

---

## 🗃️ Folder Structure

```shell

services
├── 📂 database
│   ├── cnpg-operator
│   └── pg-cluster
├── 📂 network
│   ├── cert-manager
│   ├── cloudflared
│   ├── external-dns
│   ├── gateway
│   ├── netbird
│   └── speedtest
├── 📂 observability
│   ├── grafana
│   ├── kube-state-metrics
│   ├── loki
│   ├── metrics-server
│   ├── prometheus-stack
│   ├── promtail
│   └── smartctl-exporter
├── 📂 security
│   └── authentik
├── 📂 storage
│   ├── longhorn
│   └── nfs-external-provisioner
├── 📂 tools
│   ├── gitlab-runner
│   ├── n8n
│   ├── paperless
│   ├── spegal
│   ├── talos-backup
│   └── whoami
└── 📂 web
    └── lmno

```

