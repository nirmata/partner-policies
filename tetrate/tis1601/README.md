# Validate VirtualService Destination Namespace
## Overview
The `validate-virtualservice-namespace` policy is a Kyverno ClusterPolicy designed to ensure that all Istio VirtualService resources reference valid destination namespaces. The policy validates that any namespace specified in the destination host (in the format `service.namespace.svc.cluster.local`) exists in the cluster.

This policy helps prevent misconfigurations and potential routing issues by ensuring that VirtualServices only reference existing namespaces.

## Usage
To apply this policy, ensure you have Kyverno installed in your Kubernetes cluster and apply the YAML configuration using:
```bash
kubectl apply -f validate-virtualservice-namespace.yaml
```

## Web Reference
For more details, see:
TIS1601 - VirtualService References Non-Existent Namespace
This guidance from Tetrate outlines the importance of validating namespace references in VirtualService configurations.
[View Details](https://docs.tetrate.io/istio-subscription/tools/tca/analysis/TIS1601)

## Conclusion
Validating namespace references in VirtualService configurations is crucial for maintaining a reliable service mesh. This Kyverno policy ensures that all VirtualServices reference existing namespaces, preventing potential routing issues and misconfigurations.
