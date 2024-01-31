# Odigos Helm Chart

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0) [![Release Charts](https://github.com/keyval-dev/odigos-charts/actions/workflows/release.yml/badge.svg?branch=master)](https://github.com/keyval-dev/odigos-charts/actions/workflows/release.yml)

This repository contains the helm chart for Odigos - the observability control plane.

## Usage

Add helm repository:
```console
helm repo add odigos https://keyval-dev.github.io/odigos-charts/
```

Install helm release:
```console
helm repo update
helm upgrade --install odigos odigos/odigos --namespace odigos-system --create-namespace
kubectl label namespace odigos-system odigos.io/system-object="true"
```

Uninstall helm release:
```console
helm delete odigos -n odigos-system
kubectl delete ns odigos-system
```


## License

[Apache 2.0 License](https://github.com/prometheus-community/helm-charts/blob/main/LICENSE).
