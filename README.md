# Helm-Kustomize-Observability

Centralized management of observability components across multiple Kubernetes clusters and namespaces using Helm for package management and Kustomize for configuration customization. Supports dynamic environment-specific configurations for tools like Grafana and Prometheus, streamlining deployments and ensuring consistent monitoring setups.

## Overview

This repository contains Helm charts and Kustomize configurations for deploying and managing observability tools such as Grafana and Prometheus in a Kubernetes environment. It is designed to be flexible, supporting multiple environments (e.g., staging, production) and namespaces, making it ideal for organizations managing complex, multi-cluster deployments.

## Prerequisites

Before you begin, ensure you have the following installed:

- Kubernetes cluster
- Helm (version 3.x or later)
- Kustomize (version 4.x or later)
- kubectl (compatible with your cluster version)

## Installation

1. Clone the repository:

```bash
git clone https://github.com/sandy2008/helm-kustomize-observability.git
cd helm-kustomize-observability
```

2. Navigate to the `helm-charts` directory and package the Helm chart:

```bash
cd helm-charts/observability
helm package .
```

3. Apply the base Kustomize configuration to create the observability tools in your default namespace:

```bash
kustomize build ../kustomize/base | kubectl apply -f -
```

## Usage

### Deploying to Different Environments

To deploy to a specific environment and namespace, use Kustomize to apply the corresponding overlay. For example, to deploy to the production environment in namespace `ns1`:

```bash
kustomize build kustomize/overlays/prod/ns1 | kubectl apply -f -
```

### Customizing Configurations

Edit the values in the `values.yaml` file in the Helm chart or the overlay `kustomization.yaml` files to customize the deployment for your environment.

## License

[MIT](https://choosealicense.com/licenses/mit/)
