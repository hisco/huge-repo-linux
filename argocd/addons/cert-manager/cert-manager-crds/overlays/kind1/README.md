# cert-manager-crds - kind1 cluster

This folder contains cluster-specific Kustomize patches for deploying **cert-manager-crds** to the **kind1** cluster.

## Files

- `kustomization.yaml` - Kustomize configuration with base reference and patches
- `*.yaml` - Cluster-specific patches that override base manifests
- `cert-manager-crds-appset.yaml` - ArgoCD ApplicationSet for deployment

## Running with Kustomize

### Build manifests
Build the final manifests with cluster-specific patches applied:

```bash
kustomize build overlays/kind1/
```

### Apply to cluster
Apply the manifests directly to the cluster:

```bash
kubectl apply -k overlays/kind1/
```

### Diff before applying
Preview what changes would be applied:

```bash
kubectl diff -k overlays/kind1/
```

## How Kustomize Overlays Work

This overlay uses Kustomize's patching mechanism:

1. **Base manifests** are defined in `../../base/`
2. **Cluster-specific patches** in this directory override base values
3. Kustomize merges them together when you build or apply

### Patch Files

Each `*.yaml` file in this directory is a patch that targets a specific resource by:
- `kind` - The Kubernetes resource type (e.g., Deployment, Service)
- `metadata.name` - The resource name

Only the fields you specify in the patch are overridden; everything else comes from the base.

### Example Patch Structure

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: cert-manager-crds
spec:
  replicas: 3  # Override replicas from base
  template:
    spec:
      containers:
        - name: main
          resources:
            requests:
              memory: "512Mi"  # Override memory from base
```

This patch only changes `replicas` and `resources.requests.memory` - all other Deployment fields come from the base manifest.
