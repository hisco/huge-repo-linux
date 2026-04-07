# envoy-gateway-controller - home-test cluster

This folder contains cluster-specific configuration for deploying **gateway-helm** to the **home-test** cluster.

## Files

- `Chart.yaml` - Chart metadata (wrapper chart version: 1.0.0)
- `values.yaml` - Cluster-specific values that override base values
- `envoy-gateway-controller-appset.yaml` - ArgoCD ApplicationSet for deployment

## Running with Helm

The following commands should be run from the **parent directory** (one level up).

### Install
Install the chart with both base values and home-test-specific overrides:

```bash
helm install envoy-gateway-controller . \
  -f ../values.yaml \
  -f home-test/values.yaml
```

### Upgrade
Upgrade an existing release:

```bash
helm upgrade envoy-gateway-controller . \
  -f ../values.yaml \
  -f home-test/values.yaml
```

### Template/Dry-run
Preview the manifests that would be installed:

```bash
helm template envoy-gateway-controller . \
  -f ../values.yaml \
  -f home-test/values.yaml
```

### Diff (with helm-diff plugin)
See what would change in an upgrade:

```bash
helm diff upgrade envoy-gateway-controller . \
  -f ../values.yaml \
  -f home-test/values.yaml
```

### Uninstall
```bash
helm uninstall envoy-gateway-controller
```

## Values Hierarchy

Values are applied in the following order (later values override earlier ones):
1. Base values from `../values.yaml`
2. Cluster-specific values from `values.yaml`

This allows you to define common configuration in the base values and override specific settings per cluster.
