# envoy-gateway-class

This is a Kustomize component with the following structure:

```
envoy-gateway-class/
├── README.md (This file)
├── base/
│   ├── kustomization.yaml
│   └── *.yaml (Kubernetes manifests)
└── overlays/
    ├── [cluster]/
    │   ├── kustomization.yaml
    │   ├── README.md (Cluster-specific usage instructions)
    │   ├── *.yaml (Cluster-specific patches)
    │   └── envoy-gateway-class-appset.yaml
```

## Running with Kustomize

### Build manifests for base
```bash
kustomize build base/
```

### Build manifests for a specific cluster overlay
```bash
# Replace [cluster] with the cluster name (e.g., prod, staging)
kustomize build overlays/[cluster]/
```

## Usage with ArgoCD

Each cluster overlay includes an ApplicationSet for deployment:
- `overlays/[cluster]/envoy-gateway-class-appset.yaml`

### Apply to cluster

```bash
# Apply base
kubectl apply -k base/

# Apply specific overlay
kubectl apply -k overlays/[cluster]/
```

### Diff before applying
```bash
kubectl diff -k overlays/[cluster]/
```
