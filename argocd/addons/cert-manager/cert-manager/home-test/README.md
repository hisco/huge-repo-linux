# cert-manager - home-test cluster

This folder contains cluster-specific configuration for deploying **cert-manager** to the **home-test** cluster.

## Files

- `Chart.yaml` - Chart metadata (wrapper chart version: 1.0.0)
- `values.yaml` - Cluster-specific values that override base values
- `cert-manager-appset.yaml` - ArgoCD ApplicationSet for deployment

## Running with Helm

The following commands should be run from the **parent directory** (one level up).

### Install
Install the chart with both base values and home-test-specific overrides:

```bash
helm install cert-manager . \
  -f ../values.yaml \
  -f home-test/values.yaml
```

### Upgrade
Upgrade an existing release:

```bash
helm upgrade cert-manager . \
  -f ../values.yaml \
  -f home-test/values.yaml
```

### Template/Dry-run
Preview the manifests that would be installed:

```bash
helm template cert-manager . \
  -f ../values.yaml \
  -f home-test/values.yaml
```

### Diff (with helm-diff plugin)
See what would change in an upgrade:

```bash
helm diff upgrade cert-manager . \
  -f ../values.yaml \
  -f home-test/values.yaml
```

### Uninstall
```bash
helm uninstall cert-manager
```

## Values Hierarchy

Values are applied in the following order (later values override earlier ones):
1. Base values from `../values.yaml`
2. Cluster-specific values from `values.yaml`

This allows you to define common configuration in the base values and override specific settings per cluster.
