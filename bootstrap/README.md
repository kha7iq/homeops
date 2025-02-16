# Bootstrapping Your Cluster

This will walk you through initializing your cluster using the provided `Taskfile.yaml` and the `bootstrap` directory.

## Prerequisites

Before diving in, ensure you have the following installed:

- **Kustomize**: For building Kubernetes manifests.
- **kubectl**: To interact with your Kubernetes cluster.
- **Task**: A task runner for executing tasks defined in `Taskfile.yaml`.

## Step 1: Clone the Repository

Begin by cloning the HomeOps repository to your local machine:

```bash
git clone https://github.com/kha7iq/homeops.git
cd homeops
```

## Step 2: Understand the Taskfile

The `Taskfile.yaml` defines tasks to bootstrap your environment. Here's a breakdown:

- **crds**: Installs Custom Resource Definitions (CRDs) from `bootstrap/crds`.
- **cilium**: Deploys Cilium for networking and waits for it to be ready.
- **csr-approver**: Sets up the Certificate Signing Request (CSR) approver.
- **external-secrets**: Deploys External Secrets; executes its own Taskfile.
- **argocd**: Installs Argo CD and ensures it's up and running.
- **bootstrap**: Runs all the above tasks in sequence with necessary delays and checks.

## Step 3: Execute the Bootstrap Task

To initialize your environment, run the `bootstrap` task:

```bash
task bootstrap
```

This command will:

1. **Install CRDs**: Apply configurations from `bootstrap/crds`.
2. **Deploy Cilium**: Set up networking and wait for readiness.
3. **Set Up CSR Approver**: Deploy the CSR approver component.
4. **Deploy External Secrets**: Navigate to `bootstrap/external-secrets` and execute its Taskfile.
5. **Install Argo CD**: Deploy Argo CD and ensure it's operational.

Each step includes necessary delays and checks to confirm successful deployment.

## Step 4: Verify Deployments

After the bootstrap process completes, verify that all components are running smoothly:

```bash
kubectl get pods -A
```

Ensure pods in the following namespaces are in a `Running` or `Completed` state:

- `kube-system` (Cilium components)
- `external-secrets`
- `argocd`

## Additional Information

- **Customization**: Modify configurations in the `bootstrap` directory as needed before running the bootstrap task.
- **Task Details**: Refer to the `Taskfile.yaml` for specifics on each task and their execution order.

By following these steps, your HomeOps environment should be up and running, ready for further configuration and deployment.
