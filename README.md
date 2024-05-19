# Odigos Helm Chart

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0) [![Release Charts](https://github.com/odigos-io/odigos-charts/actions/workflows/release.yml/badge.svg?branch=main)](https://github.com/odigos-io/odigos-charts/actions/workflows/release.yml)

This repository contains the helm chart for Odigos - the observability control plane.

**Notice:** The Helm repository URL for Odigos has changed on May 6 2024. Please update your records to use the new URL: https://odigos-io.github.io/odigos-charts/:

```
helm repo add odigos https://odigos-io.github.io/odigos-charts/ --force-update
```


## Usage

Add helm repository:
```console
helm repo add odigos https://odigos-io.github.io/odigos-charts/
```

### Install Odigos

```console
helm repo update
helm upgrade --install odigos odigos/odigos --namespace odigos-system --create-namespace
kubectl label namespace odigos-system odigos.io/system-object="true"
```

### Upgrade Existing Odigos Installation

```console
helm repo update
helm upgrade odigos odigos/odigos --namespace odigos-system
```

### Uninstall Odigos

```console
helm delete odigos -n odigos-system
kubectl delete ns odigos-system
```

## License

[Apache 2.0 License](https://github.com/prometheus-community/helm-charts/blob/main/LICENSE).
