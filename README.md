# Odigos Helm Chart

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0) [![Release Charts](https://github.com/keyval-dev/odigos-charts/actions/workflows/release.yml/badge.svg?branch=master)](https://github.com/keyval-dev/odigos-charts/actions/workflows/release.yml)

This repository contains the helm chart for Odigos - the observability control plane.

## Usage

Add helm repository:
```console
helm repo add odigos https://keyval-dev.github.io/odigos-charts/
```

Install chart:
```console
helm repo update
helm upgrade --install odigos odigos/odigos --namespace odigos-system --create-namespace
```

Create community configuration:
```console
#!/usr/bin/env bash

cat <<EOF | kubectl create --namespace odigos-system -f -
apiVersion: odigos.io/v1alpha1
kind: OdigosConfiguration
metadata:
  name: odigos-config
spec:
  autoscalerImage: keyval/odigos-autoscaler
  configVersion: 1
  defaultSDKs:
    dotnet:
      sdkTier: community
      sdkType: native
    go:
      sdkTier: community
      sdkType: ebpf
    java:
      sdkTier: community
      sdkType: native
    javascript:
      sdkTier: community
      sdkType: native
    python:
      sdkTier: community
      sdkType: native
  ignoredNamespaces:
    - odigos-system
    - kube-system
    - local-path-storage
    - istio-system
    - linkerd
  instrumentorImage: keyval/odigos-instrumentor
  odigosVersion: v1.0.22
  supportedSDKs:
    dotnet:
      - sdkTier: community
        sdkType: native
    go:
      - sdkTier: community
        sdkType: ebpf
    java:
      - sdkTier: community
        sdkType: native
    javascript:
      - sdkTier: community
        sdkType: native
    python:
      - sdkTier: community
        sdkType: native
  telemetryEnabled: true
EOF
```

## License

[Apache 2.0 License](https://github.com/prometheus-community/helm-charts/blob/main/LICENSE).
