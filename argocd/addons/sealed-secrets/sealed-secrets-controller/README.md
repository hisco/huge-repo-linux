# sealed-secrets-controller

This is a Helm component for deploying **sealed-secrets**.

## Description

Sealed Secrets controller for decrypting SealedSecret resources

## Structure

```
sealed-secrets-controller/
├── Chart.yaml (Base chart definition)
├── values.yaml (Base values)
└── {cluster}/
    ├── Chart.yaml
    ├── values.yaml (Cluster-specific values)
    ├── README.md (Cluster-specific usage instructions)
    └── sealed-secrets-controller-appset.yaml
```

## Running with Helm

For cluster-specific deployment instructions, see the README.md file inside each cluster folder.

### Install using base values only
```bash
helm install sealed-secrets-controller . -f values.yaml
```

### Install with cluster-specific values
```bash
# Replace {cluster} with the cluster name (e.g., prod, staging)
# See {cluster}/README.md for detailed instructions
helm install sealed-secrets-controller . -f values.yaml -f {cluster}/values.yaml
```

### Uninstall
```bash
helm uninstall sealed-secrets-controller
```
