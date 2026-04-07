# envoy-gateway-controller

This is a Helm component for deploying **gateway-helm**.

## Description

Envoy Gateway controller and data plane

## Structure

```
envoy-gateway-controller/
├── Chart.yaml (Base chart definition)
├── values.yaml (Base values)
└── {cluster}/
    ├── Chart.yaml
    ├── values.yaml (Cluster-specific values)
    ├── README.md (Cluster-specific usage instructions)
    └── envoy-gateway-controller-appset.yaml
```

## Running with Helm

For cluster-specific deployment instructions, see the README.md file inside each cluster folder.

### Install using base values only
```bash
helm install envoy-gateway-controller . -f values.yaml
```

### Install with cluster-specific values
```bash
# Replace {cluster} with the cluster name (e.g., prod, staging)
# See {cluster}/README.md for detailed instructions
helm install envoy-gateway-controller . -f values.yaml -f {cluster}/values.yaml
```

### Uninstall
```bash
helm uninstall envoy-gateway-controller
```
