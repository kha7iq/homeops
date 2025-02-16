# 🏗️ HomeOps

This repository contains the infrastructure and Kubernetes cluster configuration for my homelab, managed using GitOps principles.  

The stack is powered by **[Talos](https://talos.dev)**, **[Kubernetes](https://kubernetes.io/)**, and **[Argo CD](https://argoproj.github.io/cd/)**, 
with automation assistance from **[Renovate](https://www.mend.io/renovate/)**. 

Most workloads run on a **Talos-powered Kubernetes cluster**, while **storage services** are handled by a dedicated
**[OpenMediaVault](https://www.openmediavault.org/) Server & [Longhorn](https://github.com/longhorn/longhorn)**.  
To securely manage secrets, it uses **[External Secrets Operator](https://external-secrets.io/)**  
integrated with **[Bitwarden](https://bitwarden.com/)** as the secret backend.

Configuration is structured using **Kustomized Helm**, with **[Argo CD](https://argoproj.github.io/cd/)** orchestrating application deployments.  

---

## 🛠️ Core Components  

Here’s a quick rundown of the key technologies in this setup:  

- **[Cilium](https://cilium.io/):** eBPF-based networking, observability, and security for Kubernetes.  
- **[Argo CD](https://argo-cd.readthedocs.io/en/stable/):** GitOps-driven continuous deployment for Kubernetes workloads.  
- **[Cert-manager](https://cert-manager.io/):** Automated certificate management for TLS security.  
- **[External Secrets](https://external-secrets.io/):** Open-source external secret management systems.  
- **[Gateway API](https://gateway-api.sigs.k8s.io/):** The next-gen Kubernetes Ingress for advanced traffic routing.  
- **[Technitium](https://github.com/TechnitiumSoftware/DnsServer):** DNS Server & ad-blocker.  
- **[Netbird](https://netbird.io/):** Secure, self-hosted VPN alternative with a mesh networking approach.  

---

## 🗃️ Folder Structure

```shell
homeops
├── 📂 argocd-apps
│   ├── databases
│   ├── logging
│   ├── network
│   ├── observability
│   ├── security
│   ├── tools
│   └── web
├── 📂 bootstrap
│   ├── argocd
│   ├── cilium
│   ├── crds
│   ├── csr-approver
│   └── external-secrets
├── 📂 services
│   ├── database
│   ├── network
│   ├── observability
│   ├── security
│   ├── storage
│   ├── tools
│   └── web
└── 📂 talos
    ├── clusterconfig
    └── patches
```


## 🗄️ Hardware Overview

Below is a list of the hardware used in the HomeOps setup:

| Device               | Model             | CPU                         | RAM   | Storage                        | Role                |
|----------------------|------------------|-----------------------------|-------|--------------------------------|---------------------|
| Lenovo SFF M900 (x4) | Lenovo M900 SFF  | Intel Core i5 @ 3.2 GHz     | 32GB  | 512GB SATA SSD + 128GB NVMe   | Worker Nodes        |
| Raspberry Pi 4       | RPI 4            | ARM Cortex-A72 @ 1.5 GHz    | 8GB   | 32GB MicroSD                  | Master Node         |
| Raspberry Pi 3       | RPI 3            | ARM Cortex-A53 @ 1.2 GHz    | 1GB   | 16GB                            | Dedicated DNS Server |
| Desktop             | Custom Build      | Intel Core i7-6700 @ 3.4 GHz | 16GB  | 2TB SATA SSD                   | NAS (Some other Services) |


## Bootstrapping Your HomeOps Environment

For detailed steps on bootstrapping your environment, check out the [Bootstrap Guide](bootstrap/README.md).

## ✅ TODO List

- [ ] 🔧 **Configure Renovate for Automated Dependency Updates**  

- [ ] 🚀 **Improve networking policies with Cilium.**  

- [ ] 📜 **Document services configuration & deployment.**  

